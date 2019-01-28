---
latest-revision: '2019-01-27T00:00:00.000Z'
original-author: Ryan Shea (ryan-shea)
created: '2019-01-01T00:00:00.000Z'
status: Accepted
title: Gossip
contributors: Ryan Shea (ryan-shea)
type: article
description: ''
discussions-to: GitHub URL
category: lightning-basics
---

# Gossip

## Overview

Node discovery, channel discovery, and channel updates are broadcasted through **gossip** messages on the Lightning network. Rather than relying on a third-party to distribute information, Lightning relies on announcements containing information with network updates.

## Details

### Channel Discovery

To support channel discovery, three _gossip messages_ are supported. Peers in the network exchange `channel_announcement` messages containing information regarding new channels between the two nodes. They can also exchange `channel_update` messages, which update information about a channel. There can only be one valid `channel_announcement` for any channel, but at least two `channel_update` messages are expected.

### Node Discovery

To support node discovery, peers exchange `node_announcement` messages, which supply additional information about the nodes. There may be multiple `node_announcement` messages, in order to update the node information.

## Resources

[BOLT \#7](https://github.com/lightningnetwork/lightning-rfc/blob/master/07-routing-gossip.md)

## References

\[1\] [https://github.com/lightningnetwork/lightning-rfc/blob/master/07-routing-gossip.md](https://github.com/lightningnetwork/lightning-rfc/blob/master/07-routing-gossip.md#rebroadcasting)

