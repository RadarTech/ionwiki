# Lightning Hodl Invoice

## Overview

A **hodl invoice** (or **hold invoice**) is an implementation extension to a [Lightning Invoice](invoice.md) where the final step of an [HTLC](../bitcoin/htlc.md) resolution is withheld by the payment `receiver`, such that the payment `sender` is fully committed, and cancelled or executed _conditionally_ at a later time.

A **hodl invoice** is not distinguishable from a normal one to a payment `sender` other than it will have a longer-than-normal `expiry` parameter.

## Details

Successful [HTLC](../bitcoin/htlc.md) resolution in a [payment channel](payment-channel.md) is complete when a payment `receiver` exposes a preimage that hashes to a `payment_hash` of an [Invoice](invoice.md) and withdrawing the locked funds. When a `sender`'s funds are committed there is no option but to wait until hashlock resolution (completing the payment) or timelock `tl` expiration (canceling the payment). By setting a long enough `tl`, a payment `receiver` has the option to withhold (or cancel) resolution after funds have been committed until a time `t` such that `t < tl`, otherwise `tl` expires (`t >= tl`) and funds are redeemed back to the `sender`. The conditions by which the `receiver` settles or cancels the [invoice](invoice.md) can be arbitrary or cryptographically conditional (ie. the `receiver` does not know the preimage and must obtain it to settle the payment).

## Use Cases

### Simplified Merchant Returns

Return processes for settled purchases of out-of-stock inventory can be cumbersome. A merchant could use a **hodl invoice** to only accept payment after it has verified the inventory is in stock, or instantly refund the purchaser otherwise.

### Fidelity Bond

A user gains access to a service by paying a **hodl invoice**. If the user is malicious the service settles the [invoice](invoice.md), otherwise it is canceled when the user is finished and funds return to the user.

### Atomic Item Delivery Payment

Consider an `item` delivery shop, a customer could generate a `hash` of a `preimage` and send it to the shop. The shop generates an [invoice](invoice.md) with `payment_hash` equal to `hash` and user pays it, however the shop cannot settle it without `preimage`. Upon `item` delivery the customer reveals the `preimage` to the shop deliverer who then settles the [invoice](invoice.md).

### Atomic Multi-party Item Delivery Payment

TODO

## Key People
- [Joost Jager](https://twitter.com/joostjgr).

## References

1. [LND pull-request](https://github.com/lightningnetwork/lnd/pull/2022)
2. [The Lite Podcast](http://thelitepodcast.libsyn.com/lightning-network-routing-and-hodl-invoices) with Joost Jager.

