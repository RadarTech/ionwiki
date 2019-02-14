# Hold Invoices

##  Overview

A **hodl invoice** \(or **hold invoice**\) is an implementation extension to a [Lightning Invoice](../lightning/invoice.md) where the final step of an [HTLC](https://github.com/RadarTech/ionwiki/tree/8fe28ac442984e71f4749aa4cabde12c4396bddf/tech/bitcoin/htlc.md) resolution is withheld by the payment `receiver`, such that the payment `sender` is fully committed, and cancelled or executed _conditionally_ at a later time.

A **hodl invoice** is not distinguishable from a normal one to a payment `sender` other than it will have a longer-than-normal `expiry` parameter.

## Details

Successful [HTLC](https://github.com/RadarTech/ionwiki/tree/8fe28ac442984e71f4749aa4cabde12c4396bddf/tech/bitcoin/htlc.md) resolution in a [payment channel](../lightning/payment-channel.md) is complete when a payment `receiver` exposes a preimage that hashes to a `payment_hash` of an [Invoice](../lightning/invoice.md) and withdrawing the locked funds. When a `sender`'s funds are committed there is no option but to wait until hashlock resolution \(completing the payment\) or timelock `tl` expiration \(canceling the payment\). By setting a long enough `tl`, a payment `receiver` has the option to withhold \(or cancel\) resolution after funds have been committed until a time `t` such that `t < tl`, otherwise `tl` expires \(`t >= tl`\) and funds are returned back to the `sender`. The conditions by which the `receiver` settles or cancels the [invoice](../lightning/invoice.md) can be arbitrary or cryptographically conditional \(ie. the `receiver` does not know the preimage and must obtain it to settle the payment\).

## Use Cases

### Simplified Merchant Returns

Return processes for settled purchases of out-of-stock inventory can be cumbersome. A merchant could use a **hodl invoice** to only accept payment after it has verified the inventory is in stock, or instantly refund the purchaser otherwise.

### Fidelity Bond

A user gains access to a service by paying a **hodl invoice**. If the user is malicious the service settles the [invoice](../lightning/invoice.md), otherwise it is canceled when the user is finished and funds return to the user.

### Atomic Item Delivery Payment

Consider an `item` delivery Shop, a Customer could generate a `hash` of a `preimage` and send it to the Shop. The Shop generates an [invoice](../lightning/invoice.md) with `payment_hash` equal to `hash` and Customer pays it, however the Shop cannot settle it without `preimage`. Upon `item` delivery the Customer reveals the `preimage` to the Shop Courier who then settles the [invoice](../lightning/invoice.md).

### Atomic Multi-party Item Delivery Payment

Consider an `item` Shop, an independent Courier, and a shop Customer:

* Customer generates a `preimage` and sends `hash` of `preimage` to the Shop
* Shop creates **hodl invoice** `invoice0` and Customer pays it
* Shop sends `hash` to the Courier who creates another **hodl invoice** `invoice1` \(for delivery costs\) with the same `payment_hash` and Shop pays it
* Upon delivery the Customer gives the `preimage` to the Courier who settles `invoice1` revealing the preimage to Shop who then settles `invoice0`.

### [Submarine Swap](submarine-swap.md) Variation

* Alice creates a `preimage` and sends `hash` to Bob
* Bob creates a **hodl invoice** with `payment_hash` equal to `hash`
* Alice pays the **hodl invoice**
* Bob creates an on-chain [HTLC](https://github.com/RadarTech/ionwiki/tree/8fe28ac442984e71f4749aa4cabde12c4396bddf/tech/bitcoin/htlc.md) with `hashlock` equal to `hash` and funds it
* Alice uses `preimage` to sweep funds from the on-chain [HTLC](https://github.com/RadarTech/ionwiki/tree/8fe28ac442984e71f4749aa4cabde12c4396bddf/tech/bitcoin/htlc.md)
* Bob uses revealed `preimage` to settle the **hodl invoice**

## Caveats

Reusing a `payment_hash` across multiple [invoices](../lightning/invoice.md) to create conditional payment chains incurs risk for all parties receiving the `preimage` after it has been revealed once as intermediate nodes on mutual payment paths will access the `preimage` that can be used to claim funds before the respective [HTLC](https://github.com/RadarTech/ionwiki/tree/8fe28ac442984e71f4749aa4cabde12c4396bddf/tech/bitcoin/htlc.md) resolution is complete, thereby potentially blocking settlement by the **hodl invoice** holder.

## Key People

* [Joost Jager](https://twitter.com/joostjgr).

## References

1. [LND pull-request](https://github.com/lightningnetwork/lnd/pull/2022)
2. [The Lite Podcast](http://thelitepodcast.libsyn.com/lightning-network-routing-and-hodl-invoices) with Joost Jager.

