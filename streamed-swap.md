---
title: 'Streamed swap'
description: Description guidelines
original-author: Isaac Newton (@appleman) < List of Original Authors' Real Name and Github; email address optional >
contributors: Leonardo Da Vinci (@leodavinci); Galileo Galilei (@ggal) < List of contributors -- Real Name + Github; email optional >
discussions-to: (GitHub PR)
status: < Draft | Under Review | Deferred | Proofing | Rejected | Withdrawn | Accepted | Superseded>
type:
category:
created: 1999-01-01 < ISO 8601 (yyyy-mm-dd) format >
latest-revision: 1999-01-29
---

# Streamed swap

<!-- Use the same title outlined above -->

## Overview

<!--

"If you can't explain it simply, you don't understand it well enough." A couple sentences of non-technical, simple jargon.

(~240 characters)

-->

A streamed swap is an agreement between two parties to swap assets using a series of alternating micropayments.  This "streamed swap" is performed by having each party alternate turns in sending to the other party a small fraction of the total amount to be swapped.  The only amount risked by each party is the value of their most recent in-flight microtransfer; as the value of the microtransfer shrinks toward zero, this streamed swap approaches the zero theft risk of the conditional swap. Streamed swaps require both assets support fast and inexpensive micropayments.

The streamed swap is powerful because it enables cross-chain (nearly) atomic swaps between any two assets that can be transferred instantly using payment channels, even if these payment channels are unconditional or if they use incompatible hashlocks and can't be made mutually conditional.  This model is simple and elegant, and doesn't rely on payment channel implementers for different assets to coordinate.

## Details

<!--
Use this space to explain the protocol, concept, or project. This might include sections such as: Functionality, Features, or Requirements.

Use bullet points, diagrams, code snippets (you can use markdown), etc.

Each section should be >300 words -- and try to keep the article under 5 sections. For extended discussion, link to resources or create another page.

-->

### Section 1

### Section 2

### Section 3

## Resources

### Key People

<!-- List individuals that are integral to the project / feature / have helped in development. References to this section can be made in the earlier section of the post.

e.x. Satashi Nakomoto or Vitalik Buterin

-->

### See also
<!--

Add any external links in this section (that were not explicitly referenced in the content above).

e.x. Documentation sites, forums, publications

-->
## References

<!--

Cite all resources used in this section.

[See Wikipedia's citation guide.](https://en.wikipedia.org/wiki/Wikipedia:Citing_sources)

Our citation guide is a WIP.

-->
