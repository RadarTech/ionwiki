---
latest-revision: '2019-01-27T00:00:00.000Z'
original-author: Ryan Shea (ryan-shea)
created: '2019-01-01T00:00:00.000Z'
status: Accepted
title: Sphinx packet
contributors: Ryan Shea (ryan-shea)
type: article
description: ''
discussions-to: GitHub URL
category: lightning-basics
---

# Sphinx Packet

## Overview

The Sphinx cryptographic packet format is a compact and provably secure design introduced by George Danezis and Ian Goldberg. It supports a full set of security features: indistinguishable replies, hiding the path length and relay position, detection of tagging attacks and replay attacks, as well as providing unlinkability for each leg of the packet’s journey over the network.

Sphinx is used in `lnd` to relay anonymized messages within the Lightning Network.

## Resources

[Sphinx Format Paper](https://cypherpunks.ca/~iang/pubs/Sphinx_Oakland09.pdf)

## References

\[1\] [https://github.com/lightningnetwork/lightning-rfc/wiki/Rendez-vous-mechanism-on-top-of-Sphinx](https://github.com/lightningnetwork/lightning-rfc/wiki/Rendez-vous-mechanism-on-top-of-Sphinx)

\[2\] [https://katzenpost.mixnetworks.org/docs/specs/sphinx.html](https://katzenpost.mixnetworks.org/docs/specs/sphinx.html)

\[3\] [https://cypherpunks.ca/~iang/pubs/Sphinx\_Oakland09.pdf](https://cypherpunks.ca/~iang/pubs/Sphinx_Oakland09.pdf)

