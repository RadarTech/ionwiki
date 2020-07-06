---
latest-revision: '2019-01-27T00:00:00.000Z'
original-author: Ryan Shea (ryan-shea)
created: '2019-01-01T00:00:00.000Z'
status: Accepted
title: Channel Closing
contributors: Ryan Shea (ryan-shea); Gareth James (gjradar)
type: article
description: ''
discussions-to: GitHub URL
category: lightning-channels
---

# Closing A Channel

Payment channels on the Lightning Network have an unlimited lifespan, and will remain open forever until a participant in the channel initiates a **closing transaction**.

Closing transactions come in different forms and may involve one or both parties to the channel. Closing transactions are broadcast to the blockchain, so the user must pay transaction fees and must wait for the transaction to be mined into the chain. A channel can no longer be used to route payments from the moment that the close is initiated.

## Types of Closing Transactions

Both parties are able to send as many Lightning payments to their counterparty as their funds in the Lightning channel allow, knowing that in the event of a disagreement they can settle their agreed-upon channel balance to the blockchain. In the vast majority of cases, there will be no disagreement and the entire lifecycle of a channel will consist of a single channel-funding transaction and a single cooperative close.

Just in case there is a disagreement, every time a payment traverses the channel, participants create transactions committing to the current channel state and exchange secrets that revoke their previous commitments. The latest commitment and the secret keys that revoke previous commitments are kept by both parties just in case the other part is non-cooperative.

During the normal operation of a Lightning channel with two non-malicious parties who cooperatively close a channel, no old commitment transactions or revocation keys are ever used, much like how a contract is rarely enforced in the courts. Because both parties understand exactly how the contracts that bind them in a channel will be enforced, both parties know that they cannot get away with fraud and they are incentivized to act honestly.

### Cooperative Close

In a cooperative close \(aka mutual close\), both channel participants agree to close the channel and settle the final state of the channel onto the blockchain. Both participants provide a digital signature that authorizes this cooperative settlement transaction.

### Force Close

If only one participant is online or if the participants disagree on the state of the channel, one participant can perform a force close \(aka unilateral close\) of the channel without the cooperation of the other participant.

A force close is performed by broadcasting a "commitment transaction", a transaction that commits to a previous channel state that the channel participants have agreed upon. A force close is legitimate if the commitment transaction that is broadcast is the newest one that the channel participants have agreed upon; if the participant has broadcast a commitment transaction that has been revoked and superseded by a newer commitment, the force close is fraudulent can can be challenged by the other party when they come back online.

The practical result of a force close is that both parties will receive their portion of the money in the channel, but the party that initiates the force close must wait anywhere from hours to weeks—the exact delay is negotiated by the nodes beforehand—to receive their funds. This delay, referred to as `to_self_delay` in the LND documentation, provides the offline node a window of opportunity to come back online and verify that the force-close was legitimate. If the force-close was fraudulent, the peer can challenge it with a penalty transaction.

Fraudulent force close transactions can also be detected and responded to by [Watchtower services](../research/watchtowers.md).

### Fraudulent Force Close

An invalid unilateral close of a channel, caused by broadcasting a commitment transaction that does not represent the newest channel state agreed upon by the participants.

If the invalid close is not detected by the other peer within the `to_self_delay` window, the malicious peer will get away with the fraudulent close and may steal some of their peer's money in the channel

If the invalid close is detected by the other peer or by a [Watchtower service](../research/watchtowers.md), the other peer can use proof that the commitment was revoked, called a commitment revocation secret key, to create and broadcast a penalty transaction that punishes the peer who attempted a fraudulent force close.

### Penalty Transaction

A penalty transaction punishes a malicious node for attempting a fraudulent force close. The penalty transaction transfers the malicious node's portion of the funds in the channel to the node that they were attempting to defraud.

## References

1. [https://github.com/lightningnetwork/lightning-rfc/blob/master/00-introduction.md](https://github.com/lightningnetwork/lightning-rfc/blob/master/00-introduction.md) BOLT \#0, Introduction and Index

