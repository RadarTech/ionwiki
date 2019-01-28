---
category: lightning-basics
contributors: "Ryan Shea (ryan-shea); Gareth James (gjradar)"
created: 2019-01-01
description: ""
discussions-to: "GitHub URL"
latest-revision: 2019-01-27
original-author: "Ryan Shea (ryan-shea)"
status: "Accepted"
title: "Payment Channel"
type: article
---

# Payment Channel

## Overview

On the [Lightning Network](lightning-network.md), a **payment channel** is a direct, bi-directional payment connection between two [nodes](node.md).

Payment channels are the primary building block for the Lightning Network as they allow for fast, low-cost transactions. Through on-chain [opening](../lightning-channels/channel-opening.md) and [closing ](../lightning-channels/channel-closing.md)transactions, payment channels leverage the security of the underlying blockchain to provide trustless payments between two parties. Based on the balance and [capacity](../lightning-channels/channel-capacity.md) of the channel, users exchange 'off-chain' commitments to each other outside of the Bitcoin blockchain. Payments within a channel are off-chain and do not require validation by or communication to the broader network. This means there is no explicit cost to each payment and no limit to the number of payments able to be shared within a channel.

A payment channel can be [closed ](../lightning-channels/channel-closing.md)by broadcasting an on-chain transaction agreed upon by both parties that finalizes the net balance transferred over the life of the channel.

## Details

A channel is a fast, off chain method of mutually exchanging funds between to peers. To transact funds, peers exchange signatures to create a multi signature commitment transaction. The participants then fund the channel with an on-chain transaction, adding funds to the channel \(e.g., 0.1 bitcoin\) that is locked on the Bitcoin network. It is spendable only with both their signatures.

Initially they each hold a bitcoin transaction that sends all the bitcoin \(e.g. 0.1 bitcoin\) back to one party. They can later sign a new bitcoin transaction that splits these funds differently, e.g. 0.09 bitcoin to one party, 0.01 bitcoin to the other, and invalidate the previous bitcoin transaction so it won't be spent.

### Use Cases

An ideal use case for the technology is **micropayments**: Imagine a user making numerous very small payments \(e.g. .0001 BTC\) to a streaming service as they listen to songs over a certain period. Without payment channels, the Bitcoin transaction fees from these small payments would be as much or more than the payments themselves, and each payment would take on average 10 minutes to clear.

Other potential use cases:

* Rewarding users for specific actions they take, such as contributing content to a blog, or writing a review
* Incrementally purchasing a service offering[j](https://storj.io/)
* Payments for other digital/virtual goods, such as a “contributor” badge on a forum
* Referral network payments
* Small/regular donations to charities, projects or individuals
* Enabling rental of Counterparty asset names

## Resources

[Lightning Network Whitepaper](https://lightning.network/lightning-network-paper.pdf)

### See also

[Lightning Networks Part I: Revocable Transactions](https://rusty.ozlabs.org/?p=450)

## References

\[1\] [https://counterparty.io/docs/paymentchannels-lightning-faq/](https://counterparty.io/docs/paymentchannels-lightning-faq/)

\[2\] [https://lightning.network/lightning-network-paper.pdf](https://lightning.network/lightning-network-paper.pdf)
