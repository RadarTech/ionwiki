---
category: lightning-rnd
contributors: "Ryan Shea (ryan-shea)"
created: 2019-01-01
description: ""
discussions-to: "GitHub URL"
latest-revision: 2019-01-27
original-author: "Ryan Shea (ryan-shea)"
status: "Accepted"
title: "Submarine Swap"
type: article
---

# Submarine Swap

## Overview

Submarine Swaps are atomic on-chain to off-chain conditional swaps \(and vice versa\) of cryptocurrencies.

This was made possible \(and put into production\) by Alex Bosworth, who named it a "Submarine Swap" \(one half is above water \[on-chain\], one half is below water \[off-chain\]\).

## Details

### Problem

Transactions between on-chain blockchain addresses and off-chain Lightning addresses are not directly compatible. This creates a transaction barrier between the underlying blockchain and the off-chain Lightning Network, regardless of implementation.

Submarine swaps solve this issue by enabling Lightning channels to be refilled via an on-chain transfer from the underlying blockchain to the off-chain LN channel.

### Structure

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

This means that a user can make Lightning Network payments without being on the Lightning Network, rebalance their Lightning Network channels with a fast and low-cost payment on another chain, and perform fast trustless swaps where the usual slow step is made instant.

Submarine conditional swaps have been demonstrated on the Bitcoin and Litecoin Lightning Networks, using on-chain payments on Bitcoin, Litecoin, and BCH. They should also be possible \(albeit with more steps\) using on-chain payments on other Bitcoin derivatives, Ethereum, Stellar, Ripple, and more.

## Resources

[Submarine Swaps](https://submarineswaps.org)

### Key People

* [Alex Bosworth](https://twitter.com/alexbosworth)

### See also

[Submarine Swaps Service](https://github.com/submarineswaps/swaps-service)

## References

\[1\] [https://submarineswaps.org/](https://submarineswaps.org/)
