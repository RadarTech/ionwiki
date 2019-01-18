---
latest-revision: '1999-01-29T00:00:00.000Z'
original-author: >-
  Isaac Newton (@appleman) < List of Original Authors' Real Name and Github;
  email address optional >
created: 1999-01-01 < ISO 8601 (yyyy-mm-dd) format >
status: >-
  < Draft | Under Review | Deferred | Proofing | Rejected | Withdrawn | Accepted
  | Superseded>
title: Channel opening
contributors: >-
  Leonardo Da Vinci (@leodavinci); Galileo Galilei (@ggal) < List of
  contributors -- Real Name + Github; email optional >
type: null
description: Description guidelines
discussions-to: (GitHub PR)
category: null
---

# Opening A Channel

## Overview

Opening a channel between two parties on the Lightning network begins with sending an on-chain transaction to a multisig address controlled by the channel's participants. This initial funding transaction creates the channel that are controlled by both parties. The shared address can be funded as a single-payer channel, or by both parties involved.

_Opening a channel involves sending an on-chain transaction \(with a multisig output controlled by the channel’s participants\), so when the channel is ‘pending’ it simply means this transaction is not yet confirmed. How long it takes the transaction to confirm depends on the same factors as any other transaction._

_Further, the participants will often wait for a certain number of transaction confirmations before starting to make channel payments. The number of confirmations required is negotiated in the `minimum_depth` parameter of the `accept_channel` message. From BOLT 2:_

> _The `funding_locked` message indicates that the funding transaction has reached the `minimum_depth` asked for in `accept_channel`. Once both nodes have sent this, the channel enters normal operating mode_

* _The Funding Transaction creates the channel. During this stage, funds are sent into a multisig address controlled by both Alice and Bob, the counterparties to the channel. This address can be funded as a single-payer channel or by both Alice and Bob._



## Details

### Transaction Confirmation

Initial 

### Autopilot

Lightning Network implementations can be equipped with 'autopilot' functionality, which automates the process of finding, funding and establishing a payments channel with another node. This can be helpful for new users who want to expedite their node setup and may have no preference of which node to connect with, or who have no experience with opening a channel. 

Autopilot features require criteria to select which nodes to establish channels with. These criteria vary across implementation and wallet software. Criteria could include uptime, measures of channel connectivity, fee levels, outbound channel volume, and relative position in the network. 

### Section 3

## Resources

### Key People

* [Person 1](channel-opening.md)
* [Person 2](channel-opening.md)

### See also

## References

