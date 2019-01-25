---
latest-revision: '1999-01-29T00:00:00.000Z'
original-author: >-
  Isaac Newton (@appleman) < List of Original Authors' Real Name and Github;
  email address optional >
created: 1999-01-01 < ISO 8601 (yyyy-mm-dd) format >
status: >-
  < Draft | Under Review | Deferred | Proofing | Rejected | Withdrawn | Accepted
  | Superseded>
title: Node
contributors: >-
  Leonardo Da Vinci (@leodavinci); Galileo Galilei (@ggal) < List of
  contributors -- Real Name + Github; email optional >
type: null
description: Description guidelines
discussions-to: (GitHub PR)
category: null
---

# Node

## Overview

A **node** is an entity on the Lightning Network that is able to connect to other nodes by establishing a [payment channel](payment-channel.md). Users can create a node by running an implementation of [Lightning Network software](../lightning-software/implementations-of-lightning-network.md), either directly or as part of pre-packaged [wallet](../lightning-software/wallet/) software. 

This should not be confused with a Bitcoin full node that validates Bitcoin blocks, although a full node's wallet may also be simultaneously used as a Lightning node to the advantage of the Lightning network user.

## Details

### Routing Nodes

Routing node is another term for a [hub](hub.md). A functional routing node requires high uptime and strong connectivity to other nodes in order to facilitate consistent, reliable and economic routing. Routing nodes have the ability to charge fees for passing traffic through to the remainder of the route. 

## Resources

[BOLT \#0](https://github.com/lightningnetwork/lightning-rfc/blob/master/00-introduction.md)

## References

\[1\] [https://lightning.network/lightning-network-paper.pdf](https://lightning.network/lightning-network-paper.pdf)

