---
latest-revision: '1999-01-29T00:00:00.000Z'
original-author: >-
  Isaac Newton (@appleman) < List of Original Authors' Real Name and Github;
  email address optional >
created: 1999-01-01 < ISO 8601 (yyyy-mm-dd) format >
status: >-
  < Draft | Under Review | Deferred | Proofing | Rejected | Withdrawn | Accepted
  | Superseded>
title: Scriptless Scripts (Schnorr)
contributors: >-
  Leonardo Da Vinci (@leodavinci); Galileo Galilei (@ggal) < List of
  contributors -- Real Name + Github; email optional >
type: null
description: Description guidelines
discussions-to: (GitHub PR)
category: null
---

# Scriptless Scripts \(Schnorr\)

## Overview

Scriptless Scripts are a way to execute smart contracts off-chain using Schnorr Signatures. Scriptless scripts are a way to encode smart contracts into digital signatures -- effectively accomplishing smart contract features without any scripts. 

By removing hash preimages, removing Script tricks that people use to get atomicity between chains and transactions, and moving those onto signatures, contracts are accomplished in something smaller, more efficient, more scalable, more private, an inherently interoperable.

A Schnorr signature is a digital signature produced by the Schnorr signature algorithm that was described by Claus Schnorr. It is a digital signature scheme known for its simplicity, among the first whose security is based on the intractability of certain discrete logarithm problems. It is efficient and generates short signatures.

## Details

### Background

_Smart contracts:_ Currently, smart contracts are used to process Bitcoin transactions. These include standard transactions that only require a single signature as well as more complex transactions such as time-locked or multi-signature transactions.

_Script:_ These smart contracts are currently processed on-chain using [Bitcoin Script](https://en.bitcoin.it/wiki/Script).

_On-chain vs. off-chain_: Bitcoin smart contracts are currently processed “on-chain” which has negative effects on user transaction costs, network participation resource requirements, and privacy \(all of which are discussed in more detail below\). __The potential power of Scriptless Scripts is that they address these issues by using Schnorr signatures to move smart contract processing off-chain.

### Benefits

The primary benefits of Scriptless scripts are functionality, privacy, and efficiency.

In terms of **functionality**, Scriptless Scripts could increase the range and complexity of smart contracts that are possible with Bitcoin today. Currently, Bitcoin smart contracts are executed within Bitcoin Script which is limited in the types of contracts that can be executed. This limitation stems from the number of “opcodes” that have been enabled by the network \(remember, anything done at the network level requires network-wide consensus, which is hard to achieve\).

Scriptless scripts move the specification and execution of these smart contracts from a _network-wide decision_ — as is currently the case for smart contracts that execute within Bitcoin Script — to a decision that _only involves the participants of the smart contract_. As a result, the range of smart contracts that a Bitcoin user could potentially deploy should increase drastically.

Moving the specification and execution of smart contracts from on-chain to off-chain is also what drives the **privacy** benefits of Scriptless Scripts. When the smart contracts themselves are on-chain, many details are divulged to the entire network including the number and addresses of participants as well as the amount of capital involved — that’s not ideal as it’s very far afield from typical user expectations regarding contracts and money transfers.

Instead, Scriptless Scripts use Schnorr signatures to move these contracts off-chain. This means that instead of the entire network verifying the actual terms of a contract, the network and its participants simply verify that there is a valid outcome — That is, that the parties to the contract agree that the terms have been satisfied and the resulting transaction is valid.

Said differently, the network doesn’t actually need to know the terms of the contract between Alice and Bob, the network just needs to know that Alice and Bob agree that the terms of their contract have been satisfied and that the resulting transaction is valid — that’s what Scriptless Scripts accomplish.

Scriptless Scripts also offer a significant **efficiency** advantage: By moving smart contracts off-chain, Scriptless Scripts minimize the amount of data that needs to be verified and stored on the network level. That means less overhead for network participants \(e.g. full nodes\) and lower transaction fees for users \(a win-win\).

Ultimately, it’s helpful to think of these innovations in terms of puts and takes and evaluating the tradeoff that’s proposed. Typically, improvements in functionality and privacy come at the expense of efficiency. However, Scriptless Scripts \(via Schnorr signatures\) could potentially improve functionality and privacy without compromising at all on efficiency.

## Resources

[Scriptless Scripts Slides](https://download.wpsoftware.net/bitcoin/wizardry/mw-slides/2017-05-milan-meetup/slides.pdf)

### See also

[Scriptless Scripts Explained](http://diyhpl.us/wiki/transcripts/layer2-summit/2018/scriptless-scripts/)

## References

\[1\] [https://medium.com/blockchain-capital-blog/crypto-innovation-spotlight-2-scriptless-scripts-306c4eb6b3a8](https://medium.com/blockchain-capital-blog/crypto-innovation-spotlight-2-scriptless-scripts-306c4eb6b3a8)

\[2\] [https://medium.com/blockchain-capital-blog/crypto-innovation-spotlight-schnorr-signatures-a83748f16a4](https://medium.com/blockchain-capital-blog/crypto-innovation-spotlight-schnorr-signatures-a83748f16a4)

\[3\] [https://bitcoinmagazine.com/articles/scriptless-scripts-how-bitcoin-can-support-smart-contracts-without-smart-contracts/](https://bitcoinmagazine.com/articles/scriptless-scripts-how-bitcoin-can-support-smart-contracts-without-smart-contracts/)

\[4\] [https://joinmarket.me/blog/blog/flipping-the-scriptless-script-on-schnorr/](https://joinmarket.me/blog/blog/flipping-the-scriptless-script-on-schnorr/)

