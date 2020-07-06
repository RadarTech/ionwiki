---
description: quickly improve your Lightning Network connection
---

# Bootstrapping Liquidity

Your Lightning node starts with zero channels, and you must fund channels with other nodes on the network in order to send Lightning payments. Connecting to nodes that are already well-connected helps ensure that you will be able to find routes and send payments anywhere on the network.

Because payment channels are currently funded only by the initiating party \(though [dual-funded channels](../tech/channels/channel-opening.md) are eventually planned\), opening channels only gives you capacity to send, not to receive. To get receiving capacity, you must either open a channel and then spend money through it, or you must convince other nodes to open channels to you. This guide will walk you through the process!

## Spend With Lightning

The easiest way to get inbound capacity is to open a Lightning channel and then spend some of the BTC balance in it.  Spending money on Lightning transfers some of your Lightning channel "local balance" that you can spend into "remote balance" that you can use to receive Lightning payments.  When you receive a Lightning payment in a channel, "remote balance" within that channel is converted back into "local balance" that you can spend again—the circular Lightning economy!

For recommendations on places to spend money on the Lightning Network, see [Lightning Apps](apps/) and [Lightning Stores](stores.md).

You can also acquire inbound liquidity by selling BTC in the Lightning Network; see the article on [Lightning-compatible exchanges](lightning-exchanges.md).

## Ask For Inbound Channels

One way to get more inbound liquidity is simply to ask for it.  This does requires other nodes to lock up BTC to open a channel to you, so don't be surprised if your request does not receive a response.

Several Lightning request boards allow you to offer a bounty for others to complete requests, such as opening a channel to your node.  As of 2019-12, Microlancer and Sats-4-Likes are the most popular:

{% embed url="https://microlancer.io/" %}

{% embed url="https://kriptode.com/satsforlikes/index.html" %}

\[offline as of 2019-12-06\] [https://singles.shock.network/](https://singles.shock.network/) is an inbound liquidity request board. We have not tried it, but you can list your node there along with any conditions of opening a return channel and maybe someone will open inbound channels to you.

## Inbound Channel Marketplaces

Some node operators are offering the service of connecting back to other nodes if they meet certain criteria, usually opening a channel to their node first or making a payment. This page details some of these services that we have tested.

Please note that services that require you to pay to open a channel are NOT TRUSTLESS, so there is nothing technically stopping them from stealing your money. You should only use these if you trust the operator and/or small amounts of money are involved.

### Prerequisites

In order for another node to open a channel to your node, the other node must have a way of contacting your node on the network. There are several ways of accomplishing this:

1. using a wallet and a channel service that supports LNURL
2. configuring your node to advertise a public IP address
3. [connecting to the network with Tor](nodes/tor.md), if the other node is also connected to Tor
4. connecting first to the other node, whether or not you open a channel with that node

If you are using `lnd` on the command line, you can connect to a node with `lncli connect <pubkey>@<address>`. If your wallet app uses LND under the hood, it may or may not expose this functionality. Try starting to open a channel with the node and then cancelling it before actually sending the transaction.



### LNBIG

LNBIG is the operator of a large number of nodes that hold a significant fraction of the total BTC in the Lightning Network.  Simply fill out a form and LNBIG will open a channel to you.  Your wallet must support LNURL or you must have—and know how to use—terminal access to your node.

Successfully tested on 2019-11-05.

{% embed url="https://lnbig.com/" %}



### LightningTo.Me

By filling out the form on this website, this node will immediately open a 2,000,000 satoshi channel to you without conditions—you don't even need to open a channel to them!

Successfully tested on 2019-02-06.

{% embed url="https://lightningto.me/" caption="" %}

{% embed url="https://1ml.com/node/03bb88ccc444534da7b5b64b4f7b15e1eccb18e102db0e400d4b9cfe93763aa26d" caption="" %}



### LightningPowerUsers

If you open a channel to this node and fill out the form on the website, this node will open a channel of the same size back to you.

Successfully tested on 2019-11-05.

{% embed url="https://lightningpowerusers.com/home/" caption="" %}

{% embed url="https://1ml.com/node/0331f80652fb840239df8dc99205792bba2e559a05469915804c08420230e23c7c" caption="" %}



### Lightning Conductor

If you open a channel larger than 250,000 satoshis and fill out the form on the website, this node will open a 250,000 satoshi channel back to you.

Successful tested on 2019-02-06.

{% embed url="https://lightningconductor.net/channels" caption="" %}

{% embed url="https://1ml.com/node/03c436af41160a355fc1ed230a64f6a64bcbd2ae50f12171d1318f9782602be601" caption="" %}



### Y'alls

Pay a Lightning payment and Y'alls will open a channel back to your node. If your node doesn't appear on the list of node public keys, then Y'alls is not connected to your node \(see [prerequisites](bootstrapping-liquidity.md#prerequisites)\).

This exchange is **not trustless**, but there are several mitigating factors:

* Y'alls will only allow you to pay to attempt to open a channel to nodes that the Y'alls node is already connected to; therefore it's unlikely that Y'alls will not succeed in opening a channel once you have paid for it.
* Y'alls is run by [Alex Bosworth](https://twitter.com/alexbosworth/), an engineer at Lightning Labs.  He is a public figure that has made numerous contributions to the Lightning Network and is currently working on [LND](nodes/lnd.md).  It is unlikely that he is going to steal $0.50 from you.

Successfully tested on 2019-02-10. Offer was 18,900 satoshis for a 2,000,000 satoshi channel \(0.945%\)

Successfully tested on 2019-02-27. Offer was 63,000 satoshis for a 2,000,000 satoshi channel \(3.15%\)

Successfully tested on 2019-12.  Offer was $5.65 for a 4,000,00 satoshi channel \(1.89%\)

{% embed url="https://yalls.org/about/" caption="" %}



### Bitrefill

Bitrefill Thor is a service that charges high fees to open a channel to your node. The channel is only guaranteed to remain open for 30 days.

Due to high fees, we have not tested this service.

{% embed url="https://www.bitrefill.com/thor-lightning-network-channels/" caption="" %}



### Popmin.net

You must open a channel to their node OR pay a 10,000 satoshi one-time fee to "register".

Will open a channel to your node for a fee of 1% of the channel balance, up to 2,000,000 satoshis.

Successfully tested on 2019-02-15.

{% embed url="https://popmin.net/inbound" caption="" %}

{% embed url="https://1ml.com/node/03d24a4d2c8841890779f3c788cd269d467ad8ff8fcfdc21c8ceead42c7dd7f04b" caption="" %}



### WILL\_CONNECT\_BACK

This node's name and large number of channels suggests that it will connect back, but it's unclear what the terms of a reciprocal channel are.

Tested on 2019-02-09. Had not received a channel by 2019-02-15.

{% embed url="https://1ml.com/node/03ee180e8ee07f1f9c9987d98b5d5decf6bad7d058bdd8be3ad97c8e0dd2cdc7ba" caption="" %}









