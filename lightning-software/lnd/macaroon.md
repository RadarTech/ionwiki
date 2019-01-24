---
latest-revision: '1999-01-29T00:00:00.000Z'
original-author: >-
  Isaac Newton (@appleman) < List of Original Authors' Real Name and Github;
  email address optional >
created: 1999-01-01 < ISO 8601 (yyyy-mm-dd) format >
status: >-
  < Draft | Under Review | Deferred | Proofing | Rejected | Withdrawn | Accepted
  | Superseded>
title: Macaroon
contributors: >-
  Leonardo Da Vinci (@leodavinci); Galileo Galilei (@ggal) < List of
  contributors -- Real Name + Github; email optional >
type: null
description: Description guidelines
discussions-to: (GitHub PR)
category: null
---

# Macaroon

## Overview

A **macaroon** is an identifier tied to a Lightning node that can interface with services and allow actions to be performed. A macaroon is similar to a cookie, but unlike a traditional browser cookie, a macaroon can be created to have limited capabilities and then sent to others to use.

## Details

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

