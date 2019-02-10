---
description: quickly improve your Lightning Network connection
---

# Bootstrapping Channels

Your Lightning node starts with zero channels, and you must fund channels with other nodes on the network in order to send Lightning payments.  Connecting to nodes that are already well-connected helps ensure that you will be able to find routes and send payments anywhere on the network.

Because payment channels are currently funded only by the initiating party \(though [dual-funded channels](../../lightning-technology/lightning-channels/channel-opening.md) are eventually planned\), opening channels only gives you capacity to send, not to receive.  To get receiving capacity, you must either open a channel and then spend money through it, or you must convince other nodes to open channels to you.

## Prerequisites

In order for another node to open a channel to your node, the other node must have a way of contacting your node on the network.  There are several ways of accomplishing this:

1. configuring your node to advertise a public IP address
2. [connecting to the network with Tor](../nodes/tor.md), if the other node is also connected to Tor
3. connecting to another node that does 1 or 2, whether or not you open a channel with that node

If you are using `lnd` on the command line, you can connect to a node with `lncli connect <pubkey>@<address>`.  If your wallet app uses LND under the hood, it may or may not expose this functionality.  Try starting to open a channel with the node and then cancelling it before actually sending the transaction.

## Nodes That Open Back

Some node operators are offering the service of connecting back to other nodes if they meet certain criteria, often requiring them to open a channel first.  This page details some of these services that we have tested.

[https://singles.shock.network/](https://singles.shock.network/) is an inbound liquidity request board.  We have not tried it, but you can list your node there along with any conditions of opening a return channel and maybe someone will open inbound channels to you.

### Y'alls

Pay a Lightning payment for 18,900 satoshis \($0.68\) and Y'alls will open a 2,000,000 channel back to your node.  If your node doesn't appear on the list of node public keys, then Y'alls is not connected to your node \(see [prerequisites](bootstrapping-channels.md#prerequisites)\).

This exchange is **not trustless**, but there are several mitigating factors:

* Y'alls will only allow you to pay to attempt to open a channel to nodes that the Y'alls node is already connected to; therefore it's unlikely that Y'alls will not succeed in opening a channel once you have paid for it.
* Y'alls is run by [Alex Bosworth](https://twitter.com/alexbosworth/), an engineer at Lightning Labs.  He is a public figure that has made numerous contributions to the Lightning Network and is currently working on [LND](../nodes/lnd.md).  It is unlikely that he is going to steal $0.50 from you.

{% embed url="https://yalls.org/about/" %}

{% embed url="https://yalls.org/" %}

### LightningTo.Me

By filling out the form on this website, this node will immediately open a 2,000,000 satoshi channel to you without conditions—you don't even need to open a channel to them!

Successfully tested on 2019-02-06.

{% embed url="https://lightningto.me/" %}

{% embed url="https://1ml.com/node/03bb88ccc444534da7b5b64b4f7b15e1eccb18e102db0e400d4b9cfe93763aa26d" %}

### Lightning Conductor

If you open a channel larger than 250,000 satoshis and fill out the form on the website, this node will open a 250,000 satoshi channel back to you.

Successful tested on 2019-02-06.

{% embed url="https://lightningconductor.net/channels" %}

{% embed url="https://1ml.com/node/03c436af41160a355fc1ed230a64f6a64bcbd2ae50f12171d1318f9782602be601" %}

### LightningPowerUsers

If you open a channel larger than 500,000 satoshis and fill out the form on the website, this node will open a channel of the same size back to you.

Requested a channel on 2019-02-06 and had _not_ received a channel by 2019-02-10.

{% embed url="https://lightningpowerusers.com/home/" %}

{% embed url="https://1ml.com/node/0331f80652fb840239df8dc99205792bba2e559a05469915804c08420230e23c7c" %}

### WILL\_CONNECT\_BACK

This node's name and large number of channels suggests that it will connect back, but it's unclear what the terms of a reciprocal channel are.

Tested on 2019-02-09; awaiting results 24 hours later.  Does not appear to be automated.

{% embed url="https://1ml.com/node/03ee180e8ee07f1f9c9987d98b5d5decf6bad7d058bdd8be3ad97c8e0dd2cdc7ba" %}

## Huge Service Nodes

These nodes have lots of channels funded with lots of bitcoin.  Nodes that also host Lightning Network apps and services have a strong incentive to have good uptime and will tend to have larger volumes of inbound payments, so their channels with other nodes will tend to have both sending and receiving capacity. Connect to them and you can route payments through them to large swathes of the Lightning Network graph.  See the [1ML list by capacity](https://1ml.com/node?order=capacity) for other large nodes.

Note that without additional information, it is not possible to know whether a node is actually run by the individual or company that it is named after—anyone can name a node anything.  A representative _can_ prove that they control a particular Lightning node by signing a message with the private key that corresponds to the node's public key, e.g. in LND with `lncli signmessage <message>`.

### Y'alls

Y'alls is a Lightning-powered forum run by Alex Bosworth, an engineer at Lightning Labs.

{% embed url="https://1ml.com/node/03e50492eab4107a773141bb419e107bda3de3d55652e6e1a41225f06a0bbf2d56" %}

### Bitrefill

Bitrefill is a merchant that sells store credit and vouchers, bill payments, gift cards, cell phone minutes, and more for Lightning payments.

{% embed url="https://www.bitrefill.com/" %}

{% embed url="https://1ml.com/node/030c3f19d742ca294a55c00376b3b355c3c90d61c6b6b39554dbc7ac19b141c14f" %}

### Lightning Roulette

{% embed url="https://lightning-roulette.com/" %}

{% embed url="https://1ml.com/node/031678745383bd273b4c3dbefc8ffbf4847d85c2f62d3407c0c980430b3257c403" %}

### OpenNode

Opennode is a custodial Lightning payment processor.

{% embed url="https://www.opennode.co/" %}

{% embed url="https://1ml.com/node/03abf6f44c355dec0d5aa155bdbdd6e0c8fefe318eff402de65c6eb2e1be55dc3e" %}

### zigzag.io

ZigZag is a Shapeshift-like exchange that uses Lightning payments for the Bitcoin side of the exchange.

{% embed url="https://zigzag.io/" %}

{% embed url="https://1ml.com/node/0232e20e7b68b9b673fb25f48322b151a93186bffe4550045040673797ceca43cf" %}

### tippin.me

tippin.me is a custodial Lightning web wallet with Twitter login.

{% embed url="https://tippin.me/" %}

{% embed url="https://1ml.com/node/03c2abfa93eacec04721c019644584424aab2ba4dff3ac9bdab4e9c97007491dda" %}

### ACINQ

This node is a large-volume and high-uptime Eclair node run by ACINQ, the creators of the [Eclair node software](../nodes/eclair.md).  This node is the default connection recommended to [Eclair Mobile](../wallets/eclair-mobile.md) users.  Eclair Mobile users can't yet receive payments, but if you are able to establish receiving capacity from this node, you will have a short path to reliably receive payments from Eclair Mobile users.  Unfortunately we don't yet have a recommended way to accomplish this.

{% embed url="https://1ml.com/node/03864ef025fde8fb587d989186ce6a4a186895ee44a926bfc370e2c366597a3f8f" %}

### Satoshi Labs

Satoshi Labs is the creator of the Trezor hardware wallet.  We have not confirmed that this node is actually run by Satoshi Labs.

{% embed url="https://1ml.com/node/0279c22ed7a068d10dc1a38ae66d2d6461e269226c60258c021b1ddcdfe4b00bc4" %}

### LNBIG

LNBIG is an unknown entity that has set up dozens of Lightning Network nodes and used dozens of bitcoin to fund thousands of channels across the Lightning Network.  You will notice several LNBIG nodes on the [list of top capacity nodes](https://1ml.com/node?order=capacity).  The owner of LNBIG, as verified by a messaged signed by an LNBIG node key, sometimes posts messages in the [Y'alls forum](https://yalls.org/).  Because LNBIG doesn't offer any services, its channels tend to all be outgoing and unbalanced.  Whether you want to connect to this entity is up to you—they cannot steal Bitcoin in your Lightning channels, but their identity and intentions are unknown and they are a source of centralization in the Lightning Network.





