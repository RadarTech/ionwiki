---
category: bitcoin-basics
contributors: "Ryan Shea (ryan-shea); Gareth James (gjradar)"
created: 2019-01-01
description: ""
discussions-to: "GitHub URL"
latest-revision: 2019-01-27
original-author: "Ryan Shea (ryan-shea)"
status: "Accepted"
title: "HTLC"
type: article
---

# HTLC

## Overview

A **Hashed TimeLock Contract** or **HTLC** is smart contract that allows transactions to be sent between parties who do not have a direct [channel ](../lightning-basics/payment-channel.md)on the Lightning Network. HTLC's rely on the fact that an individual can structure a payment such that another party can only accept it if the party knows the secret whose [hash](hash.md) has been shared with them.

HTLC's use hashlocks and timelocks to ensure payment security. HTLC's require that the receiver of a payment acknowledges receiving the payment prior to a deadline by generating cryptographic proof of payment or forfeits the ability to claim the payment, returning it to the payer. Because any receipt of funds triggers the creation of a new hash, this idea can be extended to allow a sequence of payments; with the right conditionality, payments can be securely routed through a series of users.

The cryptographic proof of payment the receiver generates can then be used to trigger other actions in other payments.

## Details

### Functionality

The completion of payments via a routed network using HTLCs is probabilistic, depending on the availability of users and the quantity of funds held by those users. To forward payments through the network, users must be live and must have locked funds in a greater quantity than the payment they are forwarding. This makes the network geared towards dedicated payment processors who will forward transactions in exchange for fees.

### Hashlock

Hashlocks restrict the spending of an output until a specified piece of data is publicly revealed. This allows for payments to be routed through third parties without any risk that the third parties will take the payments themselves.

### Timelock

Timelocks are restrictions on transactions or outputs that only allow spending after a point in time. Timelocks ensure that routed payments cannot be claimed by intermediate nodes. Timelocks require the production of a verifiable digital signature before a certain time.

If the secret is not revealed, the payer of the HTLC can get a “refund” after some time. This is achieved with an absolute time lock using `CHECKLOCKTIMEVERIFY`.

### HTLC Code

An HTLC is an additional output in a Commitment Transaction with a unique output script:

```text
OP IF
    OP HASH160 <Hash160 (R)> OP EQUALVERIFY
    2 <Alice2> <Bob2> OP CHECKMULTISIG
OP ELSE
    2 <Alice1> <Bob1> OP CHECKMULTISIG
OP ENDIF
```

Conceptually, this script has two possible paths spending from a single HTLC output. The first path \(defined in the `OP IF`\) sends funds to Bob if Bob can produce R. The second path is redeemed using a 3-day timelocked refund to Alice. The 3-day timelock is enforced using nLockTime from the spending transaction.

### Issues

For all payments between two parties, HTLCs require hashlocks to be resolved and routes to be found. This results in higher work and bandwidth requirements for nodes in the network.

## Resources

[HTLCs in the Lightning Network Whitepaper](https://lightning.network/lightning-network-paper.pdf)

## References

\[1\] [https://en.bitcoin.it/wiki/Hashed\_Timelock\_Contracts](https://en.bitcoin.it/wiki/Hashed_Timelock_Contracts)
