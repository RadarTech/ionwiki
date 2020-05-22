---
description: Send Lightning payments without using an invoice!
---

# Key Send

Before [lnd] [v0.9.0-beta] and [c-lightning] [v0.8.2] you must acquire a one-time-use [Lightning invoice](../lightning/invoice.md) from a user in order to initiate a Lightning payment to them.  **Key Send** is a technology that allows any node to send a payment to any other \(online\) node without requiring an invoice.

In [lnd] version 0.7.0, **Sphinx Send** was renamed to **Key Send**.

## Implications

Today, a payer must receive a unique invoice from a payee for each payment:

{% embed url="https://twitter.com/pavolrusnak/status/1096414778845786113" %}

Many tools have been built that LND users can host on a webserver in order to dispense invoices to users:

{% embed url="https://github.com/brndnhrbrt/ln-donate-node" %}

{% embed url="https://github.com/michael1011/lightningtip" %}

With Key Send, these dynamic invoice generators can be replaced with a static string or QR code that anyone can pay to.

## Progress

[LND] has **Key Send** payments implemented in [v0.9.0-beta]:

[c-lightning] has **Key Send** payments implemented in [v0.8.2] via plugin.

## Applications

Apart from being a way to make spontaneous payments without an invoice, **Key Send** payments could be used as a way to exchange messages with a payment attached to them. A minimum required payment could be used as a measure to prevent spam. A Lightning Network-based messaging platform [Juggernaut](https://github.com/LN-Juggernaut/juggernaut-desktop) uses **Key Send** to exchange messages between users and to make payment requests.

[v0.9.0-beta]: https://github.com/lightningnetwork/lnd/releases/tag/v0.9.0-beta
[v0.8.2]: https://github.com/ElementsProject/lightning/releases/tag/v0.8.2
[lnd]: ../../tutorials/nodes/lnd.md
[c-lightning]: ../../tutorials/nodes/c-lightning.md
