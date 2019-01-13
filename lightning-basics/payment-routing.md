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

