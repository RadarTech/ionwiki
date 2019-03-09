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

## Bash One-Liners

LND ships with `lncli`, a tool for controlling LND in the command line.  The outputs of `lncli` commands are often pages and pages of JSON that is hard to read.  By using standard Bash tools, you can reprocess this output into something that is more readable.

For these examples, you will need to install a small tool called [`jq`](https://stedolan.github.io/jq/) to process the JSON.  In Debian/Ubuntu Linux, you can do this with `sudo apt install jq`.

For instance, to view a **table of the payments your node routed** in 2019 \(use [epochconverter](https://www.epochconverter.com/) to go between Unix epoch time \(looks like `1552118735`\) and normal human time:

```text
$ lncli fwdinghistory --start_time 1546300800 --end_time 9999999999 --max_events 10000000 | jq '.forwarding_events[] | "(.timestamp|tonumber|gmtime|todate) (.amt_out|tonumber) (.fee|tonumber)"' | awk 'BEGIN {printf "%6s %18s %8s %5s\n", "id", "time", "sats", "fee"} {printf "%6s %18s %8s %5s\n", NR, substr($1,2,16), $2, substr($3,1,length($3)-1)}'

    id               time     sats   fee
     1   2019-01-01T19:28     1000     1
     2   2019-01-01T19:28     2000     1
     3   2019-01-02T19:39      151     1
     4   2019-01-02T23:06       70     1
     5   2019-01-02T23:08      151     1
```

To view a simple **table of your channels,** including how the channel balance is divided between you and your channel peer and whether your peer is online and the channel is active:

```text
lncli listchannels | jq '.channels[] | ["\(.remote_pubkey) \(.capacity) \(.local_balance) \(.remote_balance) \(.active)"] | @tsv'| awk 'BEGIN {printf "%19s %10s %10s %10s %7s\n", "peer", "capacity", "local", "remote", "active"} {printf "%19s %10s %10s %10s %7s\n", substr($1,2,16)"...", $2, $3, $4, substr($5,1,length($5)-1)}'
               peer   capacity      local     remote  active
020398acf2628709...    4999823    4737659     258860    true
022decf2837abadd...    5375294    5371990          0    true
023ab7123987213a...    9000000     159998    8836166    true
024832efabc23786...    1000000     497948     498747    true
02438972abcd3966...    1000000     941894      53449    true
0242387974587aba...    1886031      63000    1819195    false
```

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

