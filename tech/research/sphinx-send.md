---
description: Send Lightning payments without using an invoice!
---

# Sphinx Send

Today \(2019-02-15\), you must acquire a one-time-use [Lightning invoice](../lightning/invoice.md) from a user in order to initiate a Lightning payment to them.  **Sphinx Send** is a technology currently in development that will allow any node to send a payment to any other \(online\) node without requiring an invoice.

## Implications

Today, a payer must receive a unique invoice from a payee for each payment:

{% embed url="https://twitter.com/pavolrusnak/status/1096414778845786113" %}

Many tools have been built that LND users can host on a webserver in order to dispense invoices to users:

{% embed url="https://github.com/brndnhrbrt/ln-donate-node" %}

{% embed url="https://github.com/michael1011/lightningtip" %}

With Sphinx Send, these dynamic invoice generators can be replaced with a static string or QR code that anyone can pay to.

## Progress

[LND](../../tutorials/nodes/lnd.md) has work-in-progress code that will enable Sphinx Send:

{% embed url="https://github.com/lightningnetwork/lnd/pull/2455" %}

This work is incomplete, but if you build two LND nodes from source using the `Roasbeef:new-eob-sphinx-send` feature branch, these nodes are able to exchange Sphinx Send payments.

