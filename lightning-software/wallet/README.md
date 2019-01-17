---
latest-revision: '1999-01-29T00:00:00.000Z'
original-author: >-
  Isaac Newton (@appleman) < List of Original Authors' Real Name and Github;
  email address optional >
created: 1999-01-01 < ISO 8601 (yyyy-mm-dd) format >
status: >-
  < Draft | Under Review | Deferred | Proofing | Rejected | Withdrawn | Accepted
  | Superseded>
title: Wallet
contributors: >-
  Leonardo Da Vinci (@leodavinci); Galileo Galilei (@ggal) < List of
  contributors -- Real Name + Github; email optional >
type: null
description: What is a wallet?
discussions-to: (GitHub PR)
category: null
---

# Wallet

## Overview

A **wallet** is an app or program that enables you to send and recieve Bitcoin. A Lightning-enabled wallet allows you to interact with the Lightning Network via channels. Wallets keep track of your BTC balance - which is usually held in one or more bitcoin addresses - and your transaction history.

_The word “wallet” is used to describe a few different things in bitcoin. At a high level, a wallet is an application that serves as the primary user interface. The wallet controls access to a user’s money, managing keys and addresses, tracking the balance, and creating and signing transactions. More narrowly, from a programmer’s perspective, the word “wallet” refers to the data structure used to store and manage a user’s keys. In this chapter we will look at the second meaning, where wallets are containers for private keys, usually implemented as structured files or simple databases._

## Details

### Wallet Function

_Keys are often stored in a digital wallet on each user’s computer or smartphone. Possession of the key that can sign a transaction is the only prerequisite to spending bitcoin, putting the control entirely in the hands of each user._

### Lightning-enabled Wallets

A _“bitcoin wallet” is the most common user interface to the bitcoin system, just like a web browser is the most common user interface for the HTTP protocol. There are many implementations and brands of bitcoin wallets, just like there are many brands of web browsers \(e.g., Chrome, Safari, Firefox, and Internet Explorer\). And just like we all have our favorite browsers \(Mozilla Firefox, Yay!\) and our villains \(Internet Explorer, Yuck!\), bitcoin wallets vary in quality, performance, security, privacy, and reliability. There is also a reference implementation of the bitcoin protocol that includes a wallet, known as the “Satoshi Client” or “Bitcoin Core,” which is derived from the original implementation written by Satoshi Nakamoto._

### Wallet Types

_Bitcoin wallets are one of the most actively developed applications in the bitcoin ecosystem. There is intense competition, and while a new wallet is probably being developed right now, several wallets from last year are no longer actively maintained. Many wallets focus on specific platforms or specific uses and some are more suitable for beginners while others are filled with features for advanced users. Choosing a wallet is highly subjective and depends on the use and user expertise. It is therefore impossible to recommend a specific brand or project of wallet. However, we can categorize bitcoin wallets according to their platform and function and provide some clarity about all the different types of wallets that exist. Better yet, moving money between bitcoin wallets is easy, cheap, and fast, so it is worth trying out several different wallets until you find one that fits your needs. Bitcoin wallets can be categorized as follows, according to the platform: Desktop wallet A desktop wallet was the first type of bitcoin wallet created as a reference implementation and many users run desktop wallets for the features, autonomy, and control they offer. Running on general-use operating systems such as Windows and Mac OS has certain security disadvantages however, as these platforms are often insecure and poorly configured. Mobile wallet A mobile wallet is the most common type of bitcoin wallet. Running on smart-phone operating systems such as Apple iOS and Android, these wallets are often a great choice for new users. Many are designed for simplicity and ease-of-use, but there are also fully featured mobile wallets for power users. Web wallet Web wallets are accessed through a web browser and store the user’s wallet on a server owned by a third party. This is similar to webmail in that it relies entirely on a third-party server. Some of these services operate using client-side code running in the user’s browser, which keeps control of the bitcoin keys in the hands of the user. Most, however, present a compromise by taking control of the bitcoin keys from users in exchange for ease-of-use. It is inadvisable to store large amounts of bitcoin on third-party systems. Hardware wallet Hardware wallets are devices that operate a secure self-contained bitcoin wallet on specialpurpose hardware. They are operated via USB with a desktop web browser or via near-fieldcommunication \(NFC\) on a mobile device. By handling all bitcoin-related operations on the specialized hardware, these wallets are considered very secure and suitable for storing large amounts of bitcoin. Paper wallet The keys controlling bitcoin can also be printed for long-term storage. These are known as paper wallets even though other materials \(wood, metal, etc.\) can be used. Paper wallets offer a low-tech but highly secure means of storing bitcoin long term. Offline storage is also often referred to as cold storage. Another way to categorize bitcoin wallets is by their degree of autonomy and how they interact with the bitcoin network: Full-node client A full client, or “full node,” is a client that stores the entire history of bitcoin transactions \(every transaction by every user, ever\), manages users’ wallets, and can initiate transactions directly on the bitcoin network. A full node handles all aspects of the protocol and can independently validate the entire blockchain and any transaction. A full-node client consumes substantial computer resources \(e.g., more than 125 GB of disk, 2 GB of RAM\) but offers complete autonomy and independent transaction verification. Lightweight client A lightweight client, also known as a simple-payment-verification \(SPV\) client, connects to bitcoin full nodes \(mentioned previously\) for access to the bitcoin transaction information, but stores the user wallet locally and independently creates, validates, and transmits transactions. Lightweight clients interact directly with the bitcoin network, without an intermediary. Third-party API client A third-party API client is one that interacts with bitcoin through a third-party system of application programming interfaces \(APIs\), rather than by connecting to the bitcoin network directly. The wallet may be stored by the user or by third-party servers, but all transactions go through a third party. Combining these categorizations, many bitcoin wallets fall into a few groups, with the three most common being desktop full client, mobile lightweight wallet, and web third-party wallet. The lines between different categories are often blurry, as many wallets run on multiple platforms and can interact with the network in different ways. For the purposes of this book, we will be demonstrating the use of a variety of downloadable bitcoin clients, from the reference implementation \(Bitcoin Core\) to mobile and web wallets. Some of the examples will require the use of Bitcoin Core, which, in addition to being a full client, also exposes APIs to the wallet, network, and transaction services. If you are planning to explore the programmatic interfaces into the bitcoin system, you will need to run Bitc_

_Section 3_

## Resources

### See also

## References

