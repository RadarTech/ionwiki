---
latest-revision: '2019-01-27T00:00:00.000Z'
original-author: Ryan Shea (ryan-shea)
created: '2019-01-01T00:00:00.000Z'
status: Accepted
title: Invoice
contributors: Ryan Shea (ryan-shea); Gareth James (gjradar)
type: article
description: ''
discussions-to: GitHub URL
category: lightning-basics
---

# Lightning Invoice

## Overview

An **invoice** represents a request for funds on the Lightning Network. Invoices include numerous parameters, both required and optional, such as payment amount, chain, expiry date, payee [pubkey](../bitcoin/pubkey.md), [routing hints](payment-routing.md#routing-hints), and other information. Invoices are used to make payments on the Lightning Network, rather than using [Bitcoin-style addresses](../bitcoin/bitcoin-address-formats.md).

Invoices are commonly presented as alphanumerical strings or QR codes. In order to parse specific information from the request string, users can pass the string into a decoding tool \[1\].

## Details

### Components

Every Lightning invoice requires the following information in order to be valid:

* `destination`: The public key of the person receiving the LN payment.
* `payment_hash`: The hash of the preimage that is used to lock the payment. You can only redeem a locked payment with the corresponding preimage to the payment hash. This enables routing on the Lightning Network without trusted third parties.
* `num_satoshis`: The amount of satoshis to be paid.
* `expiry`: Time when your node marks the invoice as invalid. Default is 1 hour or 3600 seconds.
* `timestamp`: Time when the invoice was created.  This is measured in [seconds since 1970](https://github.com/lightningnetwork/lightning-rfc/blob/master/11-payment-encoding.md#data-part).
* `cltv_expiry`: Delta to use for time-lock of CLTV extended to the final hop.

### Example Invoice

Below is a sample invoice decoded using an invoice decoding tool. The standard fields included are:

| Key | Value |  |
| :--- | :--- | :--- |
| Request String | lntb10m1pwr6x4spp57r8y5aslqnrmaap0cv3uefy9puchccjzre5k2nl2f4s9uuxr8xeqdqqcqzysxqzjc4ssgpuk27qesndex0sna6e33skjqwju5sd4ydcp0mnzctsvuq23sjst0wedlx9n6q0vj6md7auv7hjapdzu5qg5v34vfd6snwa5hnrqqnvhulk |  |
| Network | bitcoin testnet |  |
| Amount | 0.01 BTC |  |
| Date | Mon, 14 Jan 2019 23:26:40 GMT |  |
| Payment Hash | f0ce4a761f04c7bef42fc323cca4850f317c62421e69654fea4d605e70c339b2 |  |
| Min Final CLTV Expiry | 144 |  |
| Expiration | 600 seconds |  |
| Signature |  |  |
| _R value_ | ac2080f2caf03309b7267c27dd663185a4074b94836a46e02fdcc585c19c02a3 |  |
| _S value_ | 09416f765bf3167a03d92d6dbeef19ebcba168b940228c8d5896ea137769798c |  |
| _Recovery Flag_ | 0 |  |
| Signing Data | 6c6e746231306d0b87a356010d3c33929d87c131efbd0bf0c8f3292143cc5f1890879a5953fa9358179c30ce6c81a006002240c014b0 |  |
| Checksum | nvhulk |  |

```text
{
    "human_readable_part": {
        "prefix": "lntb",
        "amount": 1000000000
    },
    "data": {
        "time_stamp": 1547508400,
        "tags": [
            {
                "type": "p",
                "length": 52,
                "description": "payment_hash",
                "value": "f0ce4a761f04c7bef42fc323cca4850f317c62421e69654fea4d605e70c339b2"
            },
            {
                "type": "d",
                "length": 0,
                "description": "description",
                "value": ""
            },
            {
                "type": "c",
                "length": 2,
                "description": "min_final_cltv_expiry",
                "value": 144
            },
            {
                "type": "x",
                "length": 2,
                "description": "expiry",
                "value": 600
            }
        ],
        "signature": {
            "r": "ac2080f2caf03309b7267c27dd663185a4074b94836a46e02fdcc585c19c02a3",
            "s": "09416f765bf3167a03d92d6dbeef19ebcba168b940228c8d5896ea137769798c",
            "recovery_flag": 0
        },
        "signing_data": "6c6e746231306d0b87a356010d3c33929d87c131efbd0bf0c8f3292143cc5f1890879a5953fa9358179c30ce6c81a006002240c014b0"
    },
    "checksum": "nvhulk"
}
```

## Resources

Lightning Decoder

[https://lightningdecoder.com/](https://lightningdecoder.com/)

Lightning Payment Request Decoder

[https://lndecode.com/](https://lndecode.com/)

### See also

[Lightning Network Invoices](https://blockfuse.io/blog/lightning-network-invoices/)

## References

\[1\] [Lightning Decoder](https://lightningdecoder.com/)

\[2\] [BOLT \#11](https://github.com/lightningnetwork/lightning-rfc/blob/master/11-payment-encoding.md)

