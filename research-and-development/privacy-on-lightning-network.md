---
latest-revision: '2019-01-27T00:00:00.000Z'
original-author: Ryan Shea (ryan-shea)
created: '2019-01-01T00:00:00.000Z'
status: Accepted
title: Privacy (on Lightning Network)
contributors: Ryan Shea (ryan-shea)
type: article
description: ''
discussions-to: GitHub URL
category: lightning-rnd
---

# Privacy

## Overview

While there is no public, trackable ledger of Lightning transactions, **privacy** \_\_on Lightning is still a work in progress. Through techniques like [onion routing](../lightning-basics-1/lightning-basics/onion-routing.md) and [eltoo](eltoo.md), privacy is improving.

## Details

### Implementation of Sphinx

The current Lightning Network specification includes a solution to mask routing data from all intermediaries, based on [Sphinx](../lightning-basics-1/lightning-basics/sphinx-packet.md).

On Lightning, the payer determines a path over the peer-to-peer network and wraps a payment package in layers of encryption. Apart from just relay information, each intermediary also unpacks some additional data. This includes amounts, fees and more, along with allowing all intermediaries to set up a step in the payment chain.

Importantly, all intermediaries only learn from which channel they receive tokens, and to which channel they must forward the payment. The intermediaries have no idea whether they are the first step in the chain, the last step, a step somewhere in the middle, or perhaps even the only step. Whoever originally sent the transaction, and the one who ultimately receives it, remain known to only the sender and the receiver.

## Resources

[Will Lightning Help or Hurt Bitcoin Privacy?](https://www.coindesk.com/will-lightning-help-hurt-bitcoin-privacy)

## References

\[1\] [https://medium.com/@rusty\_lightning/the-bitcoin-lightning-spec-part-5-8-onion-routing-protocol-86c91e455909](https://medium.com/@rusty_lightning/the-bitcoin-lightning-spec-part-5-8-onion-routing-protocol-86c91e455909)

\[2\] [https://bitcoinmagazine.com/articles/how-the-lightning-network-layers-privacy-on-top-of-bitcoin-1482183775/](https://bitcoinmagazine.com/articles/how-the-lightning-network-layers-privacy-on-top-of-bitcoin-1482183775/)

