---
latest-revision: '1999-01-29T00:00:00.000Z'
original-author: >-
  Isaac Newton (@appleman) < List of Original Authors' Real Name and Github;
  email address optional >
created: 1999-01-01 < ISO 8601 (yyyy-mm-dd) format >
status: >-
  < Draft | Under Review | Deferred | Proofing | Rejected | Withdrawn | Accepted
  | Superseded>
title: Implementations (of lightning network)
contributors: >-
  Leonardo Da Vinci (@leodavinci); Galileo Galilei (@ggal) < List of
  contributors -- Real Name + Github; email optional >
type: null
description: Description guidelines
discussions-to: (GitHub PR)
category: null
---

# Network Implementations

## Overview

Participation in the [Lightning Network](../lightning-basics/lightning-network.md) requires running an implementation of a Lightning Network daemon software. This software launches and runs a unique [node](../lightning-basics/node.md) that allows communication with other peers on the network. Multiple versions, or implementations, have been created by different entities, just as multiple implementations of core Bitcoin software exist. Different implementations maintain interoperability by conforming to [BOLT](../lightning-basics/basics-of-lightning-technology-bolt.md) \(Basis of Lightning Technology\) standards.

## Details

### Existing Implementations

\*\*\*\*[**lnd**](lnd/), a BOLT-compliant Lightning node by Lightning Labs written in Golang [https://github.com/lightningnetwork/lnd](https://github.com/lightningnetwork/lnd)

\*\*\*\*[**c-lightning**](c-lightning.md), a BOLT-compliant Lightning node by Blockstream written in C [https://github.com/ElementsProject/lightning](https://github.com/ElementsProject/lightning)

\*\*\*\*[**Eclair**](eclair.md), a BOLT-compliant Lightning node by ACINQ written in Scala [https://github.com/ACINQ/eclair](https://github.com/ACINQ/eclair)

**Ptarmigan**, a BOLT-compliant Lightning node by written in C++ [https://github.com/nayutaco/ptarmigan](https://github.com/nayutaco/ptarmigan)

**LIT**, a non-BOLT-compliant Lightning node by MIT-DCI written in Go [https://github.com/mit-dci/lit](https://github.com/mit-dci/lit) Native multichain support and some other novel features developed by Tadge Dryja

## References

\[1\] [https://github.com/lightningnetwork/lnd](https://github.com/lightningnetwork/lnd)

\[2\] [https://github.com/ElementsProject/lightning](https://github.com/ElementsProject/lightning)

\[3\] [https://github.com/ACINQ/eclair](https://github.com/ACINQ/eclair)

\[4\] [https://github.com/nayutaco/ptarmigan](https://github.com/nayutaco/ptarmigan)

\[5\] [https://github.com/mit-dci/lit](https://github.com/mit-dci/lit)

