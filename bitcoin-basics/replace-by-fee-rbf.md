---
latest-revision: '2019-01-27T00:00:00.000Z'
original-author: Ryan Shea (ryan-shea)
created: '2019-01-01T00:00:00.000Z'
status: Accepted
title: Replace By Fee (RBF)
contributors: Ryan Shea (ryan-shea); Gareth James (gjradar)
type: article
description: ''
discussions-to: GitHub URL
category: bitcoin-basics
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

