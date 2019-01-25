---
latest-revision: '1999-01-29T00:00:00.000Z'
original-author: >-
  Isaac Newton (@appleman) < List of Original Authors' Real Name and Github;
  email address optional >
created: 1999-01-01 < ISO 8601 (yyyy-mm-dd) format >
status: >-
  < Draft | Under Review | Deferred | Proofing | Rejected | Withdrawn | Accepted
  | Superseded>
title: Channel factory
contributors: >-
  Leonardo Da Vinci (@leodavinci); Galileo Galilei (@ggal) < List of
  contributors -- Real Name + Github; email optional >
type: null
description: Description guidelines
discussions-to: (GitHub PR)
category: null
---

# Channel Factories

## Overview

A **channel factory** is a non-custodial, multi participatory system that contains channels. Channel factories allow users to open unlimited channels within their group.

## Details

### Overview

Channel Factories are payment channels that can be used to create more payment channels.

In a regular payment channel, you always have a transaction signed by all participating parties that's ready to commit the current channel balances to the block chain. For example, in a channel between Alice and Bob, this transaction might have two outputs, one paying Alice 0.25 BTC and one paying Bob 0.75 BTC. If this example transaction were broadcast, it would close the payment channel between Alice and Bob.

However, it's possible to format the ready-to-commit transaction as a transaction that not only closes the existing payment channel but which also opens a new payment channel. In that case, the same security that allows the initial payment channel to have zero-conf security also extends its security to the second payment channel.

The key feature of a regular payment channel is the ability to securely update the state \(balance\) of the channel many times without creating extra on-chain transactions, so the key feature of a Channel Factory is the ability to securely create and destroy new payment channels without creating extra on-chain transactions.

The resulting network provides the third layer, where regular transfers of currency are executed. Similar to regular micropayment channels, multi-party channels can be implemented with either timelocks or punishments for dishonest parties. 

The regular micropayment channels of the third layer can be punishment based or timelock based independent from the implementation of the multi-party channels of the second layer

### Settlement

When the involved parties cooperatively decide to close a channel factory, they can create and broadcast a settlement transaction, which pays out the current stake of each party directly from the shared account and without a timelock, replacing the allocation, and removing the locked funds.

### Moving Funds

A channel factory can be used to rebalance channels which have become one sided. A new allocation is set up, which replaces every channel with a balanced new one while keeping the total stake of each party the same. As an advantage, funds can also be moved between channels, new channels can be created or old ones removed, changing the network connectivity without contacting the blockchain.

## Resources

[What are Channel Factories and how do they work?](https://bitcoin.stackexchange.com/questions/67158/what-are-channel-factories-and-how-do-they-work)

## References

\[1\] [https://www.tik.ee.ethz.ch/file/a20a865ce40d40c8f942cf206a7cba96/Scalable\_Funding\_Of\_Blockchain\_Micropayment\_Networks%20\(1\).pdf](https://www.tik.ee.ethz.ch/file/a20a865ce40d40c8f942cf206a7cba96/Scalable_Funding_Of_Blockchain_Micropayment_Networks%20%281%29.pdf)



