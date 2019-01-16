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

**`lnd`**, or the Lightning Network Daemon, is a complete implementation of a BOLT-compliant Lightning Network node developed by Lightning Labs. It is currently deployed on the Bitcoin Test Network `testnet3`. `lnd` 0.1 alpha was released on January 11th, 2017, and since has been in active beta development. 

## Details

### Technical Details

_`lnd` has several pluggable back-end chain services including_ [_`btcd`_](https://github.com/btcsuite/btcd) _\(a full-node\),_ [_`bitcoind`_](https://github.com/bitcoin/bitcoin)_, and_ [_`neutrino`_](https://github.com/lightninglabs/neutrino) _\(a new experimental light client\). `lnd` is fully compliant with all current network specifications, outlined in the Basics of Lightning Technology standards outline._

_At the time of writing, January 14th, 2018, `lnd` is capable of:_

\_\_

* _Creating channels._
* _Closing channels._
* _Completely managing all channel states \(including the exceptional ones!\)._
* _Maintaining a fully authenticated+validated channel graph._
* _Performing path finding within the network, passively forwarding incoming payments._
* _Sending outgoing_ [_onion-encrypted payments_](https://github.com/lightningnetwork/lightning-onion) _through the network._
* _Updating advertised fee schedules._
* _Automatic channel management \(_[_`autopilot`_](https://github.com/lightningnetwork/lnd/tree/master/autopilot)_\)._

### _Developer Resources_

_`lnd`he daemon has been designed to be as developer friendly as possible in order to facilitate application development. Two primary RPC interfaces are exported: an HTTP REST API, and a_ [_gRPC_](https://grpc.io/) _service. The exported API's are not yet stable, so be warned: they may change drastically in the near future._

_An automatically generated set of documentation for the RPC APIs can be found at_ [_api.lightning.community_](https://api.lightning.community/)_._ 

_Finally, we also have an active_ [_Slack_](https://join.slack.com/t/lightningcommunity/shared_invite/enQtMzQ0OTQyNjE5NjU1LWRiMGNmOTZiNzU0MTVmYzc1ZGFkZTUyNzUwOGJjMjYwNWRkNWQzZWE3MTkwZjdjZGE5ZGNiNGVkMzI2MDU4ZTE) _where protocol developers, application developers, testers and users gather to discuss various aspects of `lnd` and also Lightning in general._

### Additional Features

## Resources

[lnd GitHub repository](https://github.com/lightningnetwork/lnd)

A set of developer resources including talks, articles, and example applications can be found at: [dev.lightning.community](https://dev.lightning.community/).

### Key People

* [Elizabeth Stark](https://twitter.com/starkness)
* [Olaoluwa Osuntokun](https://twitter.com/roasbeef)

### See also

* [Lightning Labs](https://lightning.engineering/)



## References

\[1\] 

