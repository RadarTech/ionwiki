---
latest-revision: '2019-01-27T00:00:00.000Z'
original-author: Ryan Shea (ryan-shea)
created: '2019-01-01T00:00:00.000Z'
status: Accepted
title: Wallet
contributors: Ryan Shea (ryan-shea); Gareth James (gjradar)
type: article
description: ''
discussions-to: GitHub URL
category: lightning-software
---

# Lightning Wallets

## Overview

A **wallet** is an app or program that enables you to send and recieve Bitcoin. A Lightning-enabled wallet allows you to interact with the Lightning Network. Wallets keep track of your BTC balance - which is usually held in one or more bitcoin addresses - and your transaction history.

The wallet controls access to a user's money, manages keys and addresses, tracks balance, and creates and signs transactions.

## Details

### Wallet Function

A wallet is the most common user interface to the Bitcoin and Lightning system, just like a web browser is the most common interface for the HTTP protocol.

Wallets manage public and private keys, track balances, and create and sign transactions.

Keys are often stored in a digital wallet on each user’s computer or smartphone. Possession of the key that can sign a transaction is the only prerequisite to spending bitcoin, putting the control entirely in the hands of each user.

### Lightning-enabled Wallets

On Lightning, wallets establish channels, calculate routes on the network, manage channel opening and closing, and in some cases, ensure constant uptimes.

### Wallet Types

Wallets are one of the most actively developed applications in the Bitcoin and Lightning ecosystem. There is intense competition, and wallet adoption serves as an essential element to user adoption. Choosing a wallet is highly subjective and depends on the use and user experience.

There are multiple types of wallet:

#### Browser Wallet

A browser wallet runs on a Internet Browser (e.g. Chrome, Firefox, Edge, etc.). They can run a Lightning node directly in the browser, allow to connect mobile, desktop or web wallets or can be custodial. [Alby](https://getalby.com/) is one example.

#### Desktop Wallet

A desktop wallet runs on Windows, macOS, or Linux. Often running a complete Bitcoin and Lightning node, desktop wallets are the most common in the Lightning Ecosystem as LN requires constant uptime to maintain channels.

**Mobile wallet**

Mobile wallets for Lightning run on iOS and Android. Many mobile wallets for Lightning are currently under development and have not reached maturity due to the requirement of hosting a full Bitcoin node to interact with the Lightning Network. Projects like `neutrino` are being explored to enable seamless mobile wallet adoption. Some current mobile wallets connect to hosted nodes and interact remotely. \_\_

**Hardware wallet**

Hardware wallets operate self-hosted Bitcoin and Lightning nodes on special hardware. By handling all Bitcoin and Lightning related operations on the hardware, hardware wallets can operate with high uptimes and can enable high levels of security.

**Web Wallet**

Web-based wallets are functioning Lightning or Bitcoin wallets built entirely on web services. Often containing minimal features, they allow for simple interaction with the Lightning Network or Bitcoin protocol.

Another way to categorize bitcoin wallets is by their degree of autonomy and how they interact with the bitcoin network:

**Full-node client**

A full client, or “full node,” is a client that stores the entire history of bitcoin transactions \(every transaction by every user, ever\), manages users’ wallets, and can initiate transactions directly on the bitcoin and Lightning network. A full node handles all aspects of the protocol and can independently validate the entire blockchain and any transaction. A full-node client consumes substantial computer resources \(e.g., more than 125 GB of disk, 2 GB of RAM\) but offers complete autonomy and independent transaction verification.

**Lightweight client**

A lightweight client, also known as a simple-payment-verification \(SPV\) client, connects to bitcoin full nodes or uses protocols like `neutrino` for access to the bitcoin transaction information, but stores the user wallet locally and independently creates, validates, and transmits transactions. Lightweight clients interact directly with the bitcoin network without an intermediary.

**Third-party API client**

A third-party API client is one that interacts with bitcoin or Lightning through a third-party system of application programming interfaces \(APIs\), rather than by connecting to the bitcoin network directly. The wallet may be stored by the user or by third-party servers, but all transactions go through a third party.

## Resources

[Lightning Compatible Wallets](https://lightningnetworkstores.com/wallets)

## References

\[1\] [https://en.bitcoin.it/wiki/Wallet](https://en.bitcoin.it/wiki/Wallet)

\[2\] [https://github.com/bitcoinbook/bitcoinbook/blob/f8b883dcd4e3d1b9adf40fed59b7e898fbd9241f/ch05.asciidoc](https://github.com/bitcoinbook/bitcoinbook/blob/f8b883dcd4e3d1b9adf40fed59b7e898fbd9241f/ch05.asciidoc) \(content adapted\)

