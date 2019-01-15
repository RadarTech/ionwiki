---
latest-revision: '1999-01-29T00:00:00.000Z'
original-author: >-
  Isaac Newton (@appleman) < List of Original Authors' Real Name and Github;
  email address optional >
created: 1999-01-01 < ISO 8601 (yyyy-mm-dd) format >
status: >-
  < Draft | Under Review | Deferred | Proofing | Rejected | Withdrawn | Accepted
  | Superseded>
title: Payment routing
contributors: >-
  Leonardo Da Vinci (@leodavinci); Galileo Galilei (@ggal) < List of
  contributors -- Real Name + Github; email optional >
type: null
description: Description guidelines
discussions-to: (GitHub PR)
category: null
---

# Payment Routing

## Overview

**Routing nodes** - We expect most Lightning users to be sending and receiving transactions using mobile devices or computers that have intermittent power and intermittent access to the internet. Because of this, the vast majority of channels will be opened between end user nodes and routing nodes. A routing node is a Lightning node operated with the intent to be online at all times, earning fees by routing Lightning payments. A routing node, like any other Lightning node, must be able to interface with the Bitcoin network. Routing nodes don’t necessarily need to be full nodes and can operate using light client protocols such as [neutrino](https://github.com/lightninglabs/neutrino). However, more heavily-capitalized routing nodes will likely prefer the additional security provided by a fully-validating Bitcoin node.

“Gateway” routing nodes are those that directly serve end users. These nodes will serve a relatively small number of users \(likely in the hundreds\) and will have modest hardware, bandwidth and capital requirements. Over time, some gateway nodes will become more highly connected \(see bridge channels below\). We’re currently working on tools and guides for routing node operators, and initial versions of those will be released over the coming months. Our goal is to help facilitate the development of a broadly distributed routing node ecosystem with low barriers to entry. 

as mentioned above, Carol connects to the Lightning Network through a set of routing nodes \(by default, Autopilot will create channels with five nodes\). A routing node is a computer intended to be online at all times, and that facilitates the sending of payments for other users. Bloomingblocks is also connected to the network via its own set of routing nodes. Through a process that’s analogous to finding connections between people in “Six Degrees of Separation,” Carol’s Lightning App automatically determines which nodes link her with Bloomingblocks, and Carol’s transaction is sent across that series of links. The next post in this series will provide more information about routing nodes, channel balance and the routing network.  


## Details

### Routing Hints

Routing hints specify a partial route from a public node to the node issuing the invoice and accepting the payment

By specifying a node_id and a chan\_id, the final step\(s\) in the route is fully specified even if the chan\_id refers to a channel that is private and \_not_ gossiped to the rest of the network.

you can inspect route hints with `lncli decodepayreq <invoice>` \(edited\) by specifying many many routing hints, the paying node can successfully route if it knows a route to _any_ of the specified public nodes and it's begun! Lightning Network Browser Wars

 [https://lightning-wallet.com/joint/](https://lightning-wallet.com/joint/) this is the first adventure \(that I am aware of\) of building a mess of nonstandard features into an otherwise normal LN node to improve performance for people who also run your nonstandard node

```text
    "route_hints": [                                           
        {
            "hop_hints": [
                {
                    "node_id": "03236a685d30096b26692dce0cf0fa7c8528bdf61dbf5363a3ef6d5c92733a3016",
                    "chan_id": "1589513382741409793",
                    "fee_base_msat": 1000,
                    "fee_proportional_millionths": 1,
                    "cltv_expiry_delta": 144
                }
            ]
        }
    ]
```

### Section 2

### Section 3

## Resources

### Key People

* [Person 1](payment-routing.md)
* [Person 2](payment-routing.md)

### See also

## References

