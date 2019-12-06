---
description: Lightning nodes that run popular Lightning apps and services
---

# Nodes To Connect To

These nodes have lots of channels funded with lots of bitcoin. Nodes that also host Lightning Network apps and services have a strong incentive to have good uptime and will tend to have larger volumes of inbound payments, so their channels with other nodes will tend to have both sending and receiving capacity. Connect to them and you can route payments through them to large swathes of the Lightning Network graph. See the [1ML list by capacity](https://1ml.com/node?order=capacity) for other large nodes.

Note that without additional information, it is not possible to know whether a node is actually run by the individual or company that it is named after—anyone can name a node anything. A representative _can_ prove that they control a particular Lightning node by signing a message with the private key that corresponds to the node's public key, e.g. in LND with `lncli signmessage <message>`.

### Y'alls

Y'alls is a Lightning-powered forum run by Alex Bosworth, an engineer at Lightning Labs.

{% embed url="https://1ml.com/node/03e50492eab4107a773141bb419e107bda3de3d55652e6e1a41225f06a0bbf2d56" caption="" %}

### Bitrefill

Bitrefill is a merchant that sells store credit and vouchers, bill payments, gift cards, cell phone minutes, and more for Lightning payments.

{% embed url="https://www.bitrefill.com/" caption="" %}

{% embed url="https://1ml.com/node/030c3f19d742ca294a55c00376b3b355c3c90d61c6b6b39554dbc7ac19b141c14f" caption="" %}

### Lightning Roulette

{% embed url="https://lightning-roulette.com/" caption="" %}

{% embed url="https://1ml.com/node/031678745383bd273b4c3dbefc8ffbf4847d85c2f62d3407c0c980430b3257c403" caption="" %}

### OpenNode

Opennode is a custodial Lightning payment processor.

{% embed url="https://www.opennode.co/" caption="" %}

{% embed url="https://1ml.com/node/03abf6f44c355dec0d5aa155bdbdd6e0c8fefe318eff402de65c6eb2e1be55dc3e" caption="" %}

### zigzag.io

ZigZag is a Shapeshift-like exchange that uses Lightning payments for the Bitcoin side of the exchange.

{% embed url="https://zigzag.io/" caption="" %}

{% embed url="https://1ml.com/node/0232e20e7b68b9b673fb25f48322b151a93186bffe4550045040673797ceca43cf" caption="" %}

### tippin.me

tippin.me is a custodial Lightning web wallet with Twitter login.

{% embed url="https://tippin.me/" caption="" %}

{% embed url="https://1ml.com/node/03c2abfa93eacec04721c019644584424aab2ba4dff3ac9bdab4e9c97007491dda" caption="" %}

### Bottle Pay

Bottle Pay is a custodial Lightning web wallet which supports integration with multiple online accounts, such as Twitter, Instagram and Reddit.

{% embed url="https://about.bottle.li" caption="" %}

{% embed url="https://1ml.com/node/033025e6701f5266d5c7d83859d032213708e50430c82602b8d02d152c91853811" caption="" %}

### ACINQ

This node is a large-volume and high-uptime Eclair node run by ACINQ, the creators of the [Eclair node software](nodes/eclair.md). This node is the default connection recommended to [Eclair Mobile](wallets/eclair-mobile.md) users. If you are able to establish receiving capacity from this node, you will have a short path to reliably receive payments from many Eclair Mobile users.

{% embed url="https://1ml.com/node/03864ef025fde8fb587d989186ce6a4a186895ee44a926bfc370e2c366597a3f8f" caption="" %}

### Satoshi Labs

Satoshi Labs is the creator of the Trezor hardware wallet. We have not confirmed that this node is actually run by Satoshi Labs.

{% embed url="https://1ml.com/node/0279c22ed7a068d10dc1a38ae66d2d6461e269226c60258c021b1ddcdfe4b00bc4" caption="" %}

### LNBIG

LNBIG is an unknown entity that has set up dozens of Lightning Network nodes and used dozens of bitcoin to fund thousands of channels across the Lightning Network. You will notice several LNBIG nodes on the [list of top capacity nodes](https://1ml.com/node?order=capacity). The owner of LNBIG, as verified by a messaged signed by an LNBIG node key, sometimes posts messages in the [Y'alls forum](https://yalls.org/). Because LNBIG doesn't offer any services, its channels tend to all be outgoing and unbalanced. Whether you want to connect to this entity is up to you—they cannot steal Bitcoin in your Lightning channels, but their identity and intentions are unknown and they are a source of centralization in the Lightning Network.

