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

_The fee calculation for both commitment transactions and HTLC transactions is based on the current `feerate_per_kw`and the expected weight of the transaction._

_The actual and expected weights vary for several reasons:_

* _Bitcoin uses DER-encoded signatures, which vary in size._
* _Bitcoin also uses variable-length integers, so a large number of outputs will take 3 bytes to encode rather than 1._
* _The `to_remote` output may be below the dust limit._
* _The `to_local` output may be below the dust limit once fees are extracted._

_Thus, a simplified formula for expected weight is used, which assumes:_

* _Signatures are 73 bytes long \(the maximum length\)._
* _There are a small number of outputs \(thus 1 byte to count them\)._
* _There are always both a `to_local` output and a `to_remote` output._

_This yields the following expected weights \(details of the computation in_ [_Appendix A_](https://github.com/lightningnetwork/lightning-rfc/blob/master/03-transactions.md#appendix-a-expected-weights)_\):_

```text
Commitment weight:   724 + 172 * num-untrimmed-htlc-outputs
HTLC-timeout weight: 663
HTLC-success weight: 703
```

_Note the reference to the "base fee" for a commitment transaction in the requirements below, which is what the funder pays. The actual fee may be higher than the amount calculated here, due to rounding and trimmed outputs._

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

### Key People

* [Person 1](fees.md)
* [Person 2](fees.md)

### See also

## References

