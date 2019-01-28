---
latest-revision: '2019-01-27T00:00:00.000Z'
original-author: Ryan Shea (ryan-shea)
created: '2019-01-01T00:00:00.000Z'
status: Accepted
title: Onion routing
contributors: Ryan Shea (ryan-shea); Gareth James (gjradar)
type: article
description: ''
discussions-to: GitHub URL
category: lightning-basics
---

# Onion Routing

## Overview

**Onion routing** is a technique for anonymous [routing](payment-routing.md) of payments over the Lightning Network. Routing messages are encapsulated in layers of encryption, analogous to layers of an onion. The encrypted data is transmitted through [nodes ](node.md)on the network, each of which "peels" away a single layer, uncovering the data's next destination. When the final layer of routing information is decrypted, the message arrives at its destination. The sender remains anonymous because each intermediary knows only the location of the immediately preceding and following nodes.

Onion routing means that each note only sees the immediate hope before it and the immediate hop after that. It is called onion routing because the routing information is wrapped in layers. So a node receives an encrypted package from the node one hop before it, and doesn't know where the final destination is. You unwrap one layer which tells you to go for the next

## Details

### Path Calculation

When calculating a route for a payment from the sender to a receiver, the route is constructed by the payment sender \(source routing\) rather than being determined by the routers along the path. The sender builds a set of instructions wrapped in various layers of encryption, analogous to an onion. Each layer of encryption is meant for a single node constructed in the initial routing procedure.

This means that intermediate nodes in the payment path know only the identity of their immediate predecessor and successor in the route. The combination of source routing and onion routing protects the identities of payment senders and receivers so as to enhance user privacy and censorship-resistance.

### Limitations

A route produced via source and onion routing is limited to 20 steps.

## Resources

[Onion Routing, Wikipedia](https://en.wikipedia.org/wiki/Onion_routing)

[lightning-onion, GitHub](https://github.com/lightningnetwork/lightning-onion)

## References

\[1\][ BOLT \#4](https://github.com/lightningnetwork/lightning-rfc/blob/master/04-onion-routing.md)

\[2\] [Bitcoin Book](https://github.com/bitcoinbook/bitcoinbook/blob/f8b883dcd4e3d1b9adf40fed59b7e898fbd9241f/ch12.asciidoc)

