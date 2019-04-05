---
latest-revision: '2019-01-27T00:00:00.000Z'
original-author: Ryan Shea (ryan-shea)
created: '2019-01-01T00:00:00.000Z'
status: Accepted
title: c-lightning
contributors: Ryan Shea (ryan-shea)
type: article
description: ''
discussions-to: GitHub URL
category: lightning-software
---

# c-lightning

## Overview

**c-lightning** is a a [BOLT](../../lightning-technology/lightning/basics-of-lightning-technology-bolt.md)-compliant Lightning implementation by Blockstream \[2\] written in C. Version 1 of c-lightning was released on August 8th, 2015, and has since been under active beta development. c-lightning runs on Linux.

## Details

### Plugin Support Architecture

On top of complying with all BOLT standards, c-lightning is developing an architecture for plugins. Plugins can be built to extend the c-lightning command line API.

### Developer Tools

There are a number of developer tools, libraries and plugins that exist for the c-lightning implementation.

{% embed url="https://github.com/ElementsProject/lightning-charge" %}

{% embed url="https://github.com/ElementsProject/paypercall" %}

{% embed url="https://github.com/ElementsProject/lightning-charge-client-php" %}

{% embed url="https://github.com/ElementsProject/lightning-charge-client-js" %}

## Resources

[c-lightning GitHub](https://github.com/ElementsProject/lightning)

### Key People

* [Rusty Russell](https://github.com/rustyrussell)
* [Christian Decker](https://twitter.com/snyke?lang=en)

### See also

[c-lightning Plugin Collection](https://github.com/renepickhardt/c-lightning-plugin-collection)

## References

\[1\] [Blockstream](https://blockstream.com/)

\[2\] [c-lightning](https://github.com/ElementsProject/lightning)

