<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Welcome to the Ethereum Wiki](#welcome-to-the-ethereum-wiki)
- [Contribution guidelines](#contribution-guidelines)
  - [License and contributor license agreement](#license-and-contributor-license-agreement)
- [Getting started](#getting-started)
- [Downloads](#downloads)
  - [Status / Releases / Development timeline / Roadmap](#status--releases--development-timeline--roadmap)
- [Don't get lost](#dont-get-lost)
- [A proposal to move the content in this wiki to a Wikipedia-style wiki site](#a-proposal-to-move-the-content-in-this-wiki-to-a-wikipedia-style-wiki-site)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Welcome to the Ethereum Wiki

[![Documentation chat](https://img.shields.io/badge/gitter-Docs%20chat-4AB495.svg)](https://gitter.im/ethereum/documentation)

This is the community maintained wiki covering all sorts of information on the next-generation peer-to-peer technology platform built by the Ethereum Foundation, including **Ethereum**, _the generalized blockchain for smart contract development_, as well as sister protocols like **[Whisper](https://github.com/ethereum/wiki/wiki/Whisper-pages)**, _the private low-level datagram communication platform_, and **[Swarm](http://swarm-gateways.net/bzz:/theswarm.eth/)**, a distributed storage platform and content distribution service.

<!-- START doctoc -->
<!-- END doctoc -->

# Contribution guidelines

Users signed in with GitHub can edit and add pages using a [browser](https://help.github.com/articles/editing-wiki-pages-via-the-online-interface) or [locally](https://help.github.com/articles/adding-and-editing-wiki-pages-locally). 

**Do not change the title of a page**, as the link for it will change. In particular, if you change the title for a page, any link to it will just direct to a blank page. (In the case of this page, also the Wiki tab in the header of this repo, as well as any link to the Home page, will just direct to a list of pages.) If you really want to change the title, then create a new page with the new title, move the contents of the old page to the new page, and update the old page with a redirect link to the new page. If you want to translate a page, create a new page and translate the original there. Consider previewing your changes before saving them, and if you detect any errors, fix them. If you happen to get directed to a page that doesn't exist with a prompt to create a new page, do that, without changing the title. Then check the history of the newly created page. It may be that there is a history of changes to the page that you just created, with the second most recent change (second to you creating the page) being that someone renamed the page. If so, please fix the page (restore it to the revision before the title was changed or redirect to the new page) and tag the person who renamed the page in this issue [here](https://github.com/ethereum/wiki/issues/591) or on [Gitter](https://gitter.im/ethereum/documentation).

Wikipedia has [five pillars](https://en.wikipedia.org/wiki/Wikipedia:Five_pillars) which provide a good standard for contributing that we can adapt for our needs, however certain aspects such as notability need not be adhered to.

## License and [contributor license agreement](https://github.com/ethereum/wiki/wiki/CC0-license#list-of-contributors)

Please permit your contributions to be under the CC0 license,  which makes your contributions have no rights reserved, putting them in the public domain. This will help to allow for the dissemination of information about Ethereum, the Ethereum ecosystem and Web 3 to the public, in a completely permissive manner. To state that you accept your contributions to be under a CC0 license, please add yourself to the list of external contributors [here](https://github.com/ethereum/wiki/wiki/CC0-license#list-of-contributors). Otherwise, without adding yourself to the list, your contributions will be all rights reserved. Some previous contributions may have all rights reserved (by contributors that have not agreed to a CC0 license [at pull request 528](https://github.com/ethereum/wiki/pull/528)), since no copyright permission was stated explicitly. Until all previous contributors agree to a CC0 license, and to provide clarity of licensing, you may also wish to add a HTML comment to the top of pages or sections that you contribute to, like so: `<!--*Name Surname*, Github username, **email@domain** and/or other contact methods-->`. 

# Getting started

To get the basic concepts of Ethereum visit [http://ethereum.org](http://ethereum.org/). For another introduction targeted for end users but also for developers and others, see [here](https://github.com/ethereum/wiki/wiki/Ethereum-introduction). If you want to get a deeper understanding, start by reading the [whitepaper](https://github.com/ethereum/wiki/wiki/White-Paper) and the [design rationale](https://github.com/ethereum/wiki/wiki/Design-Rationale). For a more formal review, read the [yellow paper](https://ethereum.github.io/yellowpaper/paper.pdf). If you are interested in being a core developer, find a project that interests you, and start contributing to that (maybe pro-bono initially, until maintainers like you and decide to hire you). For Ethereum research and protocol architecture, visit [https://ethresear.ch](https://ethresear.ch/) as well as https://github.com/ethereum/wiki/wiki/R&D. If you are interested in developing smart contracts you can see [here](https://en.wikipedia.org/wiki/Ethereum#Programming_languages), as well as under [ÐApp Development](https://github.com/ethereum/wiki/wiki/%C3%90App-Development) (which is also in the sidebar).

For getting started guides, see here

* [Step-by-Step Guide: Getting Started with Ethereum Mist Wallet](https://medium.com/@attores/step-by-step-guide-getting-started-with-ethereum-mist-wallet-772a3cc99af4)
* [Create a Hello World Contract in ethereum](https://www.ethereum.org/greeter)
* [How to create a private Ethereum network Comments Feed](https://omarmetwally.wordpress.com/2017/07/25/how-to-create-a-private-ethereum-network/)

# Downloads

See [here](https://github.com/ethereum/wiki/wiki/Clients).

## Status / Releases / Development timeline / Roadmap

See [here](https://github.com/ethereum/wiki/wiki/Releases).

# Don't get lost

If you have any question, check the [FAQS](https://github.com/ethereum/wiki/wiki/FAQS) and [Glossary](https://github.com/ethereum/wiki/wiki/Glossary).

There are separate wikis for some implementations, as follows:

* [go-ethereum](https://github.com/ethereum/go-ethereum/wiki)
* [Parity](https://paritytech.github.io/wiki/)
* [cpp-ethereum](http://www.ethdocs.org/en/latest/ethereum-clients/cpp-ethereum/index.htm)
* [pyethereum](https://github.com/ethereum/pyethereum/wiki)

# A proposal to move the content in this wiki to a Wikipedia-style wiki site

Github wikis have the limitation that anyone can edit them while it is difficult to moderate them (it is not possible to watch a page to get updates for changes), which is a double-edged sword, in that it is great for non-censorship which is in the spirit of the [Ethereum philosophy](https://github.com/ethereum/wiki/wiki/White-Paper#philosophy), however it is also prone to graffiti, bias, etc. Because of this limitation of lack of ease for moderation, we should consider moving the content in this wiki to a wiki site, e.g. one that is hosted by [Media Wiki](https://www.mediawiki.org/wiki/MediaWiki), adding a deprecation notice to this wiki and refer to the proposed new Media Wiki hosted site. This would have the benefits of anyone still being able to edit the wiki (they do not even need to create an account, although there are advantages to doing so), as well as being able to more easily moderate content. In order to move the contents of this wiki to another site, we would need a site that is compatible with Github Flavoured Markdown, to prevent manually changing the syntax to support the new site (or using a conversion tool); and it would need to have moderation features like Media Wiki sites, such as the ability to watch a page and get email notifications of any changes. There is a list of other [Ethereum wikis and documentation](https://github.com/ethereum/wiki/wiki/List-of-other-Ethereum-wikis-and-documentation).