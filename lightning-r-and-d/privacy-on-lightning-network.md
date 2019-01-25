---
latest-revision: '1999-01-29T00:00:00.000Z'
original-author: >-
  Isaac Newton (@appleman) < List of Original Authors' Real Name and Github;
  email address optional >
created: 1999-01-01 < ISO 8601 (yyyy-mm-dd) format >
status: >-
  < Draft | Under Review | Deferred | Proofing | Rejected | Withdrawn | Accepted
  | Superseded>
title: Privacy (on lightning network)
contributors: >-
  Leonardo Da Vinci (@leodavinci); Galileo Galilei (@ggal) < List of
  contributors -- Real Name + Github; email optional >
type: null
description: Description guidelines
discussions-to: (GitHub PR)
category: null
---

# Privacy \(on Lightning Network\)

## Overview

While there is no public, trackable ledger of Lightning transactions, **privacy** __on Lightning is still a work in progress. Through techniques like [onion routing](../lightning-basics/onion-routing.md) and [eltoo](eltoo.md), privacy is improving.  

## Details

### Implementation of Sphinx

The current Lightning Network specification includes a solution to mask routing data from all intermediaries, based on [Sphinx](../lightning-basics/sphinx-packet.md).

On Lightning, the payer determines a path over the peer-to-peer network and wraps a payment package in layers of encryption. Apart from just relay information, each intermediary also unpacks some additional data. This includes amounts, fees and more, along with allowing all intermediaries to set up a step in the payment chain.

Importantly, all intermediaries only learn from which channel they receive tokens, and to which channel they must forward the payment. The intermediaries have no idea whether they are the first step in the chain, the last step, a step somewhere in the middle, or perhaps even the only step. Whoever originally sent the transaction, and the one who ultimately receives it, remain known to only the sender and the receiver.

## Resources

[Will Lightning Help or Hurt Bitcoin Privacy?](https://www.coindesk.com/will-lightning-help-hurt-bitcoin-privacy)

## References

\[1\] [https://medium.com/@rusty\_lightning/the-bitcoin-lightning-spec-part-5-8-onion-routing-protocol-86c91e455909](https://medium.com/@rusty_lightning/the-bitcoin-lightning-spec-part-5-8-onion-routing-protocol-86c91e455909)

\[2\] [https://bitcoinmagazine.com/articles/how-the-lightning-network-layers-privacy-on-top-of-bitcoin-1482183775/](https://bitcoinmagazine.com/articles/how-the-lightning-network-layers-privacy-on-top-of-bitcoin-1482183775/)

