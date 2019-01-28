---
category: bitcoin-basics
contributors: "Ryan Shea (ryan-shea)"
created: 2019-01-01
description: ""
discussions-to: "GitHub URL"
latest-revision: 2019-01-27
original-author: "Ryan Shea (ryan-shea)"
status: "Accepted"
title: "Pubkey"
type: article
---

# Pubkey

## Overview

A **pubkey** is a public portion of a keypair which can be used to verify [signatures](signatures-on-lightning.md) made with the private portion of the keypair.

## Details

Keys are a part of the [Elliptic Curve Digital Signature Algorithm](http://en.wikipedia.org/wiki/Elliptic_Curve_DSA). A private key is a random number, while the public key is a 2D point coordinate on an Elliptic Curve derived from it. The private key is used to sign messages \(in case of Bitcoin - the transactions\), and the public key is used to check whether the signature is correct. The public key can either be used raw in a transaction, or turned into a [Bitcoin address](https://en.bitcoin.it/wiki/Technical_background_of_Bitcoin_addresses) by means of [hashing ](hash.md)and other operations.

One can use any library that supports the ECDSA curve used by Bitcoin \(secp256k1\) to generate the appropriate keypair.

However, most commonly one leaves key pair generation to the Bitcoin program. If needed be, the private key can be retrieved from the program by using `dumpprivkey` [Bitcoin API](https://en.bitcoin.it/wiki/Original_Bitcoin_client/API_calls_list) call.

## Resources

[What is a private key and a public key?](https://bitcoin.stackexchange.com/questions/4675/what-is-a-private-key-and-a-public-key)

## References

\[1\] [https://bitcoin.org/en/glossary/public-key](https://bitcoin.org/en/glossary/public-key)

\[2\] [https://bitcoin.stackexchange.com/questions/4675/what-is-a-private-key-and-a-public-key](https://bitcoin.stackexchange.com/questions/4675/what-is-a-private-key-and-a-public-key)

\[3\] [https://bitcoin.org/en/glossary/private-key](https://bitcoin.org/en/glossary/private-key)
