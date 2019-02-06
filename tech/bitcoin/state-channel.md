---
latest-revision: '2019-01-27T00:00:00.000Z'
original-author: Ryan Shea (ryan-shea)
created: '2019-01-01T00:00:00.000Z'
status: Accepted
title: State Channel
contributors: Ryan Shea (ryan-shea)
type: article
description: ''
discussions-to: GitHub URL
category: bitcoin-basics
---

# State Channels

## Overview

State channels are a technique for allowing fast and cheap off-chain payments that retain the security of the underyling blockchain. They allow transacting users instant finality and minimal blockchain transaction fees.

## Details

### Overview

State channels enhance blockchain performance by taking state-modifying operations off of a blockchain and instead executing them directly between defined sets of participants.

[Payment channels ](../lightning/payment-channel.md)were the first type of state channel to be described, using off-chain interactions to modify ownership of locked Bitcoin, thereby allowing users to make “off-chain payments” to each other. The term “state channels” generalizes this approach beyond payments, encompassing all types of blockchain state modification which operate within a security paradigm comparable to that of the payment channel.

State channels let parties securely modify locked portions of blockchain state called state deposits. These deposits are typically held in multisignature wallets, where the participants to the state channel are the signers to the multisig.

Participants update the state channel by exchanging off-chain messages. These messages describe an update to the state deposit, for instance, a payment that changes the balance between two parties in a payment channel, or a player’s next move in a chess state channel. Participants can continue exchanging these off-chain updates without incurring any on-chain fees until they choose to close the channel, at which point the most recent state update is sent to the on-chain multisig as a single transaction, and the state deposit is withdrawn to the parties in accordance with the final state.

Participants store copies of these off-chain state updates. Because every message is crypto-graphically signed and the multisig contains code to verify these signatures and interpret these messages, participants preserve the ability to realize the most recent state update on-chain at anytime. Parties are prevented from submitting old messages by their counterparties: if Alice submits an old state, Bob is given an opportunity to “rebut” it by broadcasting a more recent state. This design allows participants to treat updates within a state channel as “final”, despite taking place entirely off-chain.

### Payment Channels vs State Channels

Payment channels are a subset of state channels. Requiring radically simpler dispute resolution methods than state channels, payment channels were the first implementation of state channels and have less complex functionality.

## Resources

[Counterfactual: Generalized State Channels](https://l4.ventures/papers/statechannels.pdf)

[LearnChannels](https://docs.learnchannels.org/)

## References

\[1\] [https://l4.ventures/papers/statechannels.pdf](https://l4.ventures/papers/statechannels.pdf)

