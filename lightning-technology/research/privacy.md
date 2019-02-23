---
latest-revision: '2019-01-27T00:00:00.000Z'
original-author: Ryan Shea (ryan-shea)
created: '2019-01-01T00:00:00.000Z'
status: Accepted
title: Privacy (on Lightning Network)
contributors: Ryan Shea (ryan-shea)
type: article
description: ''
discussions-to: GitHub URL
category: lightning-rnd
---

# Privacy

While there is no public, trackable ledger of Lightning transactions, **privacy** on Lightning is still a work in progress. Through techniques like [onion routing](../lightning/onion-routing.md) and [eltoo](eltoo.md), privacy is improving.  

## Invoice and Channel Privacy

When you **create** an invoice, it reveals your node's public key, which stays the same for the lifetime of your node.  This has privacy implications:

* if you post invoices in public places, the pubkey may link together your identities across platforms
* the recipient of an invoice can link multiple invoices from the same node to eachother
* anyone can view the value of bitcoins that a node pubkey has in non-private channels
* anyone can view the channel opening and closing history of a node pubkey
* anyone can match public channel opening and closing events to the on-chain inputs used to find them, and can trace those inputs using blockchain analysis
* if your node is configured to broadcast a public IP address,
  * your invoice reveals the node's IP address and approximate geolocation
  * network participants can link together multiple nodes hosted at a single IP address
* if you use multiple nodes with a single identity, invoice recipients can link together those two nodes

When you **pay** invoices, much less information is revealed:

* A payment does not indicate to the recipient what node pubkey it originated from
* A node that routes a payment does not know conclusively which node the payment came from or which node the payment is going to
  * the routing node only knows which node forwarded it the payment and which node it was instructed to forward the payment to
* If the recipient service uses accounts of embeds user-provided information in the invoice, then obviously the service can link together invoices.

What things stay private?

* The existence and balance of **private channels** remains secret to every node except for the node you have opened the private channel to, unless that node chooses to disclose that information
* Your on-chain wallet balance that is not contained in a channel is not linked to your node pubkey, unless though it may be possible to link on-chain wallet balance to previously closed public channels through blockchain analysis
* If you use separate nodes with separate identities, there is not a straightforward way to link them

How does using [Tor with Lightning](../../tutorials/nodes/tor.md) improve your privacy?

* By connecting your node to Tor, other Lightning nodes connected to Tor can open channels to your node _without requiring you to broadcast a public IP address_

## Sphinx Routing

The current Lightning Network specification includes a solution to mask routing data from all intermediaries, based on [Sphinx](../lightning/sphinx-packet.md).

On Lightning, the payer determines a path over the peer-to-peer network and wraps a payment package in layers of encryption. Apart from just relay information, each intermediary also unpacks some additional data. This includes amounts, fees and more, along with allowing all intermediaries to set up a step in the payment chain.

Importantly, all intermediaries only learn from which channel they receive tokens, and to which channel they must forward the payment. The intermediaries have no idea whether they are the first step in the chain, the last step, a step somewhere in the middle, or perhaps even the only step. Whoever originally sent the transaction, and the one who ultimately receives it, remain known to only the sender and the receiver.

## Resources

[Will Lightning Help or Hurt Bitcoin Privacy?](https://www.coindesk.com/will-lightning-help-hurt-bitcoin-privacy)

## References

\[1\] [https://medium.com/@rusty\_lightning/the-bitcoin-lightning-spec-part-5-8-onion-routing-protocol-86c91e455909](https://medium.com/@rusty_lightning/the-bitcoin-lightning-spec-part-5-8-onion-routing-protocol-86c91e455909)

\[2\] [https://bitcoinmagazine.com/articles/how-the-lightning-network-layers-privacy-on-top-of-bitcoin-1482183775/](https://bitcoinmagazine.com/articles/how-the-lightning-network-layers-privacy-on-top-of-bitcoin-1482183775/)

