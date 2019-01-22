---
latest-revision: '1999-01-29T00:00:00.000Z'
original-author: >-
  Isaac Newton (@appleman) < List of Original Authors' Real Name and Github;
  email address optional >
created: 1999-01-01 < ISO 8601 (yyyy-mm-dd) format >
status: >-
  < Draft | Under Review | Deferred | Proofing | Rejected | Withdrawn | Accepted
  | Superseded>
title: HLTC
contributors: >-
  Leonardo Da Vinci (@leodavinci); Galileo Galilei (@ggal) < List of
  contributors -- Real Name + Github; email optional >
type: null
description: Hashed Time Locked Contract
discussions-to: (GitHub PR)
category: null
---

# HTLC

## Overview

A **Hashed TimeLock Contract** or **HTLC** is a class of payments that allow transactions to be sent between parties who do not have a direct [channel ](../lightning-basics/payment-channel.md)on the Lightning Network. HTLC's rely on the fact that an individual can structure a payment such that another party can only accept it if the party knows the secret whose hash has been shared with them.

HTLC's use hashlocks and timelocks to require that the receiver of a payment either acknowledges receiving the payment prior to a deadline by generating cryptographic proof of payment or forfeits the ability to claim the payment, returning it to the payer. Because any receipt of funds triggers the creation of a new hash, this idea can be extended to allow a sequence of payments; with the right conditionality, payments can be securely routed through a series of users.

The cryptographic proof of payment the receiver generates can then be used to trigger other actions in other payments.

## Details

### Timelock

Timelocks are restrictions on transactions or outputs that only allow spending after a point in time. Bitcoin has had a transaction-level timelock feature from the first implementation.

### Issues

For all payments between two parties, HTLCs require hashlocks to be resolved and routes to be found. This results in higher work and bandwidth requirements for nodes in the network.

The completion of payments via a routed network using HTLCs is probabilistic, depending on \(1\) the availability \("liveness"\) of users and \(2\) the quantity of funds held by those users. To forward payments through the network, users must be live and must have locked funds in a greater quantity than the payment they are forwarding. This makes the network geared towards dedicated payment processors who will forward transactions in exchange for fees.

### Section 3

## Resources

### Key People

* [Person 1](hltc.md)
* [Person 2](hltc.md)

### See also

## References

