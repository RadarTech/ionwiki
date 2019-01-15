---
latest-revision: '1999-01-29T00:00:00.000Z'
original-author: >-
  Isaac Newton (@appleman) < List of Original Authors' Real Name and Github;
  email address optional >
created: 1999-01-01 < ISO 8601 (yyyy-mm-dd) format >
status: >-
  < Draft | Under Review | Deferred | Proofing | Rejected | Withdrawn | Accepted
  | Superseded>
title: Onion routing
contributors: >-
  Leonardo Da Vinci (@leodavinci); Galileo Galilei (@ggal) < List of
  contributors -- Real Name + Github; email optional >
type: null
description: Description guidelines
discussions-to: (GitHub PR)
category: null
---

# Onion Routing

## Overview

**Source routing and onion routing** - One of the differences between Lightning payment routing and most data network routing is that in the case of Lightning, the route is constructed by the payment sender \(source routing\), rather than being determined by the routers along the path. In addition, Lightning employs [onion routing](https://en.wikipedia.org/wiki/Onion_routing) for multi-hop payments. This means that intermediate nodes in the payment path know only the identity of their immediate predecessor and successor in the route. Importantly, the combination of source routing and onion routing protects the identities of payment senders and receivers so as to enhance user privacy and censorship-resistance.

Also note that the Lightning Network protocol supports [Tor](https://www.torproject.org/), and future releases of `lnd` will include Tor support. Communications from end user `lnd` nodes to gateway routing nodes will eventually default to Tor, providing additional privacy protection. 

[https://github.com/bitcoinbook/bitcoinbook/blob/f8b883dcd4e3d1b9adf40fed59b7e898fbd9241f/ch12.asciidoc](https://github.com/bitcoinbook/bitcoinbook/blob/f8b883dcd4e3d1b9adf40fed59b7e898fbd9241f/ch12.asciidoc)

[https://github.com/lightningnetwork/lightning-onion](https://github.com/lightningnetwork/lightning-onion)

## Details

### Section 1



### Section 2

### Section 3

## Resources

### Key People

* [Person 1](onion-routing.md)
* [Person 2](onion-routing.md)

### See also

## References

