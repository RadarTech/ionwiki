---
latest-revision: '1999-01-29T00:00:00.000Z'
original-author: >-
  Isaac Newton (@appleman) < List of Original Authors' Real Name and Github;
  email address optional >
created: 1999-01-01 < ISO 8601 (yyyy-mm-dd) format >
status: >-
  < Draft | Under Review | Deferred | Proofing | Rejected | Withdrawn | Accepted
  | Superseded>
title: Submarine swap
contributors: >-
  Leonardo Da Vinci (@leodavinci); Galileo Galilei (@ggal) < List of
  contributors -- Real Name + Github; email optional >
type: null
description: Description guidelines
discussions-to: (GitHub PR)
category: null
---

# Submarine Swap

## Overview

All you need to perform a conditional swap across two different networks is, essentially, a compatible hashlock so that you can construct mutually conditional HTLCs on each network. So what if one of these HTLCs is on the Lightning Network, and the other one is on-chain...?

This is entirely possible. This was figured out \(and put into production\) by Alex Bosworth, and he named it a "Submarine Swap" \(one half is above water \[on-chain\], one half is below water \[off-chain\]\).

A submarine swap essentially looks like this:

1. Alice produces or retrieves a Lightning Network payment invoice.  _It doesn't matter whether the Lightning payment is to Alice or to someone else that Alice is trying to pay_.
2. Alice presents the Lightning invoice to Bob, a "submarine swap provider".
3. Bob quotes what he must be paid _on chain_ in order to pay the Lightning invoice _off-chain_.
4. If Alice accepts the exchange rate, Bob and Alice work together and construct an HTLC that creates a conditional **on-chain** payment to Bob.
5. Alice makes the conditional payment to Bob.
6. The conditional payment to Bob is hashlocked with the same secret that will be revealed if the Lightning invoice is paid.  Bob can only redeem the conditional payment from Alice by making the Lightning payment.
7. Bob pays the Lightning invoice, forcing the Lightning payment recipient to reveal the secret S.
8. Bob uses the secret S to redeem the conditional payment from Alice.

If Bob does not pay the Lightning invoice before it expires, Bob is not able to redeem the conditional payment from Alice. In this case, Alice can wait for the HTLC to expire, then redeem the conditional payment's funds back to herself.

What do submarine swaps allow you to do?

* _trustlessly_ pay someone on-chain to perform an off-chain payment for you
* _trustlessly_ pay someone on-chain to buy coins on the Lightning Network from them

This means that a user can make Lightning Network payments without being on the Lightning Network, rebalance their Lightning Network channels with a fast and low-cost payment on another chain, and perform fast trustless Shapeshift-like swaps where the usual slow step is made instant!

Submarine conditional swaps have been demonstrated on the Bitcoin and Litecoin Lightning Networks, using on-chain payments on Bitcoin, Litecoin, and Bcash. They should also be possible \(albeit with more steps!\) using on-chain payments on other Bitcoin derivatives, Ethereum, Stellar, Ripple, and more.

Alex Bosworth has made all of his Submarine Swaps code open source: [https://github.com/submarineswaps/swaps-service](https://github.com/submarineswaps/swaps-service), [https://submarineswaps.org](https://submarineswaps.org)



A submarine swap essentially looks like this:

1. Alice produces or retrieves a Lightning Network payment invoice.  _It doesn't matter whether the Lightning payment is to Alice or to someone else that Alice is trying to pay_.
2. Alice presents the Lightning invoice to Bob, a "submarine swap provider".
3. Bob quotes what he must be paid _on chain_ in order to pay the Lightning invoice _off-chain_.
4. If Alice accepts the exchange rate, Bob and Alice work together and construct an HTLC that creates a conditional **on-chain** payment to Bob.
5. Alice makes the conditional payment to Bob.
6. The conditional payment to Bob is hashlocked with the same secret that will be revealed if the Lightning invoice is paid.  Bob can only redeem the conditional payment from Alice by making the Lightning payment.
7. Bob pays the Lightning invoice, forcing the Lightning payment recipient to reveal the secret S.
8. Bob uses the secret S to redeem the conditional payment from Alice.

If Bob does not pay the Lightning invoice before it expires, Bob is not able to redeem the conditional payment from Alice. In this case, Alice can wait for the HTLC to expire, then redeem the conditional payment's funds back to herself.

What do submarine swaps allow you to do?

* _trustlessly_ pay someone on-chain to perform an off-chain payment for you
* _trustlessly_ pay someone on-chain to buy coins on the Lightning Network from them

This means that a user can make Lightning Network payments without being on the Lightning Network, rebalance their Lightning Network channels with a fast and low-cost payment on another chain, and perform fast trustless Shapeshift-like swaps where the usual slow step is made instant!

## Details

### Section 1

### Section 2

### Section 3

## Resources

### Key People

* [Person 1](submarine-swap.md)
* [Person 2](submarine-swap.md)

### See also

## References

