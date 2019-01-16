---
latest-revision: '1999-01-29T00:00:00.000Z'
original-author: >-
  Isaac Newton (@appleman) < List of Original Authors' Real Name and Github;
  email address optional >
created: 1999-01-01 < ISO 8601 (yyyy-mm-dd) format >
status: >-
  < Draft | Under Review | Deferred | Proofing | Rejected | Withdrawn | Accepted
  | Superseded>
title: Eltoo
contributors: >-
  Leonardo Da Vinci (@leodavinci); Galileo Galilei (@ggal) < List of
  contributors -- Real Name + Github; email optional >
type: null
description: Description guidelines
discussions-to: (GitHub PR)
category: null
---

# Eltoo

## Overview

_**Eltoo** is a Layer 2 Protocol originally outlined by Christian Decker, Rusty Russell, and Olaoluwa Osuntokun. It proposes a new update mechanism for layer 2 protocols, enhancing off-chain negotiations. Among other concepts, it introduces state numbers, an enforceable variant of sequence numbers._ 

## Details

### Functionality

_We can imagine off-chain negotiation as a contractual agreement between a number of parties and settlement as presenting the case to a court that will decide the final state — the court in this case being the blockchain. Since all updates happen off-chain, we need a way for the on-chain court to hear all sides of the argument before making a final judgement. In the case of a participant initiating settlement of the contract, we need a mechanism that defers final settlement, to give the counterparty a chance to provide a more recent state. The court must continue to wait for new state, until eventually it decides to settle the last one it heard. Surprisingly most of the requirements to create this blockchain tailor-made for layer 2 protocols are already fulfilled by the Bitcoin blockchain._

### _Mechanism_

_We can imagine off-chain negotiation as a contractual agreement between a number of parties and settlement as presenting the case to a court that will decide the final state — the court in this case being the blockchain. Since all updates happen off-chain, we need a way for the on-chain court to hear all sides of the argument before making a final judgement. In the case of a participant initiating settlement of the contract, we need a mechanism that defers final settlement, to give the counterparty a chance to provide a more recent state. The court must continue to wait for new state, until eventually it decides to settle the last one it heard. Surprisingly most of the requirements to create this blockchain tailor-made for layer 2 protocols are already fulfilled by the Bitcoin blockchain._

_\[img\]_

_In eltoo every state is represented as a set of two transactions: an update transaction that spends the contract’s output and creates a new output, and a settlement transaction that spends the newly created update output and splits the funds according to the agreed-upon distribution. The outputs have a script that allows a new update transaction to be attached immediately or else a settlement transaction to be attached after a configurable timeout. Should the participants agree on an update before the timeout expires, they will create a new update transaction, spending the previous output and doublespending the corresponding settlement, effectively invalidating it._

_The repeated invalidation of prior state to agree on a new state builds a long chain of update transactions that will eventually be terminated by the latest settlement transaction. However, this has a major disadvantage: should we want to settle, we would have to replay the entire chain of updates on the blockchain. At that point we could have simply performed the entire protocol on-chain. The key insight in eltoo is that we can skip intermediate updates, basically connecting the final update transaction to the contract creation. In order to enable this short-circuiting of updates, we propose a new `SIGHASH` flag,`SIGHASH_NOINPUT`, which allows a transaction input to be bound to any transaction output with a matching script. Since all output scripts of prior update-transaction outputs match later input scripts, we can bind a later update to any prior update, allowing us to skip any number of intermediate updates. The paper contains the full construction of the protocol, including the details on how the scripts are built._  


\_\_

### _Roadblocks_

_Before we can implement eltoo, we need a minor change to Bitcoin: the introduction of the `SIGHASH_NOINPUT` flag for signatures. This was first discussed a few months ago in the context of watchtowers to help secure Lightning channels, but was not formally proposed. A formal proposal may now be found in the eltoo paper._

_We invite the community to consider our proposal and to participate in its discussion. We hope to arrive at a consensus for the usage of `SIGHASH_NOINPUT`, so that it can be accepted and included in a future soft fork of Bitcoin Script. Doing so will put us on the road to a more reliable and simpler Lightning Network, incorporating a new update mechanism that can also be used for many other applications._  


## Resources

### Key People

* Christian Decker
* Rusty Russell
* Olaoluwa Osuntokun

### See also

## References

\[1\] [https://blockstream.com/2018/04/30/eltoo-next-lightning/](https://blockstream.com/2018/04/30/eltoo-next-lightning/)

\[2\] [https://blockstream.com/eltoo.pdf](https://blockstream.com/eltoo.pdf)

