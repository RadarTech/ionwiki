---
category: bitcoin-basics
contributors: "Ryan Shea (ryan-shea); Gareth James (gjradar)"
created: 2019-01-01
description: ""
discussions-to: "GitHub URL"
latest-revision: 2019-01-27
original-author: "Ryan Shea (ryan-shea)"
status: "Accepted"
title: "Hash"
type: article
---

# Hash

## Overview

A hash algorithm turns an arbitrary amount of data into a fixed-length **hash**. A hash is a fingerprint of the input data, and the same fingerprint can always be produced from the same input data. Hashes are essential to cryptographic functions not only on Bitcoin but also on the Lightning Network.

## Details

### Bitcoin Hashes

Cryptographic hash functions are used extensively in Bitcoin: in bitcoin addresses, in script addresses, and in the mining Proof-of-Work algorithm. Bitcoin uses the SHA-256 algorithm to generate hashes.

### Private and Public Keys

![Image from Mastering Bitcoin](../.gitbook/assets/screen-shot-2019-01-24-at-8.46.37-am.png)

In private and public key cryptography, a one-way cryptographic hash function is used to generate a bitcoin address.

## Resources

[SHA-256 Hash Generator](https://www.movable-type.co.uk/scripts/sha256.html)

## References

\[1\] [https://en.bitcoin.it/wiki/Hash](https://en.bitcoin.it/wiki/Hash)

\[2\] [https://en.wikipedia.org/wiki/Cryptographic\_hash\_function](https://en.wikipedia.org/wiki/Cryptographic_hash_function)
