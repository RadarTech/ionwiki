---
latest-revision: '1999-01-29T00:00:00.000Z'
original-author: >-
  Isaac Newton (@appleman) < List of Original Authors' Real Name and Github;
  email address optional >
created: 1999-01-01 < ISO 8601 (yyyy-mm-dd) format >
status: >-
  < Draft | Under Review | Deferred | Proofing | Rejected | Withdrawn | Accepted
  | Superseded>
title: Channel closing
contributors: >-
  Leonardo Da Vinci (@leodavinci); Galileo Galilei (@ggal) < List of
  contributors -- Real Name + Github; email optional >
type: null
description: Description guidelines
discussions-to: (GitHub PR)
category: null
---

# Closing A Channel

## Overview

To **close** an established channel on the Lightning Network, a closing transaction must be initiated. On top of a normal mutual close, there are other ways to close a channel.

## Details

### Cooperative Close

In a mutual close, both channel participants agree to a cooperative close, where final channel amounts are settled on-chain. Both participants sign a digital signature that then authorizes the on chain settlement transaction.

Both parties are able to send as many payments to their counterparty as they wish, as long as they have funds available in the channel, knowing that in the event of disagreements they can broadcast to the blockchain the current state at any time. In the vast majority of cases, all the outputs from the Funding Transaction will never be broadcast on the blockchain. They are just there in case the other party is non-cooperative, much like how a contract is rarely enforced in the courts. A proven ability for the contract to be enforced in a deterministic manner is sufficient incentive for both parties to act honestly. When either party wishes to close out a channel cooperatively, they will be able to do so by contacting the other party and spending from the Funding Transaction with an output of the most current Commitment Transaction directly with no script encumbering conditions. No further payments may occur in the channel.

### Unilateral Close

In an uncooperative close of a channel, a peer broadcasts a commitment transaction. 

### Revoked Transaction Close

An invalid close of a channel, accomplished by broadcasting a revoked commitment transaction. Since the other peer knows the commitment revocation secret key, it can create a penalty transaction.

### Penalty Transaction

A transaction that spends all outputs of a revoked commitment transaction, using the commitment revocation private key. A peer uses this if the other peer tries to "cheat" by broadcasting a revoked commitment transaction.

## Resources

[BOLT \#0, Introduction and Index](https://github.com/lightningnetwork/lightning-rfc/blob/master/00-introduction.md)

## References

\[1\] [https://github.com/lightningnetwork/lightning-rfc/blob/master/00-introduction.md](https://github.com/lightningnetwork/lightning-rfc/blob/master/00-introduction.md)



