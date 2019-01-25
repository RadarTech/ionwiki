---
latest-revision: '1999-01-29T00:00:00.000Z'
original-author: >-
  Isaac Newton (@appleman) < List of Original Authors' Real Name and Github;
  email address optional >
created: 1999-01-01 < ISO 8601 (yyyy-mm-dd) format >
status: >-
  < Draft | Under Review | Deferred | Proofing | Rejected | Withdrawn | Accepted
  | Superseded>
title: Sphinx packet
contributors: >-
  Leonardo Da Vinci (@leodavinci); Galileo Galilei (@ggal) < List of
  contributors -- Real Name + Github; email optional >
type: null
description: Description guidelines
discussions-to: (GitHub PR)
category: null
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



