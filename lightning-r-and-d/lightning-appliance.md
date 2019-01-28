---
latest-revision: '2019-01-27T00:00:00.000Z'
original-author: Ryan Shea (ryan-shea)
created: '2019-01-01T00:00:00.000Z'
status: Accepted
title: Lightning Appliance
contributors: Ryan Shea (ryan-shea); Gareth James (gjradar)
type: article
description: ''
discussions-to: GitHub URL
category: lightning-rnd
---

# Lightning Appliance

## Overview

A **lightning appliance** is a dedicated piece of hardware that runs a Lightning node and Bitcoin wallet. Enabling secure storage, high uptime, and total customizability, appliances are a common way of interacting with the Lightning Network.

There are two models for appliances: paid products and self-hosted nodes.

## Details

### Hardware Advantage

#### Bitcoin Node

Connecting to the Lightning Network requires both the ability to run a Lightning Network daemon and interact with the Bitcoin blockchain. On-chain transactions are required for opening and closing channels in the Lightning Network, which necessitates communication between a Lightning Network node and a source of blockchain data. A common advantage of a dedicated lightning appliance is the ability to run a Bitcoin full node on the same hardware as a Lightning Network daemon. Given the storage requirements of running a full node, which entails hosting all historical block data and the current UTXO set, many mobile devices and home computers are unable to do so. Running a local full node removes any dependency on a third party's blockchain data or the risk of using an SPV \(Simplified Payment Verification\) client.

## Resources

### Existing LN Appliances

* [Casa Node](https://keys.casa/lightning-bitcoin-node/)

### See also

[Run a Lightning Node](https://medium.com/coinmonks/bitcoin-lightning-network-run-your-node-at-home-for-fun-and-no-profit-da5b61be2ba9)

## References

\[1\] [https://keys.casa/](https://keys.casa/)

\[2\] [https://medium.com/coinmonks/the-lightning-network-how-to-install-and-hopefully-make-money-6e3058e3fa7c](https://medium.com/coinmonks/the-lightning-network-how-to-install-and-hopefully-make-money-6e3058e3fa7c)

