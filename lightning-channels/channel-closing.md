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

To close an established channel on the Lightning Network, a closing transaction must be initiated. On top of a normal, mutual close, there are other transactions that come into play.

## Details

### Mutual Close

In a mutual close, both channel participants agree a cooperative close, where final channel amounts are settled on-chain. 

### Unilateral Close

In an uncooperative close of a channel, a peer broadcasts a commitment transaction. 

### Revoked Transaction Close

An invalid close of a channel, accomplished by broadcasting a revoked commitment transaction. Since the other peer knows the commitment revocation secret key, it can create a penalty transaction.

### Penalty Transaction

A transaction that spends all outputs of a revoked commitment transaction, using the commitment revocation private key. A peer uses this if the other peer tries to "cheat" by broadcasting a revoked commitment transaction.



## Resources



### See also

## References

