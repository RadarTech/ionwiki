---
latest-revision: '2019-01-27T00:00:00.000Z'
original-author: Brandon Curtis (brandoncurtis)
created: '2019-01-01T00:00:00.000Z'
status: Accepted
title: Error Codes
contributors: Ryan Shea (ryan-shea); Brandon Curtis (brandoncurtis)
type: article
description: ''
discussions-to: GitHub URL
category: lightning-troubleshooting
---

# Error codes

## Overview

**Error codes** can be encountered when sending a payment or interacting with the Lightning Network via an [implementation](../lightning-software/implementations-of-lightning-network.md).

## Details

### Routing

#### `ErrNoPathFound`

ErrNoPathFound is returned when a path to the target destination does not exist in the graph.

#### `ErrNoRouteFound`

ErrNoRouteFound is returned when the router is unable to find a valid route to the target destination after fees and time-lock limitations are factored in.

#### `ErrInsufficientCapacity`

ErrInsufficientCapacity is returned when a path if found, yet the capacity of one of the channels in the path is insufficient to carry the payment. ErrMaxHopsExceeded is returned when a candidate path is found, but the length of that path exceeds HopLimit. ErrMaxHopsExceeded ErrTargetNotInNetwork is returned when the target of a path-finding or payment attempt isn't known to be within the current version of the channel graph. ErrTargetNotInNetwork ErrOutdated is returned when the routing update already have been applied, or a newer update is already known. ErrOutdated ErrIgnored is returned when the update have been ignored because this update can't bring us something new, or because a node announcement was given for node not found in any channel. ErrIgnored ErrRejected is returned if the update is for a channel ID that was previously added to the reject cache because of an invalid update was attempted to be processed. ErrRejected ErrPaymentAttemptTimeout is an error that indicates that a payment attempt timed out before we were able to successfully route an HTLC. ErrPaymentAttemptTimeout ErrFeeLimitExceeded is returned when the total fees of a route exceed the user-specified fee limit. ErrFeeLimitExceeded

### lnwire Errors

#### `ErrMaxPendingChannels`

ErrMaxPendingChannels is returned by remote peer when the number of active pending channels exceeds their maximum policy limit.

#### `ErrSynchronizingChain`

ErrSynchronizingChain is returned by a remote peer that receives a channel update or a funding request while their still syncing to the latest state of the blockchain.

#### `ErrChanTooLarge`

ErrChanTooLarge is returned by a remote peer that receives a FundingOpen request for a channel that is above their current soft-limit.

## Resources

[LND API Reference](https://api.lightning.community/)

## References

\[1\] [https://api.lightning.community/](https://api.lightning.community/)

\[2\] [https://github.com/lightningnetwork/lnd/blob/2103ebba959633c9c113df71f92610b3dfebe8ce/lnwire/error.go\#L9](https://github.com/lightningnetwork/lnd/blob/2103ebba959633c9c113df71f92610b3dfebe8ce/lnwire/error.go#L9)

