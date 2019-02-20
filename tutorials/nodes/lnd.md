---
latest-revision: '2019-01-27T00:00:00.000Z'
original-author: Ryan Shea (ryan-shea)
created: '2019-01-01T00:00:00.000Z'
status: Accepted
title: LND
contributors: Ryan Shea (ryan-shea); Gareth James (gjradar)
type: article
description: ''
discussions-to: GitHub URL
category: lightning-software
---

# LND

The Lightning Network Daemon \(LND\) is a complete Golang implementation of a [BOLT](../../tech/lightning/basics-of-lightning-technology-bolt.md)-compliant Lightning Network node developed by Lightning Labs. It can connect to the Lightning Networks deployed on Bitcoin \(mainnet, testnet3\) and Litecoin \(mainnet, testnet4\).

LND is open source software under [very active development on GitHub](https://github.com/lightningnetwork/lnd/projects/1): v0.1-alpha was released on January 11th 2017; v0.5-beta was released on September 18th 2018; v0.6-beta is expected in Spring 2019.

## Implementation Details

Lightning Labs is an active contributor to the BOLT standards and LND strives for compliance with these specifications.

### Chainwatcher Backends

Like all Lightning nodes, LND requires access to information stored in the blockchain in order to manage channels. LND accesses this information by connecting to a backend node that provides access to the chain.

On supported blockchains, LND can use the following full nodes:

* derived from Bitcoin Core: [bitcoind](https://github.com/bitcoin/bitcoin), [litecoind](https://github.com/litecoin-project/litecoin)
* derived from BTCsuite: [btcd](https://github.com/btcsuite/btcd), [ltcd](https://github.com/ltcsuite/ltcd)

These full nodes must be fully synced with a transaction index database \(e.g. `bitcoind -txindex=1`\) , which requires a substantial amount of disk space:

* bitcoin mainnet: 240 GB
* bitcoin testnet: 28 GB
* litecoin mainnet:  24 GB
* litecoin testnet: 2 GB

As a lightweight alternative for mobile and other resource-constrained devices, Lightning Labs is developing a lightweight trust-minimizing privacy-preserving Bitcoin light client called [Neutrino](https://github.com/lightninglabs/neutrino). In contrast, Neutrino requires only a few hundred MB of storage. LND ships with Neutrino and can be configured to automatically launch and manage it when LND is started. Neutrino can theoretically run on the Mainnet today if it is able to find `btcd` full node peers that will serve it compact filters, but due to [known money-losing bugs](https://github.com/lightninglabs/neutrino/issues) this is strongly discouraged. A mainnet-ready Neutrino is expected later in 2019.

### Client Capabilities

As of February 2019, LND is capable of:

* Creating channels.
* Closing channels.
* Completely managing all channel states \(including the exceptional ones!\).
* Maintaining a fully authenticated and validated channel graph.
* Performing path finding within the network, passively forwarding incoming payments.
* Sending outgoing [onion-encrypted payments](https://github.com/lightningnetwork/lightning-onion) through the network.
* Updating advertised fee schedules.
* Automatic channel management \(aka [`autopilot`](https://github.com/lightningnetwork/lnd/tree/master/autopilot)\)

## Developer Resources

Linux users can build LND from source with Go 1.11+:

```text
go get -d github.com/lightningnetwork/lnd
cd $GOPATH/src/github.com/lightningnetwork/lnd
git checkout v0.5.2-beta
make && make install
```

For more information, including setting up a Go environment, see the official LND guide:

{% embed url="https://github.com/lightningnetwork/lnd/blob/master/docs/INSTALL.md" caption="" %}

Pierre Rochard has created an LND Node Launcher application for quickly and easily installing a Lightning Network node on Windows and MacOS. Check out this tool and the accompanying installation guide:

{% embed url="https://github.com/lightning-power-users/node-launcher/" caption="" %}

{% embed url="https://medium.com/lightning-power-users/windows-macos-lightning-network-284bd5034340" caption="" %}

## References

1. [https://lightning.engineering/](https://lightning.engineering/) Lightning Labs homepage
2. [https://github.com/lightningnetwork/lnd](https://github.com/lightningnetwork/lnd) LND on Github
3. [https://dev.lightning.community/](https://dev.lightning.community/) developer resources for LND including talks, articles, and example applications
4. [https://api.lightning.community/](https://api.lightning.community/) [https://api.lightning.community/rest/](https://api.lightning.community/rest/) API documentation
5. [LND developers Slack chat](https://lightningcommunity.slack.com/join/shared_invite/enQtMzQ0OTQyNjE5NjU1LWRiMGNmOTZiNzU0MTVmYzc1ZGFkZTUyNzUwOGJjMjYwNWRkNWQzZWE3MTkwZjdjZGE5ZGNiNGVkMzI2MDU4ZTE)
6. CEO Elizabeth Stark - [Twitter](https://twitter.com/starkness), [GitHub](https://github.com/starkness)
7. CTO Olaoluwa Osuntokun - [Twitter](https://twitter.com/roasbeef), [GitHub](https://github.com/roasbeef)

