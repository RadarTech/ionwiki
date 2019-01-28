---
latest-revision: '2019-01-27T00:00:00.000Z'
original-author: Brandon Curtis (brandoncurtis))
created: '2019-01-01T00:00:00.000Z'
status: Accepted
title: Theft (on Lightning Network)
contributors: Ryan Shea (ryan-shea); Brandon Curtis (brandoncurtis)
type: article
description: ''
discussions-to: GitHub URL
category: lightning-troubleshooting
---

# Theft \(on Lightning Network\)

## Overview

Fraud and attempts on **theft** are prevented by channel update procedures. Any attempt to defraud the current agreed-upon balance in the channel results in the complete forfeiture of funds by the liable party.

## Details

### Attacks

To prevent an attack where Alice voids her payment by broadcasting the initial state of 5BTC/5BTC, there needs to be a way to revoke prior closing transactions. Payment revocation roughly works like the following.

When Alice broadcasts a closing transaction to the blockchain, she is attesting to the current state of the chain. But since there may be millions of closing transactions in a channel, all of which are valid, the blockchain itself can’t tell if what Alice attested to was indeed the correct state. Therefore, Alice must wait 3 days after broadcasting the closing transaction before she can redeem her funds. During this time, Bob is given a chance to reveal a secret that will allow him to sweep Alice’s funds immediately. Alice can thus revoke her claim to the money in some state by giving Bob the secret to the closing transaction. This allows Bob to take all of Alice’s money, but only if Alice attest to this old state by broadcasting the corresponding closing transaction to the blockchain.

### Theft via Cracking

As parties must be online and using private keys to sign, there is a possibility that, if the computer where the private keys are stored is compromised, coins will be stolen by the attacker. While there may be methods to mitigate the threat for the sender and the receiver, the intermediary nodes must be online and will likely be processing the transaction automatically. For this reason, the intermediary nodes will be at risk and should not be holding a substantial amount of money in this “hot wallet.” Intermediary nodes which have better security will likely be able to out-compete others in the long run and be able to conduct greater transaction volume due to lower fees. Historically, one of the largest component of fees and interest in the financial system are from various forms of counterparty risk – in Bitcoin it is possible that the largest component in fees will be derived from security risk premiums.

A Funding Transaction may have multiple outputs with multiple Commitment Transactions, with the Funding Transaction key and some Commitment Transactions keys stored offline. It is possible to create an equivalent of a “Checking Account” and “Savings Account” by moving funds between outputs from a Funding Transaction, with the “Savings Account” stored offline and requiring additional signatures from security services.

## Resources

[Lightning Network Whitepaper](https://lightning.network/lightning-network-paper.pdf)

[LND Overview](https://dev.lightning.community/overview/)

## References

\[1\] [https://dev.lightning.community/overview/\#channel-updates](https://dev.lightning.community/overview/#channel-updates)

\[2\] [https://lightning.network/lightning-network-paper.pdf](https://lightning.network/lightning-network-paper.pdf)

