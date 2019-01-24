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

**Opening a channel** between two parties on the Lightning network begins with sending an on-chain transaction to a multisig address controlled by the channel's participants. This initial funding transaction creates the channel that are controlled by both parties. The shared address can be funded as a single-payer channel, or by both parties involved.

## Details

### Transaction Confirmation

The initial funding transaction creates the channel that is controlled by both parties. This transaction is performed on-chain and is subject to traditional transaction fees and resolving times. The participants in the channel will often wait for a certain number of transaction confirmations before making channel payments. The number of confirmations required is negotiated in initial channel parameters.

### Autopilot

Lightning Network implementations can be equipped with 'autopilot' functionality, which automates the process of finding, funding and establishing a payments channel with another node. This can be helpful for new users who want to expedite their node setup and may have no preference of which node to connect with, or who have no experience with opening a channel. 

Autopilot features require criteria to select which nodes to establish channels with. These criteria vary across implementation and wallet software. Criteria could include uptime, measures of channel connectivity, fee levels, outbound channel volume, and relative position in the network. 

## Resources

[Lightning Network Introduction](https://lightning.network/#intro)

### See also

[Lightning Channel FAQ](https://medium.com/@The1Brand7/lightning-faq-67bd2b957d70)

## References

\[1\] [https://bitcoinmagazine.com/articles/understanding-the-lightning-network-part-building-a-bidirectional-payment-channel-1464710791/](https://bitcoinmagazine.com/articles/understanding-the-lightning-network-part-building-a-bidirectional-payment-channel-1464710791/)

\[2\] [https://counterparty.io/docs/paymentchannels-lightning-faq/](https://counterparty.io/docs/paymentchannels-lightning-faq/)

\[3\] [https://medium.com/@rusty\_lightning/bitcoin-lightning-things-to-know-e5ea8d84369f](https://medium.com/@rusty_lightning/bitcoin-lightning-things-to-know-e5ea8d84369f)

