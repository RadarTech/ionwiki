---
latest-revision: '2019-01-27T00:00:00.000Z'
original-author: Ryan Shea (ryan-shea)
created: '2019-01-01T00:00:00.000Z'
status: Accepted
title: What is the Lightning Network?
contributors: Ryan Shea (ryan-shea); Gareth James (gjradar)
type: article
description: ''
discussions-to: GitHub URL
category: lightning-basics
---

# What is the Lightning Network?

## Overview

The **Lightning Network** is an off-chain, routed [payment channel](payment-channel.md) network built on top of the Bitcoin blockchain. The network consists of [nodes](node.md) connected by peer-to-peer channels. This allows low cost, near-instant payments to be trustlessly routed across the network via connected nodes.

As a "Layer 2" payment protocol, transactions on the Lightning Network are underpinned by the security of the Bitcoin blockchain. Participants must complete on-chain transactions to open and close channels, but can make near-instant, free transactions within an open channel. As a result, the Lightning Network avoids the linear scalability problems faced by traditional proof-of-work blockchains.

## Details

The Lightning Network is a protocol that enables high­-volume, low ­latency digital micropayments without the need for trusted intermediaries. Using novel Bitcoin multi signature transactions and scripts, Lightning participants do not give unilateral custody of funds to a third party, greatly reducing transaction costs and counterparty risk. While previous micropayment solutions involve holding funds with trusted custodians, the Lightning Network achieves instant micropayments via smart contracts. Through a network of multi signature transactions, any participant on the Lightning Network is able to pay anyone else within the ecosystem of participants.

Lightning's fundamental technology is a local two ­party consensus, known as a [payment channel](payment-channel.md). Two parties send an initial amount of Bitcoin into a multi signature transaction with a local consensus on the current balance allocated between the two participants. Updates to the allocation of the current balance can be made only with the cooperation of both parties, using a new transaction which spends from the funds allocated to the multi signature transaction to each party.

### On-Chain Transactions

One on­ blockchain transaction is made to deposit the funds into a multi signature output. Before this transaction is made, a refund transaction is created, which returns the original deposit to both parties.

After the transaction is broadcast on­ chain, the payment channel is open and ready for transfers. When one wishes to update the balance with a new balance, both parties must consent to the new balance and generate a new spend from the transaction. In effect, they have created numerous "double spends" from an on­ blockchain transaction, but have elected not to broadcast the spend until either party wants to redeem their funds on­ chain. These multi signature transactions are real Bitcoin transactions. Either party may broadcast the most recent transaction, the current local consensus state, to the global blockchain at any time to redeem their current balance of funds. As either party may redeem funds from this channel at any time unilaterally, without requiring any cooperation from anyone else, the most recent transaction is effectively their current balance in the channel. They may continue updating the channel with updated states without interacting with the global blockchain until they wish to close out the channel. In other words, updating the local consensus state is actionable on the global consensus state.

Updating the local transaction state is enforceable via mutual revocation of old states. When balances are updated in a channel, the prior state is invalidated via a penalty system. Only the most recent balance state should be broadcast, which spends from the on­chain multi signature output. If either party incorrectly broadcasts an old transaction state, the counterparty may take all the funds in the channel as a penalty. As a result, both parties have a direct economic incentive to only broadcast the most recent transaction state. This is achieved by having an on­chain dispute mediation window before the funds can be dispersed. The global consensus state, the Bitcoin blockchain, becomes a dispute resolution system for off­chain local consensus states. Similar to how the vast majority of legal contracts are adhered to without going to court, the balances in the channel are agreed upon in the off­chain local consensus state, and have the option of on­chain programmatic enforcement.

The innovation of the Lightning Network is the use of time­locked transactions and cryptographic nonces to allow many two­party payment channels to form a connected network where payments can be sent over many channels without trusting the intermediate nodes. The topology is similar to IP networks like the internet: packets are routed over many physical links, and the communicating end nodes don't worry about the route as long as data gets to the destination. This works via a decrementing time­lock that permits every intermediate node along the routing path to accept funds only if they forward it along to the next participant, using disclosure of preimages of cryptographic hashes. In the Lightning Network, nodes are not able to seize funds traveling through their channels even if they fail to forward payments or refuse to perform any actions. A node operates without custody of third party funds, which is enforced by a time­limited cryptographic script. This is all achieved off­chain assuming cooperative parties, and enforced on­chain when one's counterparty is not cooperative.

Through this network of interconnected payment channels, Lightning provides a scalable, decentralized micropayments solution on top of the Bitcoin blockchain.

### Features

**Rapid payments:** payments within an established channel can be made almost as fast as data can travel over the Internet between the two peers.

**No third-party trust:** the two peers in a channel pay each other directly using regular Bitcoin transactions \(of which only one is broadcast\) so at no point does any third party control their funds.

**Reduced blockchain load:** only channel open transactions, channel close transactions, and \(hopefully infrequent\) anti-fraud respends need to be committed to the blockchain, allowing all other payments within Lightning Network channels to remain uncommitted. This allows Lightning Network users to make frequent payments secured by Bitcoin without placing excessive load on full nodes which must process every transaction on the blockchain.

**Channels can stay open indefinitely:** as long as the two parties in the channel continue to cooperate with each other, the channel can stay open indefinitely -- there is no mandatory timeout period. This can further reduce the load on the blockchain as well as allow the fees for opening and closing the channel to be amortized over a longer period of time.

**Rapid cooperative closes:** if both parties cooperate, a channel can be closed immediately \(with the parties likely wanting to wait for one or more confirmations to ensure the channel closed in the correct state\). Non-cooperative closes \(such as when one party disappears\) are also possible, but take longer.

**Outsourceable enforcement:** if one party closes a channel in an old state in an attempt to steal money, the other party has to act within a defined period of time to block the attempted theft. This function can be outsourced to a third-party without giving them control over any funds, allowing wallets to safely go offline for periods longer than the defined period.

**Onion-style routing:** payment routing information can be encrypted in a nested fashion so that intermediary nodes only know who they received a routable payment from and who to send it to next, preventing those intermediary nodes from knowing who the originator or destination is \(provided the intermediaries didn't compare records\).

**Multisignature capable:** each party can require that their payments into the channel be signed by multiple keys, giving them access to additional security techniques.

**Securely cross blockchains:** payments can be routed across more than one blockchain \(including altcoins and sidechains\) as long as all the chains support the same hash function to use for the hash lock, as well as the ability the ability to create time locks.

**Sub-satoshi payments:** payments can be made conditional upon the outcome of a random event, allowing probabilistic payments. For example, Alice can pay Bob 0.1 satoshi by creating a 1-satoshi payment with 10-to-1 odds so that 90% of the time she does this she pays him 0 satoshis and 10% of the time she pays him 1 satoshi for an average payment of 0.1 satoshis.

**Single-funded channels:** when Alice needs to send a payment to Bob and doesn't currently have a way to pay him through the Lightning Network \(whether because she can't reach him or because she doesn't have enough money in an existing channel\), she can make a regular on-chain payment that establishes a channel without Bob needing to add any of his funds to the channel. Alice only uses 12 bytes more than she would for a non-Lightning direct payment and Bob would only need about 25 more segwit virtual bytes to close the channel than he would had he received a non-Lightning direct payment.

## Resources

### Key People

* [Joseph Poon](https://twitter.com/jcp)
* [Thaddeus Dryja](https://twitter.com/tdryja)

### See also

* [Lightning Network Documents](https://lightning.network/docs/)
* [Lightning Network Whitepaper](https://lightning.network/lightning-network-paper.pdf)

## References

\[1\] [Lightning Network Technical Summary](https://lightning.network/lightning-network-technical-summary.pdf)

\[2\] [https://dev.lightning.community/overview/](https://dev.lightning.community/overview/)

\[3\] \('Rapid Payments' through to 'Single-funded Channels' sourced from [https://en.bitcoin.it/wiki/Lightning\_Network](https://en.bitcoin.it/wiki/Lightning_Network) under CC BY 3.0\)

