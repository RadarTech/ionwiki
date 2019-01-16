---
latest-revision: '1999-01-29T00:00:00.000Z'
original-author: >-
  Isaac Newton (@appleman) < List of Original Authors' Real Name and Github;
  email address optional >
created: 1999-01-01 < ISO 8601 (yyyy-mm-dd) format >
status: >-
  < Draft | Under Review | Deferred | Proofing | Rejected | Withdrawn | Accepted
  | Superseded>
title: Auto-pilot (channels)
contributors: >-
  Leonardo Da Vinci (@leodavinci); Galileo Galilei (@ggal) < List of
  contributors -- Real Name + Github; email optional >
type: null
description: Description guidelines
discussions-to: (GitHub PR)
category: null
---

# Channel Autopilot

## Overview

## _NOTE: Gareth has already written autopilot details in the_ [_Channel Opening_](../lightning-channels/channel-opening.md) _page._

_The Autopilot in Carol’s Lightning App has connected with a series of Lightning routing nodes \(specifically selected for uptime and payment reliability\) and has opened Lightning payment channels with those nodes. By default, five channels will be opened, so if one routing node goes offline and/or funds need to be recovered via on-chain transaction, 80% of funds will still be available. These are details Carol doesn’t need to be concerned with. As far as she knows, her money is now instantly accessible with Lightning, and she can send money to any Lightning-enabled person or business._

_The latest build of `lnd` comes equipped with a new experimental option for_ [_any planned flavors of automatic channel management_](https://github.com/lightningnetwork/lnd/commit/306c4aef8e3af44fb3f2d8f52fc887f2c48e9c04)_, meaning users won’t necessarily need to manually establish channels. We call this new operating node `autopilot` as it will automatically manage the opening of channels within the network._

_`autopilot` is essentially a closed-loop control system: it takes inputs such as the number of channels opened, time when channels are closed, and changes to the wallet’s balance. Once those signals are received, it consults a set of heuristic to decide if it needs more channels, and if so, to whom those channels should be opened. The Agent then carries out the recommendations of its heuristics._

_Once your wallet is loaded with testnet coins, you’ll start to see `autopilot` at work on the Channels page. The `autopilot` agent will begin opening channels driven by its heuristics. This process also helps drive the network graph toward a scale-free topology._

![Desktop Application](https://blog.lightning.engineering/assets/images/app-auto.png)

_Channels are shown in two statuses: PENDING-OPEN, and ACTIVE. The PENDING-OPEN stage indicates that the funding transaction has been broadcast, but is still awaiting confirmation on the blockchain. The ACTIVE status indicates that a channel is fully open and ready to send and receive payments._

_feature including settings optimizing for both everyday use and fee revenue._

  


## Details

### Section 1

### Section 2

### Section 3

## Resources

### Key People

* [Person 1](auto-pilot-channels.md)
* [Person 2](auto-pilot-channels.md)

### See also

## References

