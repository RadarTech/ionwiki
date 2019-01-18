---
latest-revision: '1999-01-29T00:00:00.000Z'
original-author: >-
  Isaac Newton (@appleman) < List of Original Authors' Real Name and Github;
  email address optional >
created: 1999-01-01 < ISO 8601 (yyyy-mm-dd) format >
status: >-
  < Draft | Under Review | Deferred | Proofing | Rejected | Withdrawn | Accepted
  | Superseded>
title: Fees
contributors: >-
  Leonardo Da Vinci (@leodavinci); Galileo Galilei (@ggal) < List of
  contributors -- Real Name + Github; email optional >
type: null
description: Description guidelines
discussions-to: (GitHub PR)
category: null
---

# Fees

## Overview

The Lightning Network utilizes a number of transactions types that have different potential fees. One of the key publicized advantages of the Lightning Network is the near-zero fees to send payments within the network. 

These include:

* Transactions between two participants in a single channel, which never incur fees.
* Transactions routed between participants in the network via multiple channels, which incur routing fees from intermediate nodes. These fees could be set at zero.
* On-chain transactions, such as those to open or close a channel, which incur Bitcoin network fees.

## Details

### Single Channel Transactions

Transactions between parties in an established channel never incur fees. 

### Routed Transactions

Fee calculation for payments routed through other nodes is determined by node operators.

Fees are determined by the node operators. It's a free market, you can set whatever fee you want. Of course there's lots of competition, so if you want people to route payments through you, you should set a low or no fee.

I'd simply like to expand on Andrew's answer and mention that the routing algorithm used to find the various hops towards your final destination payment will also impact your resulting fee.

The idea is that channels sometimes become almost exhausted - where most of the money is pushed towards one direction. This is bad for people because it would mean that their channels cannot be reused; you'd have to open a new channel for new payments, hence on-chain transactions.

If a channel is almost exhausted, the person of the channel with less money \(exhausted towards her\) will want payments routed towards her to allow her channel to be full again so she can make more payments on that same channel without reopening a new one.

She will actually want to pay if someone chooses her channel to route their payments -- hence sometimes you'll have negative fees.

This means that a routing algorithm will actually look for paths where you actually get paid \(negative fees\) because you'd be rebalancing some channels along the way.

### On-Chain Transactions

Transactions for opening and closing channels are settled on the Bitcoin blockchain, and thus, incur fees that are based on the bitcoin network. Fees are included with your on-chain transaction in order to have your transaction processed by a miner and confirmed by the Bitcoin network. 

There is a limited amount of space available for transactions in a block, so in order to get a transaction processed quickly, users will have to outbid other transaction requests.

_**Requirements**_

_The fee for an HTLC-timeout transaction:_

* _MUST BE calculated to match:_
  1. _Multiply `feerate_per_kw` by 663 and divide by 1000 \(rounding down\)._

_The fee for an HTLC-success transaction:_

* _MUST BE calculated to match:_
  1. _Multiply `feerate_per_kw` by 703 and divide by 1000 \(rounding down\)._

_The base fee for a commitment transaction:_

* _MUST be calculated to match:_
  1. _Start with `weight` = 724._
  2. _For each committed HTLC, if that output is not trimmed as specified in_ [_Trimmed Outputs_](https://github.com/lightningnetwork/lightning-rfc/blob/master/03-transactions.md#trimmed-outputs)_, add 172 to `weight`._
  3. _Multiply `feerate_per_kw` by `weight`, divide by 1000 \(rounding down\)._

_**Example**_

_For example, suppose there is a `feerate_per_kw` of 5000, a `dust_limit_satoshis` of 546 satoshis, and a commitment transaction with:_

* _two offered HTLCs of 5000000 and 1000000 millisatoshis \(5000 and 1000 satoshis\)_
* _two received HTLCs of 7000000 and 800000 millisatoshis \(7000 and 800 satoshis\)_

_The HTLC-timeout transaction `weight` is 663, and thus the fee is 3315 satoshis. The HTLC-success transaction `weight`is 703, and thus the fee is 3515 satoshis_

_The commitment transaction `weight` is calculated as follows:_

* _`weight` starts at 724._
* _The offered HTLC of 5000 satoshis is above 546 + 3315 and results in:_
  * _an output of 5000 satoshi in the commitment transaction_
  * _an HTLC-timeout transaction of 5000 - 3315 satoshis that spends this output_
  * _`weight` increases to 896_
* _The offered HTLC of 1000 satoshis is below 546 + 3315 so it is trimmed._
* _The received HTLC of 7000 satoshis is above 546 + 3515 and results in:_
  * _an output of 7000 satoshi in the commitment transaction_
  * _an HTLC-success transaction of 7000 - 3515 satoshis that spends this output_
  * _`weight` increases to 1068_
* _The received HTLC of 800 satoshis is below 546 + 3515 so it is trimmed._

_The base commitment transaction fee is 5340 satoshi; the actual fee \(which adds the 1000 and 800 satoshi HTLCs that would make dust outputs\) is 7140 satoshi. The final fee may be even higher if the `to_local` or `to_remote` outputs fall below `dust_limit_satoshis`._

#### _Fee Payment_

_Base commitment transaction fees are extracted from the funder's amount; if that amount is insufficient, the entire amount of the funder's output is used._

_Note that after the fee amount is subtracted from the to-funder output, that output may be below `dust_limit_satoshis`, and thus will also contribute to fees._

_A node:_

* _if the resulting fee rate is too low:_
  * _MAY fail the channel._

## Resources



### See also

\[1\] [Historical Bitcoin Fees](https://bitcoinfees.info/)

## References

