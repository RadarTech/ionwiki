---
latest-revision: '2019-01-27T00:00:00.000Z'
original-author: Ryan Shea (ryan-shea)
created: '2019-01-01T00:00:00.000Z'
status: Accepted
title: Transaction Malleability
contributors: Ryan Shea (ryan-shea); Gareth James (gjradar)
type: article
description: ''
discussions-to: GitHub URL
category: bitcoin-basics
---

# Transaction Malleability

## Overview

**Transaction malleability** is process of changing the unique identifier of a transaction by changing the digital signature used to create it. It enables unconfirmed transactions to change without making them invalid. Changing the transaction’s `txid` makes child transactions invalid.

## Details

### Transaction Malleability on Lightning

Lightning Network channels work by creating a double-signed Bitcoin address and funding it. To initiate a channel, this double-signed address must be funded.

To ensure the double-signed address isn’t held captive by an uncooperative counterparty, the first funding transaction is signed by both parties before the funding transaction is sent on-chain.

For the Lightning Network to work, the funding transaction needs to not be broadcast until the double-signed address is created.

The double-signed address refers to the funding transaction’s identifier, so if the funding transaction’s identifier is changed using [malleability](transaction-malleability.md), the double-signed address will become invalid. This represented a risk in opening a Lightning channel before `segwit` was implemented into the protocol.

### SegWit

Signatures are the only way in which transaction identifiers can be changed by an attacker. With SegWit, a new patch to the Bitcoin protocol, the transaction identifier no longer takes into account the signature.

The signature data in the unlocking script is moved and omitted when calculating the transaction ID of the transaction data. The result of this is if a bad actor modifies the signature data, the transaction ID will remain exactly the same.

This means that even if the attacker changes the signature, the transaction identifier stays the same. Signatures are still checked, just not used in calculating the transaction identifier.

SegWit was successfully activated on the Bitcoin network on 21st July 2017.

## Resources

[Transaction Malleability Explained](https://bitcointechtalk.com/transaction-malleability-explained-b7e240236fc7)

## References

\[1\] [https://en.bitcoin.it/wiki/Transaction\_malleability](https://en.bitcoin.it/wiki/Transaction_malleability)

\[2\] [https://bitcoin.org/en/glossary/malleability](https://bitcoin.org/en/glossary/malleability)

