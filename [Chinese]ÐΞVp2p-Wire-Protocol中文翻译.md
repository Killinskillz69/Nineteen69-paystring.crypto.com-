<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

:stop_sign: This wiki has now been deprecated. Please visit [ethereum.org](https://ethereum.org/zh) for up-to-date information on Ethereum. :stop_sign: 

Specific information about the wire protocol can be found at [ethereum.org/zh](https://ethereum.org/zh/developers/docs/networking-layer/)


**Contents**

- [ÐΞVP2P 通讯协议](#%C3%B0%CE%BEvp2p-%E9%80%9A%E8%AE%AF%E5%8D%8F%E8%AE%AE)
  - [2.负载内容](#2%E8%B4%9F%E8%BD%BD%E5%86%85%E5%AE%B9)
  - [3.P2P通信](#3p2p%E9%80%9A%E4%BF%A1)
    - [3.1 hello](#31-hello)
    - [3.2 Disconnect](#32-disconnect)
    - [3.3 ping](#33-ping)
    - [3.4 pong](#34-pong)
    - [3.5 未实现](#35-%E6%9C%AA%E5%AE%9E%E7%8E%B0)
  - [4.节点标识(node id) 和 可信度](#4%E8%8A%82%E7%82%B9%E6%A0%87%E8%AF%86node-id-%E5%92%8C-%E5%8F%AF%E4%BF%A1%E5%BA%A6)
  - [5.会话管理](#5%E4%BC%9A%E8%AF%9D%E7%AE%A1%E7%90%86)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->


# ÐΞVP2P 通讯协议


> 此协议用于eth/whisper/&c 等节点之间的相互通讯。由于本协议使用现有的ÐΞV技术和rlp标准,因此本通讯协议很简单
## 1.底层通讯协议
ÐΞVp2p节点通过使用RLPx（加密和认证的传输协议）发送消息进行通信。每个节点可以自定义一个端口进行广播和接受连接。默认端口为30303.虽然TCP提供面向连接的介质，但是ΞΞVp2p节点之间是以数据包为周期的形式进行通信。 
RLPx也提供发送和接收数据包的工具。
有关RLPx的更多信息，请参阅协议规范。

ÐΞVp2p节点通过RLPx的发现协议DHT(分散式哈希表)找到对端,也可以通过对端的特定的rpc接口来直接连接。
## 2.负载内容
RLP可以对很多种不同“类型”的负载数据进行编码。这个“类型”通过RLP消息的消息入口部分进行定义。消息入口部分的类型是整型。

ÐΞVp2p旨在通过基本协议支持任意子协议（也称为功能）。每个功能都按需提供尽可能多的消息ID空间（所有这些功能必须静态地指定它们需要多少消息ID）。在连接和接收到Hello消息时，两个对端都能获取到另外一端所使用的所有共享的功能(包括版本号)，并且能够对消息ID空间的组成形成共识。

0x00～0x10的闭区间内是ÐΞVp2p的预留消息id。其余的消息id从0x10开始以此递增，并且每一个共享的功能按照字母顺序排列。未共享的功能会被忽略。同一个共享功能取版本号最高的。

## 3.P2P通信
总共有4种基本的消息类型。
### 3.1 hello
> 发起连接的消息类型

双方的第一个通讯消息。该消息双方都有且只有一次发送,在收到该消息之前，其他消息都不能发送。
消息结构如下:

```
0x00 [
        p2pVersion: P, 
        clientId: B, 
        [
          [cap1: B_3, capVersion1: P],
          [cap2: B_3, capVersion2: P],
           ...
        ],
        listenPort: P, 
        nodeId: B_64
      ]

```

- `p2pVersion` :P为整型。目前必须是 **1**。 指定当前基础通讯协议版本号。
- `clientId`   :B为字符串。目前是    **Ethereum(++)/1.0.0**。 制定软件标示。必须是具有可读性的字符串。
- `cap1`,`capVersion1` :B_3为3位字符串,P为整型。 指定本节点有的功能名和版本号。功能名是长度为 **3**  的字符串,版本号是整数。目前支持 **eth, 版本号为34**， 和 **shh, 版本号是1** 。
- `listenPort`: P为整型。当前节点监听的端口。为 **0**的话表示不监听。
- `nodeId` :B_64字符串。 512位的hash值(8*64),是该节点的唯一标识符。

### 3.2 Disconnect
> 断开链接的消息类型 

通知对方断开链接。如果对方收到应该立即断开链接。在发送该消息之后，表现良好的主机应该等2秒。
消息结构如下

```
0x01 [reason: P]
```

- `reason` : P为整型。表示节点断开的原因。
  - `0x00` : 请求断开。
  - `0x01` : TCP子系统错误。
  - `0x02` : 协议被破坏。举例：消息异常，错误的RLP编码，不正确的magic number.
  - `0x03` : 无效的对端。
  - `0x04` : 过多的对端连接。
  - `0x05` : 已连接，本次连接为重复连接。
  - `0x06` : P2P协议不一致。
  - `0x07` : 未接收道对端的nodeId.这个错误是自动生成的。
  - `0x08` : 客户端退出。
  - `0x09` : 无效node id。举例:和之前连接的node id不同。和可信任的节点告诉我们的node id相比不同。
  - `0x0a` : node id和本节点相同。举例:自己连接自己。
  - `0x0b` : 接受消息超时。举例:自从上一次ping消息之后在没有收到任何消息。
  - `0x10` :未知错误。

### 3.3 ping
> 保持通讯活性

请求对端立即回复pong消息。
消息结构如下：

```
0x02 []
```

### 3.4 pong
> 保持通讯活性

回复ping消息。
消息结构如下：

```
0x03 []
```

### 3.5 未实现

- GetPeers :0x04
- Peers    :0x05

## 4.节点标识(node id) 和 可信度
使用ÐΞVp2p协议的节点，其node id 是一个经过**secp256k1**加密后的公钥。


每个节点都可以自由的给其自身所储存的node id根据该nodeid过去的有效程度进行等级划分，并且根据等级给出相应的优先权。节点还可以跟踪节点ID（及其出处），以帮助确定潜在的中间人攻击。客户端可以自由标记新节点并使用节点ID作为确定节点信誉的方法。

## 5.会话管理
在刚开始建立连接时，所有客户端（比如双方对端节点）都必须发送 `hello`消息。当收到`hello`消息并且对双方的网络类型和版本达成共识之后，活跃会话便建立了。从此双发可以发送其他的P2P消息了。

断开连接的消息(disconnect)可以随时发送。
