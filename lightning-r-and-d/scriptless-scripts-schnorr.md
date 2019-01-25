---
latest-revision: '1999-01-29T00:00:00.000Z'
original-author: >-
  Isaac Newton (@appleman) < List of Original Authors' Real Name and Github;
  email address optional >
created: 1999-01-01 < ISO 8601 (yyyy-mm-dd) format >
status: >-
  < Draft | Under Review | Deferred | Proofing | Rejected | Withdrawn | Accepted
  | Superseded>
title: Scriptless Scripts (Schnorr)
contributors: >-
  Leonardo Da Vinci (@leodavinci); Galileo Galilei (@ggal) < List of
  contributors -- Real Name + Github; email optional >
type: null
description: Description guidelines
discussions-to: (GitHub PR)
category: null
---

# Scriptless Scripts \(Schnorr\)

## Overview

Scriptless Scripts is that \(fairly\) regular cryptographic signatures can indirectly reveal something that’s not part of the transaction that includes the signature. In other words, when someone signs to validate an ordinary Bitcoin transaction, it holds that a smart contract that is not hosted on the blockchain still executes faithfully.

Scriptless scripts are a way to encode smart contracts into digital signatures. The entire purpose is to do things without any scripts. Scriptless scripts are completely agnostic to which blockchain they are on, but they do require some sort of digital signature support. Scriptless scripts removes these hash preimages, removing these various different script tricks that people use to get atomicity between chains and transactions, and moving those into signatures so that you get something smaller, more efficient, more scalable, more private, and also it's inherently interoperable.



_In cryptography, a Schnorr signature is a digital signature produced by the Schnorr signature algorithm that was described by Claus Schnorr. It is a digital signature scheme known for its simplicity,\[1\] among the first whose security is based on the intractability of certain discrete logarithm problems.\[1\] It is efficient and generates short signatures._

\_\_

_is a way to use these kernels and kernel signatures to attach conditions to them without modifying the system so that the verifiers need to understand new rules. What I mean by this is that a set of parties can decide on some sort of contract or protocol that they want to execute, and as a result of faithful execution they will produce a valid signature and the blockchain and its verifiers can validate that the signature is valid. The blockchain does not need to know any of the details of the original transaction._

_Historically this came from mimblewimble. We wanted to be able to do cool stuff with mimblewimble, and we couldn't. But in fact, any system that supports or Schnorr signatures or some signature scheme that is linear in the data can do this scriptless script technique._

_There are many reasons to do this. I described the motivation for mimblewimble, but even for bitcoin and friends this is exciting. The reason being that, the existing paradigm for doing this is to use a script-signature system where you lay out the rules and then you lay out an explicit witness that those rules were followed. And then everyone downloads all of this and then verifies the witnesses for every single transaction, which prevents the mimblewimble-style compression that we talked about, but it also means that anybody who wants to do cool stuff can only do it within the framework that the entire system is aware of, namely the consensus system where everyone agrees on whether rules were followed or implemented at all. It's very difficult to extend this to do things that require primitives that do not or do not yet exist in the consensus system. As a secondary feature, we care about privacy and fungibility for public cryptocurrencies which have every transaction published and downloadable by everyone, and this is very bad for privacy and for commercial confidentiality especially if your amounts are on the blockchain. This makes it difficult to do business, when you're revealing all of your financial transactions, and this compromises any sort of real commercial use of this system. Using scriptless scripts, we avoid revealing contracts because all that hits the chain are public keys and signatures._

\_\_

_Let me get into some algebra to explain how this works. Probably most people here are familiar with Schnorr signatures or they at least saw them in school or something. Let me briefly overview how Schnorr multi-signatures work where you have multiple parties and you want to create a signature that every participant needs to contribute to produce the signatures. They all have their separate public keys. They sum these up to get a joint public key P and they want to produce a signature which validates with the key P such that all of them together would need to produce this. So they do the standard_ [_Schnorr signature_](https://diyhpl.us/wiki/transcripts/scalingbitcoin/milan/schnorr-signatures/) _thing which is that they think of a nonce R which is actually k \* G and you produce the signature s = k + ex where k is your secret nonce and e is the hash of the data going into the signature. To do a multisignature you just sum everythin so everyone chooses their own R = k \* G. Everybody passes around their different R values they pass them around to get a joint R value. Using the joint R value everyone computes their joint hash challenge and then they do the same thing except e is now a hash of their joint public key and something else. Your nonces are the sum of everyone's contributed nonces, and the signature is the sum of everyone's contributed signature values. Very easy. In practice, I should warn people that there are things called key cancelation attacks where people can choose their keys and nonces in adversarial ways and you need to be careful about it. But it's not an impossible problem and it wont derail anything that I'm talking about here._

_Kind of a philosophical point is that these multisignatures are already kind of a scriptless script in the sense that you have a bunch of people who have all of their own independent public keys and they add them together to get a joint key. They have a joint key and joint signatures. Public verifiers that weren't party to that, won't know how many people were involved, or that there were more than one person involved. They certainly don't know the original values. You can generalize this. If you look in the literature you'll find threshold signatures, a generalization of this to m-of-n signatures using linear secret sharing and this nice property that because a multisignature came from adding up everyone's nonces and signature values, then if you put a linear secret sharing scheme on there then you can basically do the same thing where you're contributing shares of signatures instead of entire signatures and it all just sort of works- magically._

## Details

### Section 1

### Section 2

### Section 3

## Resources

### Key People

* [Person 1](scriptless-scripts-schnorr.md)
* [Person 2](scriptless-scripts-schnorr.md)

### See also

## References

