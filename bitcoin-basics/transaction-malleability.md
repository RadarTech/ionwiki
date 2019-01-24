---
latest-revision: '1999-01-29T00:00:00.000Z'
original-author: >-
  Isaac Newton (@appleman) < List of Original Authors' Real Name and Github;
  email address optional >
created: 1999-01-01 < ISO 8601 (yyyy-mm-dd) format >
status: >-
  < Draft | Under Review | Deferred | Proofing | Rejected | Withdrawn | Accepted
  | Superseded>
title: Transaction Malleability
contributors: >-
  Leonardo Da Vinci (@leodavinci); Galileo Galilei (@ggal) < List of
  contributors -- Real Name + Github; email optional >
type: null
description: Description guidelines
discussions-to: (GitHub PR)
category: null
---

# Transaction Malleability

## Overview

**Transaction malleability** is ability of someone to change unconfirmed transactions without making them invalid, which changes the transaction’s txid, making child transactions invalid.

## Details

### Explained

Malleability is a problem that has been in Bitcoin for many years, it is well known and it is not too hard to make sure a business can't lose money over this. The problem really should get fixed, though, as it is a rather embarrassing issue.

The high level problem is this; A user can create a transaction, which she signs and sends off to the network in order to get mined. Transactions get automatically assigned a transaction-ID. To uniquely identify that transaction. This assignment is done in a smart way such that the ID is assigned based on the content. This way we avoid having to ask a central server to give unique IDs.

There is a way to change the transaction slightly so it still is a valid transaction that correctly moves money as the original author intended and doesn't break the signatures either. This is called the malleability issue. The small change will have as an effect that the transaction-ID changes, as its based on slightly different content now.

The result is that a company sending a transaction can not be certain that his transaction will have the same ID from the moment is was created to when it finally gets mined in a block.

MtGox claimed that this was a reason they lost funds where users would complain a transfer from the company to them never arrived and the exchange would only check the transaction ID having been mined.

### Transaction Malleability on Lightning

The Lightning Network works by creating a double-signed transaction. That is, we have a new check that requires both parties to sign for it to be valid. The check specifies how much is being sent from one party to another. As new micro-payments are made from one party to the other, the amount on the check is changed and both parties sign the result.

To start the Lightning Network channel, this double-signed check must be funded. In order that the double-signed check isn’t held captive by an uncooperative counterparty, the double-signed check is signed by both parties before the funding transaction is sent out to the network.

For the Lightning Network to work, we need the funding transaction to not be broadcast until the double-signed check is signed.

Because the double-signed check refers to the funding transaction’s identifier, if the funding transaction’s identifier is changed, the double-signed check will become invalid. This represents a risk to opening the Lightning Network channel. There are ways to make the Lightning Network work without this fixing transaction malleability, but LN is easier when transaction malleability is fixed.

## Resources

[Transaction Malleability Explained](https://bitcointechtalk.com/transaction-malleability-explained-b7e240236fc7)

### See also

## References

\[1\] [https://en.bitcoin.it/wiki/Transaction\_malleability](https://en.bitcoin.it/wiki/Transaction_malleability)

\[2\] [https://bitcoin.org/en/glossary/malleability](https://bitcoin.org/en/glossary/malleability)

