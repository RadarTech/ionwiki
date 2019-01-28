---
latest-revision: '2019-01-27T00:00:00.000Z'
original-author: Ryan Shea (ryan-shea)
created: '2019-01-01T00:00:00.000Z'
status: Accepted
title: Watchtower
contributors: Ryan Shea (ryan-shea)
type: article
description: ''
discussions-to: GitHub URL
category: lightning-rnd
---

# Watchtowers

## Overview

**Watchtowers** are a service that provide protection in case something goes wrong with payment channels while disconnected from the internet for an extended period of time. Watchtowers, conceptually, will automatically handle the recovery process for users in the case of a channel breach.

## Details

### Problem

Payment channels introduce a new and undesirable assumption that a party must remain on-line and synchronized with the blockchain at all times to defend against execution fork attacks. An execution fork can revert a payment channel’s history, potentially causing financial damage to a party that is innocent except for having crashed. To provide security even to parties that may go off-line for an extended period of time, watchtowers are under development, protocols that are enables such parties to delegate to a third party, called the custodian, to cancel execution forks on their behalf.

### Functionality

Watchtowers implement unlinkable channel monitoring and recovery for Lightning network channels. A watchtower is a program that watches the blockchain to see when a particular transaction is broadcast to the mempool.

If that transaction is flagged in its memory as part of an outdated contract, it broadcasts the latest version of the contract it knows about. They have no control of funds. They don't need ID about their users or where the funds are destined for. They are simple tools for identifying old contracts that somehow get broadcasted, and replacing them with the latest versions.

## Resources

[Watchtower Support is coming to Bitcoin Lightning Wallet](https://medium.com/@akumaigorodski/watchtower-support-is-coming-to-bitcoin-lightning-wallet-8f969ac206b2)

### See also

[Pisa: Arbitration Outsourcing for State Channels](https://eprint.iacr.org/2018/582.pdf)

## References

\[1\] [https://lists.linuxfoundation.org/pipermail/lightning-dev/2018-April/001196.html](https://lists.linuxfoundation.org/pipermail/lightning-dev/2018-April/001196.html)

\[2\] [https://github.com/mit-dci/lit/tree/master/watchtower](https://github.com/mit-dci/lit/tree/master/watchtower)

