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

## Details

The fee calculation for both commitment transactions and HTLC transactions is based on the current `feerate_per_kw`and the _expected weight_ of the transaction.

The actual and expected weights vary for several reasons:

* Bitcoin uses DER-encoded signatures, which vary in size.
* Bitcoin also uses variable-length integers, so a large number of outputs will take 3 bytes to encode rather than 1.
* The `to_remote` output may be below the dust limit.
* The `to_local` output may be below the dust limit once fees are extracted.

Thus, a simplified formula for _expected weight_ is used, which assumes:

* Signatures are 73 bytes long \(the maximum length\).
* There are a small number of outputs \(thus 1 byte to count them\).
* There are always both a `to_local` output and a `to_remote` output.

This yields the following _expected weights_ \(details of the computation in [Appendix A](https://github.com/lightningnetwork/lightning-rfc/blob/master/03-transactions.md#appendix-a-expected-weights)\):

```text
Commitment weight:   724 + 172 * num-untrimmed-htlc-outputs
HTLC-timeout weight: 663
HTLC-success weight: 703
```

Note the reference to the "base fee" for a commitment transaction in the requirements below, which is what the funder pays. The actual fee may be higher than the amount calculated here, due to rounding and trimmed outputs.

**Requirements**

The fee for an HTLC-timeout transaction:

* MUST BE calculated to match:
  1. Multiply `feerate_per_kw` by 663 and divide by 1000 \(rounding down\).

The fee for an HTLC-success transaction:

* MUST BE calculated to match:
  1. Multiply `feerate_per_kw` by 703 and divide by 1000 \(rounding down\).

The base fee for a commitment transaction:

* MUST be calculated to match:
  1. Start with `weight` = 724.
  2. For each committed HTLC, if that output is not trimmed as specified in [Trimmed Outputs](https://github.com/lightningnetwork/lightning-rfc/blob/master/03-transactions.md#trimmed-outputs), add 172 to `weight`.
  3. Multiply `feerate_per_kw` by `weight`, divide by 1000 \(rounding down\).

**Example**

For example, suppose there is a `feerate_per_kw` of 5000, a `dust_limit_satoshis` of 546 satoshis, and a commitment transaction with:

* two offered HTLCs of 5000000 and 1000000 millisatoshis \(5000 and 1000 satoshis\)
* two received HTLCs of 7000000 and 800000 millisatoshis \(7000 and 800 satoshis\)

The HTLC-timeout transaction `weight` is 663, and thus the fee is 3315 satoshis. The HTLC-success transaction `weight`is 703, and thus the fee is 3515 satoshis

The commitment transaction `weight` is calculated as follows:

* `weight` starts at 724.
* The offered HTLC of 5000 satoshis is above 546 + 3315 and results in:
  * an output of 5000 satoshi in the commitment transaction
  * an HTLC-timeout transaction of 5000 - 3315 satoshis that spends this output
  * `weight` increases to 896
* The offered HTLC of 1000 satoshis is below 546 + 3315 so it is trimmed.
* The received HTLC of 7000 satoshis is above 546 + 3515 and results in:
  * an output of 7000 satoshi in the commitment transaction
  * an HTLC-success transaction of 7000 - 3515 satoshis that spends this output
  * `weight` increases to 1068
* The received HTLC of 800 satoshis is below 546 + 3515 so it is trimmed.

The base commitment transaction fee is 5340 satoshi; the actual fee \(which adds the 1000 and 800 satoshi HTLCs that would make dust outputs\) is 7140 satoshi. The final fee may be even higher if the `to_local` or `to_remote` outputs fall below `dust_limit_satoshis`.

#### Fee Payment

Base commitment transaction fees are extracted from the funder's amount; if that amount is insufficient, the entire amount of the funder's output is used.

Note that after the fee amount is subtracted from the to-funder output, that output may be below `dust_limit_satoshis`, and thus will also contribute to fees.

A node:

* if the resulting fee rate is too low:
  * MAY fail the channel.

## Resources

### Key People

* [Person 1](fees.md)
* [Person 2](fees.md)

### See also

## References

