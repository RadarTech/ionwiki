---
latest-revision: '2019-01-27T00:00:00.000Z'
original-author: Ryan Shea (ryan-shea)
created: '2019-01-01T00:00:00.000Z'
status: Accepted
title: Basis of Lightning Technology (BOLT)
contributors: Ryan Shea (ryan-shea); Gareth James (gjradar)
type: article
description: ''
discussions-to: GitHub URL
category: lightning-basics
---

# Basis of Lightning Technology \(BOLT\)

## Overview

The **Basis of Lightning Technology** is a standardized technical specification for the implementation of the Lightning Network. The standards define how various implementations can interoperate to interact with and create the same network. The specifications are currently a work-in-progress, and are continually being iterated upon as projects like [**lnd**](../../tutorials/lightning-software/lnd/) and [**c-lightning**](../../tutorials/lightning-software/c-lightning.md) are built in parallel.

## Details

The Basis of Lightning Technology \(BOLT\) documents describe a layer-2 protocol for off-chain bitcoin transfer by mutual cooperation, relying on on-chain transactions for enforcement if necessary.

### Channels

See [BOLT \#2: Channel Establishment](https://github.com/lightningnetwork/lightning-rfc/blob/master/02-peer-protocol.md#channel-establishment) for more on channel establishment and [BOLT \#3: Funding Transaction Output](https://github.com/lightningnetwork/lightning-rfc/blob/master/03-transactions.md#funding-transaction-output) for the format of the bitcoin transaction that creates the channel. See [BOLT \#5: Recommendations for On-chain Transaction Handling](https://github.com/lightningnetwork/lightning-rfc/blob/master/05-onchain.md) for the requirements when participants disagree or fail, and the cross-signed bitcoin transaction must be spent.

### Conditional Payments

See [BOLT \#2: Adding an HTLC](https://github.com/lightningnetwork/lightning-rfc/blob/master/02-peer-protocol.md#adding-an-htlc-update_add_htlc) for the commands a participant uses to add a conditional payment, and [BOLT \#3: Commitment Transaction](https://github.com/lightningnetwork/lightning-rfc/blob/master/03-transactions.md#commitment-transaction) for the complete format of the bitcoin transaction.

### Forwarding

See [BOLT \#2: Forwarding HTLCs](https://github.com/lightningnetwork/lightning-rfc/blob/master/02-peer-protocol.md#forwarding-htlcs) for details on forwarding payments, [BOLT \#4: Packet Structure](https://github.com/lightningnetwork/lightning-rfc/blob/master/04-onion-routing.md#packet-structure) for how payment instructions are transported.

### Network Topology

See [BOLT \#7: P2P Node and Channel Discovery](https://github.com/lightningnetwork/lightning-rfc/blob/master/07-routing-gossip.md) for details on the communication protocol, and [BOLT \#10: DNS Bootstrap and Assisted Node Location](https://github.com/lightningnetwork/lightning-rfc/blob/master/10-dns-bootstrap.md) for initial network bootstrap.

### Payment Invoicing

See [BOLT \#11: Invoice Protocol for Lightning Payments](https://github.com/lightningnetwork/lightning-rfc/blob/master/11-payment-encoding.md) for the protocol describing the destination and purpose of a payment such that the payer can later prove successful payment.

## Resources

[https://github.com/lightningnetwork/lightning-rfc](https://github.com/lightningnetwork/lightning-rfc)

## References

\[1\] [https://github.com/lightningnetwork/lightning-rfc/blob/master/00-introduction.md](https://github.com/lightningnetwork/lightning-rfc/blob/master/00-introduction.md)

