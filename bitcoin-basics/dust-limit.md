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

**Dust limits** are thresholds encoded in the blockchain that denote the minimum amount of currency used for a transaction to be processed on the chain. Amounts less than the minimum are considered “dust” and are unusable until more tokens are added to the wallet.

**Dust** refers to tiny UTXOs \(unspent transaction outputs\) on the Bitcoin blockchain. The Bitcoin Core implementation defines dust as a UTXO that would require a fee greater than 1/3rd of its value to send. 

## Details

The blockchain uses significantly more computing space and processing time than traditional data security protocols. In the early years of the blockchain, individuals or groups could spam the chain with enormous numbers of microtransactions for little to no cost, effectively clogging the block chain and denying the service to anyone trying to exchange tokens. An example of this was the 2015 Flood Attack which used a DDoS style attack to interrupt the functionality of the chain. Dust limits fixed this by imposing minimum amounts for transactions.  


The dust limit created circulation problems for token users. As token usage increases, dust also increases which takes tokens out of circulation. More dust means less tokens available for trading. Efforts to decrease the dust limit in order to eliminate excess dust have occured, notably BTC lowering its dust limit from 5460 satoshi to 546. Other proposed solutions involve ways to combine tiny wallet sums into a larger transaction, but this solution advocates reusing token addresses which creates financial privacy concerns.  


Many critics of the dust limit point to the untapped capital in the form of dust. However, there is a general consensus that removing the dust limit is not viable. Without a dust limit, transactions as small as one satoshi would be possible, but the potential for spam and denial of service has prevented removal of dust limits and different strategies are being explored to fix the micro-transaction problem while maintain efficiency.

### Application to Lightning Network

Lightning is an off-chain platform and therefore is less vulnerable to the DDoS attacks that the early blockchain faced. Microtransactions significantly smaller than the current dust limits are allowed. By circumventing the dust limit in an off chain network, dust can more readily be removed and circulation can remain efficient.

Once a channel is opened an unlimited number of trades can occur of miniscule size before being reported to the main chain. This means that trades as small as one satoshi, if using BTC, are possible through the Lightning Network.

## Resources



### See also

## References

\[1\] [https://github.com/bitcoin/bitcoin/blob/v0.10.0rc3/src/primitives/transaction.h\#L137](https://github.com/bitcoin/bitcoin/blob/v0.10.0rc3/src/primitives/transaction.h#L137)

\[2\] [https://www.coindesk.com/bitcoin-dust-tell-get-rid](https://www.coindesk.com/bitcoin-dust-tell-get-rid)

\[3\] [https://github.com/lightningnetwork/lnd/issues/48](https://github.com/lightningnetwork/lnd/issues/48) 

\[4\] 

