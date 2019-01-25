---
latest-revision: '1999-01-29T00:00:00.000Z'
original-author: >-
  Isaac Newton (@appleman) < List of Original Authors' Real Name and Github;
  email address optional >
created: 1999-01-01 < ISO 8601 (yyyy-mm-dd) format >
status: >-
  < Draft | Under Review | Deferred | Proofing | Rejected | Withdrawn | Accepted
  | Superseded>
title: Dust limit
contributors: >-
  Leonardo Da Vinci (@leodavinci); Galileo Galilei (@ggal) < List of
  contributors -- Real Name + Github; email optional >
type: null
description: Description guidelines
discussions-to: (GitHub PR)
category: null
---

# Dust

## Overview

**Dust limits** are thresholds encoded in the Bitcoin blockchain that denote the minimum amount of currency used for a transaction to be processed on the chain. Amounts less than the minimum are considered “dust” and are unusable until more tokens are added to the wallet.

**Dust** refers to tiny UTXOs \(unspent transaction outputs\) on the Bitcoin blockchain. The Bitcoin Core implementation defines dust as a UTXO that would require a fee greater than 1/3rd of its value to send. 

## Details

In the early years of the blockchain, users could spam the chain with enormous numbers of microtransactions for little to no cost, effectively clogging transaction processing and denying valid transaction processing. An example of this was the 2015 Flood Attack which used a DDoS style attack to interrupt transaction confirmation and processing. Dust limits fixed this by imposing minimum amounts for transactions.  


The dust limit created circulation problems for token users. As token usage increases, dust also increases which takes tokens out of circulation. More dust means less tokens available for trading. Efforts to decrease the dust limit in order to eliminate excess dust have occurred, notably BTC lowering its dust limit from 5460 satoshis to 546. Other proposed solutions involve ways to combine tiny wallet sums into a larger transaction, but this solution advocates reusing token addresses which creates financial privacy concerns.  


Many critics of the dust limit point to the untapped capital in the form of dust. However, there is a general consensus that removing the dust limit is not viable. Without a dust limit, transactions as small as one satoshi would be possible, but the potential for transaction clogging has prevented the removal of dust limits. Different strategies are being explored to fix the micro-transaction problem while maintaining efficiency.

### Application to Lightning Network

Lightning, circumventing the scaling problems faced by the Bitcoin protocol, enables microtransaction processing and effectively removes the dust limit. By circumventing the dust limit, dust can more readily be removed and circulation can remain efficient.

Once a channel is opened, an unlimited number of transactions can occur of minuscule size before needing to be settled on-chain. Trades as small as one satoshi \(if using BTC\) are possible through the Lightning Network.

## Resources

[What is meant by Bitcoin Dust?](https://bitcoin.stackexchange.com/questions/10986/what-is-meant-by-bitcoin-dust)

## References

\[1\] [https://github.com/bitcoin/bitcoin/blob/v0.10.0rc3/src/primitives/transaction.h\#L137](https://github.com/bitcoin/bitcoin/blob/v0.10.0rc3/src/primitives/transaction.h#L137)

\[2\] [https://www.coindesk.com/bitcoin-dust-tell-get-rid](https://www.coindesk.com/bitcoin-dust-tell-get-rid)

\[3\] [https://github.com/lightningnetwork/lnd/issues/48](https://github.com/lightningnetwork/lnd/issues/48) 

