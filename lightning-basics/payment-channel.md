---
latest-revision: '1999-01-29T00:00:00.000Z'
original-author: >-
  Isaac Newton (@appleman) < List of Original Authors' Real Name and Github;
  email address optional >
created: 1999-01-01 < ISO 8601 (yyyy-mm-dd) format >
status: >-
  < Draft | Under Review | Deferred | Proofing | Rejected | Withdrawn | Accepted
  | Superseded>
title: Payment channel
contributors: >-
  Leonardo Da Vinci (@leodavinci); Galileo Galilei (@ggal) < List of
  contributors -- Real Name + Github; email optional >
type: null
description: Description guidelines
discussions-to: (GitHub PR)
category: null
---

# Payment Channel

## Overview

**Payment channels** allow two users of Bitcoin to transact commitments to pay back and forth between each other much faster and more fluidly than Bitcoin’s 10 minute block times would normally allow. These commitments are exchanged between the users outside of the Bitcoin blockchain. Once the users are done, they can close the payment channel by publishing the last commitment\(s\) to the blockchain, which will finalize the amount actually transacted.

An ideal use case for the technology is **micropayments**: Imagine a user making numerous very small payments \(e.g. .0001 BTC\) to Big Music Company as she listens to songs over a certain period. Without payment channels, the Bitcoin transaction fees from these small payments would be as much or more than the payments themselves, and each payment would take on average 10 minutes to clear.



Lightning works by establishing _channels_: two participants create a Lightning payment channel that contains some amount of bitcoin \(e.g., 0.1 bitcoin\) that they've locked up on the Bitcoin network. It is spendable only with both their signatures.

Initially they each hold a bitcoin transaction that sends all the bitcoin \(e.g. 0.1 bitcoin\) back to one party. They can later sign a new bitcoin transaction that splits these funds differently, e.g. 0.09 bitcoin to one party, 0.01 bitcoin to the other, and invalidate the previous bitcoin transaction so it won't be spent.



* * A fast, off-chain method of mutual exchange between two _peers_. To transact funds, peers exchange signatures to create an updated _commitment transaction_.
  * _See closure methods: mutual close, revoked transaction close, unilateral close_
  * _See related: route_



the primary building block for Lightning is the concept of payment channels, which allow for fast, low-cost transactions that leverage the security of an underlying blockchain



## Details

### Section 1



### Section 2

### Section 3

## Resources

### Key People

* [Person 1](payment-channel.md)
* [Person 2](payment-channel.md)

### See also

## References

