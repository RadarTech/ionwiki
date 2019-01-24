---
latest-revision: '1999-01-29T00:00:00.000Z'
original-author: >-
  Isaac Newton (@appleman) < List of Original Authors' Real Name and Github;
  email address optional >
created: 1999-01-01 < ISO 8601 (yyyy-mm-dd) format >
status: >-
  < Draft | Under Review | Deferred | Proofing | Rejected | Withdrawn | Accepted
  | Superseded>
title: LND
contributors: >-
  Leonardo Da Vinci (@leodavinci); Galileo Galilei (@ggal) < List of
  contributors -- Real Name + Github; email optional >
type: null
description: Description guidelines
discussions-to: (GitHub PR)
category: null
---

# LND

## Overview

**`lnd`**, or the Lightning Network Daemon, is a complete implementation of a BOLT-compliant Lightning Network node developed by Lightning Labs. It is currently deployed on the Bitcoin Test Network `testnet3` and on mainnet. `lnd` 0.1 alpha was released on January 11th, 2017, and since has been in active beta development. 

## Details

### Technical Details

`lnd` has several back-end chain services including [`btcd`](https://github.com/btcsuite/btcd) \(a full-node\), [`bitcoind`](https://github.com/bitcoin/bitcoin), and [`neutrino`](https://github.com/lightninglabs/neutrino) \(an experimental light client\). `lnd` is fully compliant with the current network specifications, outlined in the [Basis of Lightning Technology](../../lightning-basics/basics-of-lightning-technology-bolt.md) standards outline.

At the time of writing, January 14th, 2018, `lnd` is capable of:

* Creating channels.
* Closing channels.
* Completely managing all channel states \(including the exceptional ones!\).
* Maintaining a fully authenticated+validated channel graph.
* Performing path finding within the network, passively forwarding incoming payments.
* Sending outgoing [onion-encrypted payments](https://github.com/lightningnetwork/lightning-onion) through the network.
* Updating advertised fee schedules.
* Automatic channel management \([`autopilot`](https://github.com/lightningnetwork/lnd/tree/master/autopilot)\).

### Developer Resources

Lightning Labs has created multiple developer resources to facilitate application development. Alongside their two RPC interfaces \(a HTTP REST API and a gRPC service\), Lightning Labs has supporting documentation and a healthy ecosystem of developer tools.

## Resources

[lnd GitHub repository](https://github.com/lightningnetwork/lnd)

A set of developer resources including talks, articles, and example applications can be found at: [dev.lightning.community](https://dev.lightning.community/).

### Key People

* [Elizabeth Stark](https://twitter.com/starkness)
* [Olaoluwa Osuntokun](https://twitter.com/roasbeef)

### See also

* [Lightning Labs](https://lightning.engineering/)
* [Lightning Dev Slack](https://join.slack.com/t/lightningcommunity/shared_invite/enQtMzQ0OTQyNjE5NjU1LWRiMGNmOTZiNzU0MTVmYzc1ZGFkZTUyNzUwOGJjMjYwNWRkNWQzZWE3MTkwZjdjZGE5ZGNiNGVkMzI2MDU4ZTE)



## References

\[1\] [https://lightning.engineering/](https://lightning.engineering/)

\[2\] [https://dev.lightning.community/](https://dev.lightning.community/)

\[3\] [https://api.lightning.community/](https://api.lightning.community/)

