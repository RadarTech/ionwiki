---
latest-revision: '2019-01-27T00:00:00.000Z'
original-author: Ryan Shea (ryan-shea)
created: '2019-01-01T00:00:00.000Z'
status: Accepted
title: Macaroon
contributors: Ryan Shea (ryan-shea); Gareth James (gjradar)
type: article
description: ''
discussions-to: GitHub URL
category: lightning-software
---

# Macaroons

## Overview

**Macaroons** are authorization credentials that provide flexible support for controlled sharing in decentralized, distributed systems like Lightning.

A macaroon can interface with services and allow actions to be performed on behalf of a Lightning node. A macaroon is similar to a cookie, but unlike a traditional browser cookie, a macaroon can be created to have limited capabilities and then sent to others to use.

## Details

### Overview

Macaroons aim to combine the best aspects of using bearer tokens and using flexible, public-key certificates for authorization, by providing \(i\) the wide applicability, ease-of-use, and privacy benefits of bearer credentials based on fast cryptographic primitives, \(ii\) the expressiveness of truly decentralized credentials based on authorization logic, and \(iii\) general, precise restrictions on how, where, and when credentials may be used.

Macaroons allow Lightning Network users and services to authorize resource access using efficient, restricted bearer tokens that can be delegated further, and, via embedded caveats, attenuated in scope, subjected to third-party inspection and approval, and confined to be used only in certain contexts.

### Delegation

When a macaroon is created, delegations are created by adding restrictions \(called caveats\) and an authentication code similar to a digital signature.

Sharing a macaroon allows anyone in possession of that macaroon to use it to access `lnd` to do anything permitted by the macaroon. There is a specific type of restriction, called a "third party caveat," that requires an external service to verify the request; however, `lnd` does not currently support implementation of those caveats.

If a caveat is added to a macaroon and shared, the person receiving it cannot remove the caveat.

### Encryption

A macaroon should be sent over a secure channel. `lnd` enforces TLS for RPC requests, attempting to ensure security across the Lightning platform. Intercepting a macaroon allows the interceptor to use the macaroon to gain all privileges of the legitimate user.

## Resources

[Macaroon Technical Overview](https://github.com/lightningnetwork/lnd/blob/master/macaroons/README.md)

## References

\[1\] [https://github.com/lightningnetwork/lnd/blob/master/docs/macaroons.md](https://github.com/lightningnetwork/lnd/blob/master/docs/macaroons.md)

\[2\] [http://theory.stanford.edu/~ataly/Papers/macaroons.pdf](http://theory.stanford.edu/~ataly/Papers/macaroons.pdf)

\[3\] [https://store.clobig.com/what-are-macaroon-files-in-lnd/](https://store.clobig.com/what-are-macaroon-files-in-lnd/)
