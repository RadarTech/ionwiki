---
latest-revision: '2019-01-27T00:00:00.000Z'
original-author: Ryan Shea (ryan-shea)
created: '2019-01-01T00:00:00.000Z'
status: Accepted
title: Eltoo
contributors: Ryan Shea (ryan-shea); Gareth James (gjradar)
type: article
description: ''
discussions-to: GitHub URL
category: lightning-rnd
---

# Eltoo

## Overview

**Eltoo** is a Layer 2 Protocol originally outlined by Christian Decker, Rusty Russell, and Olaoluwa Osuntokun. It proposes a new update mechanism for Layer 2 protocols, enhancing off-chain negotiations. Among other concepts, it introduces state numbers, an enforceable variant of sequence numbers.

## Details

### Mechanism

In eltoo every state is represented as a set of two transactions: an update transaction that spends the contract’s output and creates a new output, and a settlement transaction that spends the newly created update output and splits the funds according to the agreed-upon distribution. The outputs have a script that allows a new update transaction to be attached immediately or else a settlement transaction to be attached after a configurable timeout. Should the participants agree on an update before the timeout expires, they will create a new update transaction, spending the previous output and doublespending the corresponding settlement, effectively invalidating it.

The repeated invalidation of prior state to agree on a new state builds a long chain of update transactions that will eventually be terminated by the latest settlement transaction. However, this has a major disadvantage: should we want to settle, we would have to replay the entire chain of updates on the blockchain. At that point we could have simply performed the entire protocol on-chain. The key insight in eltoo is that we can skip intermediate updates, basically connecting the final update transaction to the contract creation. In order to enable this short-circuiting of updates, we propose a new `SIGHASH` flag,`SIGHASH_NOINPUT`, which allows a transaction input to be bound to any transaction output with a matching script. Since all output scripts of prior update-transaction outputs match later input scripts, we can bind a later update to any prior update, allowing us to skip any number of intermediate updates. The paper contains the full construction of the protocol, including the details on how the scripts are built.

### Roadblocks

Before eltoo can be implemented, a minor change to Bitcoin is needed: the introduction of the `SIGHASH_NOINPUT` flag for signatures. This was first discussed in the context of watchtowers to help secure Lightning channels, but was not formally proposed. A formal proposal may now be found in the eltoo paper.

## Resources

### Key People

* Christian Decker
* Rusty Russell
* Olaoluwa Osuntokun

## References

\[1\] [https://blockstream.com/2018/04/30/eltoo-next-lightning/](https://blockstream.com/2018/04/30/eltoo-next-lightning/)

\[2\] [https://blockstream.com/eltoo.pdf](https://blockstream.com/eltoo.pdf)

\[3\] [https://www.coindesk.com/new-twist-lightning-tech-coming-soon-bitcoin](https://www.coindesk.com/new-twist-lightning-tech-coming-soon-bitcoin)

