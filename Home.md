# Welcome to the Ethereum Wiki!

[![Documentation chat](https://img.shields.io/badge/gitter-Docs%20chat-4AB495.svg)](https://gitter.im/ethereum/documentation)
[![standard-readme compliant](https://img.shields.io/badge/readme%20style-standard-brightgreen.svg?style=flat-square)](https://github.com/RichardLitt/standard-readme)

> Ethereum wiki covering all things related to Ethereum

This is the community maintained wiki covering all sorts of  information on the next-generation peer-to-peer technology platform built by the Ethereum Foundation, including **Ethereum**, _the generalized blockchain for smart contract development_, as well as sister protocols like **[Whisper](https://github.com/ethereum/wiki/wiki/Whisper-pages)**, _the private low-level datagram communication platform_, and **[Swarm](http://swarm-gateways.net/bzz:/theswarm.eth/)**, a distributed storage platform and content distribution service. See [here](https://github.com/ethereum/wiki/wiki/Ethereum-introduction) for an introduction, and other pages in the sidebar.

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Contents**

- [See also](#see-also)
- [Issues and pull requests](#issues-and-pull-requests)
- [Contribution guidelines](#contribution-guidelines)
  - [Introduction](#introduction)
  - [Fixing vandalism](#fixing-vandalism)
    - [Page titles](#page-titles)
  - [Wikipedia pillars](#wikipedia-pillars)
  - [Translating](#translating)
  - [License and contributor license agreement](#license-and-contributor-license-agreement)
  - [Editing locally (requires access permission)](#editing-locally-requires-access-permission)
    - [Setup](#setup)
    - [Usage](#usage)
- [Getting started](#getting-started)
- [Downloads](#downloads)
- [Status / Releases / Development timeline / Roadmap](#status--releases--development-timeline--roadmap)
- [Don't get lost](#dont-get-lost)
- [A proposal to move the content in this wiki to a Wikipedia-style wiki site](#a-proposal-to-move-the-content-in-this-wiki-to-a-wikipedia-style-wiki-site)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## See also
* https://github.com/ethresearch/en-ethereum-wiki, an alternative version to this wiki. (More details on that are in [this issue](https://github.com/ethereum/wiki/issues/589)).
* https://docs.ethhub.io/, which at a quick glance, looks like a decent site worth looking into for newbies and pros to get news and info about the Ethereum sector.

## Issues and pull requests

If you have a technical issue with a specific client, application or tool, e.g. those listed [here](https://github.com/ethereum/wiki/wiki/Clients,-tools,-dapp-browsers,-wallets-and-other-projects), please ask in the Gitter room of that project, and if your issue is still not resolved, post an issue in the repo for that project. Please only create an issue if you can't fix it by editing yourself, it doesn't get resolved via the [Gitter documentation room](https://gitter.im/ethereum/documentation) (including pinging someone who knows how to handle the issue, or asking/finding out who knows then pinging them) and only if it is related to the wiki. 

If you had an issue that has been closed, and feel that it could be reopened after following the above steps, feel free to request to reopen it. Do not make a pull request; chances are that all PRs will be ignored, since any content in the codebase can be in this wiki instead. About 180 issues and 30 PRs were closed on May 29 2018, due to deleting the codebase and referring people to this wiki, in order to reduce the burden on maintenance by following the above steps. This fits well with Ethereum's ethos of decentralization, which includes minimising bureaucracies, and gives contributors more time to build Ethereum and satisfy the long-term interests of current and future users. If you had an issue or PR that was closed without explanation, I apologize, but it is time-consuming to reply to every one; I'm hoping that people will see the updated readme and this section.

While having good documentation is certainly important to help onboard new people including users and contributors of all kinds, there is a lot to do at the moment in terms of design and implementation, and editing documentation is something that seems best to be done when you are reading or learning about something, using something, building upon something, etc., not usually just for the sake of reading and editing for other users, although reviewing one's own writing is certainly a good practice.

## Contribution guidelines

### Introduction

For an introduction to GitHub wikis, see [here](https://help.github.com/articles/about-github-wikis/).

### Fixing vandalism

If you notice that a page is vandalized, such as the footer (which has been frequently vandalized), this home page, or the sidebar, please view the page history (which is the link of a page with a `/_history` appended), and revert to the last known good version (which are listed below for convenience for the above pages), by ticking it and the most recent revision, selecting "Compare revisions", and then "Revert changes":
- [gist backup](https://gist.github.com/jamesray1/810006765d7d57c11cfbfdf38500b051) of this [link to a last known working version as of Feb 16 2019](https://github.com/ethereum/wiki/wiki/_Footer/0b92c2b7a95a674d5a23b1ccab6c8ad9bd4b7085) (you will only be able to view this if the footer is deleted, to restore you'd have to select the body text, right click, select view selection source and copy and paste the HTML, which I have done to the aforementioned gist backup)
- https://github.com/ethereum/wiki/wiki/_Sidebar/1e9533bd7ce85af4befd4dae2aee6b2d2cb84189
- https://github.com/ethereum/wiki/wiki/Home/70ef1d4734198572334f9f792beb14a249a70a77

#### Page titles

**Avoid changing the title of a page**, as the link for it will change. In particular, if you change the title for a page, any link to it will just direct to a blank page. (In the case of this page, also the Wiki tab in the header of this repo, as well as any link to the Home page, will just direct to a list of pages.) If you really want to change the title, then create a new page with the new title, move the contents of the old page to the new page, and update the old page with a redirect link to the new page. If you want to translate a page, create a new page and translate the original there. Consider previewing your changes before saving them, and if you detect any errors, fix them. If you happen to get directed to a page that doesn't exist with a prompt to create a new page, do that, without changing the title. Then check the history of the newly created page. It may be that there is a history of changes to the page that you just created, with the second most recent change (second to you creating the page) being that someone renamed the page. If so, please fix the page (restore it to the revision before the title was changed or redirect to the new page) and tag the person who renamed the page in this issue [here](https://github.com/ethereum/wiki/issues/591) or on [Gitter](https://gitter.im/ethereum/documentation).

### Wikipedia pillars

Wikipedia has [five pillars](https://en.wikipedia.org/wiki/Wikipedia:Five_pillars) which provide a good standard for contributing that we can adapt for our needs. If you have experience with editing on Wikipedia, then that will help with knowing how to edit this wiki, although the contribution rules are less strict. Referencing facts is a key writing and proofreading task, as well as checking that information is up-to-date (and updating it if otherwise), correcting grammar, typos, and spelling; and making the wiki comprehensive and easy to understand. Other rules, such as a neutral point of view and no original research are desirable, but may be hard to maintain. Notability is less relevant, this wiki is about all things Ethereum.

### Translating
The title of the page should start with [Language]: title, e.g. "[German] White Paper" or "[中文] 以太坊Wiki目录". Then add a Table of Contents (ToC) page linking for the language, linking to all pages of that language, and add a link to it in the [footer](https://github.com/ethereum/wiki/wiki/_Footer/_edit). 

### License and [contributor license agreement](https://github.com/ethereum/wiki/wiki/CC0-license#list-of-contributors)

Please permit your contributions to be under the [CC0 license](https://creativecommons.org/publicdomain/zero/1.0/legalcode) [[1](https://creativecommons.org/share-your-work/public-domain/cc0/)],  which makes your contributions have no rights reserved, putting them in the public domain. This will help to allow for the dissemination of information about Ethereum, the Ethereum ecosystem and Web 3 to the public, in a completely permissive manner. To state that you accept your contributions to be under a CC0 license, please add yourself to the list of external contributors [here](https://github.com/ethereum/wiki/wiki/CC0-license#list-of-contributors). Otherwise, without adding yourself to the list, your contributions will be all rights reserved. Some previous contributions may have all rights reserved (by contributors that have not agreed to a CC0 license [at pull request 528](https://github.com/ethereum/wiki/pull/528)), since no copyright permission was stated explicitly. Until all previous contributors agree to a CC0 license, and to provide clarity of licensing, you may also wish to add a HTML comment to the top of pages or sections that you contribute to, like so: `<!--*Name Surname*, Github username, **email@domain** and/or other contact methods-->`.

### Editing locally (requires access permission)

Users signed in with GitHub can edit and add pages using a [browser](https://help.github.com/articles/editing-wiki-pages-via-the-online-interface) or [locally](https://help.github.com/articles/adding-and-editing-wiki-pages-locally). To view the wiki locally, ~~scroll to the bottom of the sidebar, and get the link to clone the wiki, (posting here for convenience: https://github.com/ethereum/wiki.wiki.git), then~~ open a terminal (CTRL+ALT+T is a typical keyboard shortcut), run `git clone https://github.com/ethereum/wiki.wiki.git` and then view the files from a file explorer or using `cd wiki.wiki; ls; // Enter a command to open a file from a terminal, e.g. gedit Home.md`. 

If you change the headers of the page then it's a good idea to update the contents to reflect that change, using doctoc, but you will need to have access permissions to push changes to this repo; you could ask in https://gitter.im/ethereum/documentation, and if there's no response from anyone in the EF after a couple of days, you could ping @Souptacular.

#### Setup

Use a package manager to install NPM or go to https://www.npmjs.com/get-npm. Then run:
```bash
npm install -g doctoc
```
#### Usage

```bash
# Open wiki folder in a terminal or cd to it.
git pull; # run this if you haven't just cloned or there are any upstream changes, or copy anyway just in case
doctoc --title "**Contents**" .; # it may take a while
git add .;
git commit -m "Update contents by running doctoc --title **Contents**";
git push;
```

## Getting started

To get the basic concepts of Ethereum visit [http://ethereum.org](http://ethereum.org/). For another introduction targeted for end users but also for developers and others, see [here](https://github.com/ethereum/wiki/wiki/Ethereum-introduction). If you want to get a deeper understanding, start by reading the [whitepaper](https://github.com/ethereum/wiki/wiki/White-Paper) and the [design rationale](https://github.com/ethereum/wiki/wiki/Design-Rationale). For a more formal review, read the [yellow paper](https://ethereum.github.io/yellowpaper/paper.pdf) or the [Jello Paper](https://jellopaper.org/). If you are interested in being a core developer, find a project such as [these ones](https://github.com/ethereum/wiki/wiki/Clients,-tools,-dapp-browsers,-wallets-and-other-projects) that interests you, and start contributing to that (maybe pro-bono initially, until maintainers like you and decide to hire you). If you start your own project, tell the world about it e.g. on [Twitter](https://twitter.com), [Peepeth](https://peepeth.com/), [Status](https://status.im/), and [Akasha](https://beta.akasha.world) and see https://gitcoin.co/grants/quickstart and https://blog.ethereum.org/2018/10/15/ethereum-foundation-grants-update-wave-4/. For Ethereum research and protocol architecture, visit [https://ethresear.ch](https://ethresear.ch/) as well as https://github.com/ethereum/wiki/wiki/R&D. If you are interested in developing smart contracts you can see [here](https://en.wikipedia.org/wiki/Ethereum#Programming_languages), as well as under [ÐApp Development](https://github.com/ethereum/wiki/wiki/%C3%90App-Development) (which is also in the sidebar).

For getting started guides, see here

* [Step-by-Step Guide: Getting Started with Ethereum Mist Wallet](https://medium.com/@attores/step-by-step-guide-getting-started-with-ethereum-mist-wallet-772a3cc99af4)
* [Create a Hello World Contract in ethereum](https://www.ethereum.org/greeter)
* [How to create a private Ethereum network Comments Feed](https://omarmetwally.wordpress.com/2017/07/25/how-to-create-a-private-ethereum-network/)

## Downloads

See [here](https://github.com/ethereum/wiki/wiki/Clients).

## Status / Releases / Development timeline / Roadmap

See [here](https://github.com/ethereum/wiki/wiki/Releases).

## Don't get lost

If you have any question, check the [FAQS](https://github.com/ethereum/wiki/wiki/FAQS) and [Glossary](https://github.com/ethereum/wiki/wiki/Glossary).

There are separate wikis for some implementations, as follows:

* [go-ethereum](https://github.com/ethereum/go-ethereum/wiki)
* [Parity](https://paritytech.github.io/wiki/)
* [cpp-ethereum](http://www.ethdocs.org/en/latest/ethereum-clients/cpp-ethereum/index.html)
* [pyethereum](https://github.com/ethereum/pyethereum/wiki)

## A proposal to move the content in this wiki to a Wikipedia-style wiki site

See [this issue](https://github.com/ethereum/wiki/issues/589).

