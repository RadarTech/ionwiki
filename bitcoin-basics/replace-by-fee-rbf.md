---
category: bitcoin-basics
contributors: "Ryan Shea (ryan-shea); Gareth James (gjradar)"
created: 2019-01-01
description: ""
discussions-to: "GitHub URL"
latest-revision: 2019-01-27
original-author: "Ryan Shea (ryan-shea)"
status: "Accepted"
title: "Replace By Fee (RBF)"
type: article
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
