---
category: bitcoin-basics
contributors: "Ryan Shea (ryan-shea); Gareth James (gjradar)"
created: 2019-01-01
description: ""
discussions-to: "GitHub URL"
latest-revision: 2019-01-27
original-author: "Ryan Shea (ryan-shea)"
status: "Accepted"
title: "Fees"
type: article
---

# Fees

## Overview

The Lightning Network utilizes a number of transactions types that have different potential fees. One of the key publicized advantages of the Lightning Network is the near-zero fees to send payments within the network.

Fee types include:

* Transactions between two participants in a single channel, which never incur fees.
* Transactions routed between participants in the network via multiple channels, which incur routing fees from intermediate nodes. These fees could be set at zero.
* On-chain transactions, such as those to open or close a channel, which incur Bitcoin network fees.

## Details

### Single Channel Transactions

Transactions between parties in an established channel never incur fees. As transactions occur between the two parties, the channel balance is updated without the need for fee allocation.

### Routed Transactions

Fee calculation for payments routed through other nodes is determined by node operators. Node operators can set any fee. As a multi-hop payment is calculated, fees can be taken into account.

The routing algorithm used to find the various hops towards a final destination payment will also impact your resulting fee. Due to channel exhaustion \(an imbalance in a channel\), the routing algorithm will look for paths where transacting users get paid because the transaction would be rebalancing channels along the way. In some cases, fees on Lightning may be negative.

### On-Chain Transactions

Transactions for opening and closing channels are settled on the Bitcoin blockchain, and thus, incur fees that are based on the Bitcoin network capacity. Fees are included with your on-chain transaction and are required in order to have your transaction processed by a miner and confirmed by the Bitcoin network.

There is a limited amount of space available for transactions in a block, so in order to get a transaction processed quickly, users will have to outbid other transaction requests.

### Fee Payment

Base commitment transaction fees are extracted from the funder's amount. If that amount is insufficient, the whole amount of the funder's output is used.

After the fee amount is subtracted from the to-funder output, that output may be below the dust limit, and thus will also contribute to fees.

## Resources

[Historical Bitcoin Fees](https://bitcoinfees.info/)

## References

\[1\] [https://github.com/lightningnetwork/lightning-rfc/blob/064d6feed036de192f71cf6854e00f33361b6090/03-transactions.md](https://github.com/lightningnetwork/lightning-rfc/blob/064d6feed036de192f71cf6854e00f33361b6090/03-transactions.md)
