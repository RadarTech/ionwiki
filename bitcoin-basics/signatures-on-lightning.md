---
category: bitcoin-basics
contributors: "Ryan Shea (ryan-shea); Gareth James (gjradar)"
created: 2019-01-01
description: ""
discussions-to: "GitHub URL"
latest-revision: 2019-01-27
original-author: "Ryan Shea (ryan-shea)"
status: "Accepted"
title: "Digital Signatures"
type: article
---

# Digital Signatures

## Overview

A **digital signature** is a mathematical concept used to demonstrate the authenticity of a digital document. A valid digital signature gives a recipient reason to believe that the message was created by a known sender \(authentication\), that the sender cannot deny having sent the message \(nonrepudiation\) and that the message was not altered in transit \(integrity\).

## Details

### How Digital Signatures Work

A digital signature consists of two parts. The first part is an algorithm for creating a signature, using a private key \(the signing key\), from a message \(the transaction\). The second part is an algorithm that allows anyone to verify the signature, given also the message and a public key.

The digital signature algorithm used in Bitcoin is the secp256k1 Elliptic Curve Digital Signature Algorithm.

### Signatures on Lightning

Digital signatures are an integral element of the multi signature holder address created in the establishment of a [channel](../lightning-basics/payment-channel.md). Two verified digital signatures are required to create the channel, as well as initiate the [closing transaction](../lightning-channels/channel-closing.md). Signatures are also essential to the [Hashed Timelock Transfer Contract](hltc.md), or HTLC, a smart contract that enables payments to be routed across the Lightning Network.

## Resources

[Digital Signatures \(Wikipedia\)](https://en.wikipedia.org/wiki/Digital_signature)

[Digital Signatures \(Mastering Bitcoin\)](https://github.com/bitcoinbook/bitcoinbook/blob/f8b883dcd4e3d1b9adf40fed59b7e898fbd9241f/ch06.asciidoc)

### See also

[Signature Hash Types \(SIGHASH\)](https://bitcoin.org/en/glossary/signature-hash)

## References

\[1\] [https://en.wikipedia.org/wiki/Digital\_signature](https://en.wikipedia.org/wiki/Digital_signature)

\[2\] [https://github.com/bitcoinbook/bitcoinbook/blob/f8b883dcd4e3d1b9adf40fed59b7e898fbd9241f/ch06.asciidoc](https://github.com/bitcoinbook/bitcoinbook/blob/f8b883dcd4e3d1b9adf40fed59b7e898fbd9241f/ch06.asciidoc)
