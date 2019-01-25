---
latest-revision: '1999-01-29T00:00:00.000Z'
original-author: >-
  Isaac Newton (@appleman) < List of Original Authors' Real Name and Github;
  email address optional >
created: 1999-01-01 < ISO 8601 (yyyy-mm-dd) format >
status: >-
  < Draft | Under Review | Deferred | Proofing | Rejected | Withdrawn | Accepted
  | Superseded>
title: Replace-by-fee (RBF)
contributors: >-
  Leonardo Da Vinci (@leodavinci); Galileo Galilei (@ggal) < List of
  contributors -- Real Name + Github; email optional >
type: null
description: Description guidelines
discussions-to: (GitHub PR)
category: null
---

# Replace-By-Fee \(RBF\)

## Overview

**Replace-by-fee** replaces one version of an unconfirmed transaction with a different version that pays a higher transaction fee. Often, RBF comes into play when a particular transaction is desired to be confirmed faster.

## Details

Bitcoin supports the concept that an unconfirmed transaction may be [modified](transaction-malleability.md) and reissued. Transaction replacement has been a critical element of the Bitcoin protocol since inception. 

When a user replaces a transaction by fee, the previous transaction outputs and inputs are kept -- the only difference is a higher fee as an incentive for miners.

## Resources

[Replace by Fee, Bitcoin Wiki](https://en.bitcoin.it/wiki/Replace_by_fee)

## References

\[1\] [https://bitcoin.org/en/glossary/rbf](https://bitcoin.org/en/glossary/rbf)

\[2\] [https://github.com/bitcoin/bips/blob/master/bip-0125.mediawiki](https://github.com/bitcoin/bips/blob/master/bip-0125.mediawiki)

