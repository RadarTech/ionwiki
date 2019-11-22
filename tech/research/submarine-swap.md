---
latest-revision: '2019-11-21T00:00:00.000Z'
original-author: Ryan Shea (ryan-shea)
created: '2019-01-01T00:00:00.000Z'
status: Accepted
title: Submarine Swap
contributors: Ryan Shea (ryan-shea)
type: article
description: ''
discussions-to: GitHub URL
category: lightning-rnd
---

# Submarine Swap

Submarine Swaps are atomic on-chain to off-chain swaps \(and vice versa, often called Reverse Submarine Swaps\) of cryptocurrencies.

This was made possible \(and put into production\) by Alex Bosworth. Olaoluwa Osuntokun originally coined the term Submarine Swap — one half is above water \(on-chain\), one half is below water \(off-chain\).

## Technical Details

### Problem

Transactions between on-chain blockchain addresses and off-chain Lightning addresses are not directly compatible. This creates a transaction barrier between the underlying blockchain and the off-chain Lightning Network, regardless of implementation.

Submarine swaps solve this issue by enabling Lightning channels to be refilled via an on-chain transfer from the underlying blockchain to the off-chain LN channel.
Reverse Submarine swaps solves the off-chain to on-chain transactions and enable Lightning channels to be reversed obtaining inbound liquidity via an off-chain transfer in the LN to a on-chain address

### Structure

#### A submarine swap essentially looks like this:

1. Alice produces or retrieves a Lightning Network payment invoice.  _It doesn't matter whether the Lightning payment is to Alice or to someone else that Alice is trying to pay_.
2. Alice presents the Lightning invoice to Bob, a "submarine swap provider".
3. Bob quotes what he must be paid _on chain_ in order to pay the Lightning invoice _off-chain_.
4. If Alice accepts the exchange rate, Bob and Alice work together and construct an HTLC that creates a conditional **on-chain** payment to Bob.
5. Alice makes the conditional payment to Bob.
6. The conditional payment to Bob is hashlocked with the same secret that will be revealed if the Lightning invoice is paid.  Bob can only redeem the conditional payment from Alice by making the Lightning payment.
7. Bob pays the Lightning invoice, forcing the Lightning payment recipient to reveal the secret S.
8. Bob uses the secret S to redeem the conditional payment from Alice.

If Bob does not pay the Lightning invoice before it expires, Bob is not able to redeem the conditional payment from Alice. In this case, Alice can wait for the HTLC to expire, then redeem the conditional payment's funds back to herself.

What do submarine swaps allow you to do?

* _trustlessly_ pay someone on-chain to perform an off-chain payment for you

This means that a user can make Lightning Network payments without being on the Lightning Network, rebalance their Lightning Network channels \(refill\) with a fast and low-cost payment on another chain, and perform fast trustless swaps where the usual slow step is made instant.

Submarine conditional swaps have been demonstrated on the Bitcoin and Litecoin Lightning Networks, using on-chain payments on Bitcoin, Litecoin, and BCH. They are possible \(albeit with more steps\) using on-chain payments on other Bitcoin derivatives, Ethereum, Stellar, Ripple, and more.

#### A reverse submarine swap essentially looks like this:

1. Alice generates a secret preimage, think in the secret as a random number that only the user knows, we call it preimage because we are going to use it as an input of a hash function, and we are going to make public (at the beginning) only the hash, hashes are one way functions, so knowing the hash give other no clues about which is the secret, but reached the point where the secret is revealed anyone can check that the secret originated that exact hash

2. Alice sends off-chain \(via Lightning\) a conditional payment to  Bob, a "submarine swap provider", implemented with a HODL invoice, the condition is that the payment need the secret as an input to be settled or it will return to the payer \(Alice\) if a determined amount of time has elapsed. As soon as Bob discovers the secret \(when Alice reveals it\) he could take that money off-chain, meanwhile it will be on hold \(HODL\). We will call this, the swap payment

3. Alice sends off-chain \(via Lightning\) another payment, called the prepayment, in this case, this is a normal payment of at most a few thousands satoshis, with no condition as its purpose is to cover Bobs on-chain fees that needed to afford while constructing the swap structure. In case the swap fails or its cancelled, Alice won’t get this prepayment back, as the provider has already \(if he is fair\) spent that in the on-chain fees of the tx described below

4. Bob broadcasts an on-chain hash locked output tx ,it is a transaction to an output that can only be spent using the secret preimage, \(the one only Alice knows\) this is the payment to Alice on-chain and the amount of this transaction is the amount of the intended swap. It also has a time condition in case the swap fails, so as we have described we are in front of a Hash Time Locked Contract \(HTLC\), this is constructed using the same hash mentioned in 1., so the secret needed to unlock it, is the same that Alice generated and that at this point only Alice knows. This contract is imposing the following condition to Alice: “if you want the on-chain payment in your wallet, you have to let me settle the swap payment \(off-chain conditional payment\) by publishing your secret” in this way we have the same secret that unlocks the swap payment in favor of Bob and the on-chain payment in favor of Alice 

5. Alice publishes the secret by disclosing the secret preimage in the spending transaction, HTLC \(the on-chain transaction that put the money in Alice wallet, often called sweep the payment\), so now anyone can see the secret, especially the provider

6. Bob uses the same secret published by Alice in 5. to settle the swap payment, the HODL invoice \(Bobs off-chain money in exchange for the money he locked on-chain\)

What do reverse submarine swaps allow you to do?

* _trustlessly_ pay someone off-chain to perform an on-chain payment for you

This means that a user can make BTC payments even if he has all his funds commited to Lightning Network channels, rebalance their Lightning Network channels obtaining inbound liquidity, etc.

## Examples

### REDSHIFT
**Radar.tech** has released **RedShift**

{% embed url="https://ion.radar.tech/redshift" %}

### LOOP
**Lightning Labs** has released **Loop**, a submarine swap service that plugs into LND.  Loop allows users running LND nodes to exchange BTC in Lightning channels for BTC on-chain, and vice-versa.  Loop charges a fee \(0.1% as of 2019-10-24\) for this service.  The Loop client is open source but the server is proprietary—to perform a swap, you have to perform it with Lightning Labs.

The Loop swap server is hosted on this node:

`03fb2a0ca79c005f493f1faa83071d3a937cf220d4051dc48b8fe3a087879cf14a`

It's not possible to connect to this node directly, but you can connect to [this node ](https://1ml.com/node/021c97a90a411ff2b10dc2a8e32de2f29d2fa49d41bfbb52bd416e460db0747d0d)that acts as a gateway to the Loop node:

`021c97a90a411ff2b10dc2a8e32de2f29d2fa49d41bfbb52bd416e460db0747d0d@18.224.56.146:9735`

A Loop server is also available on the Bitcoin testnet at [this node](https://1ml.com/testnet/node/0223acffd7f363b4591ce860eda870fea352e981212d8a25e96a0ebea37faae288):

`0223acffd7f363b4591ce860eda870fea352e981212d8a25e96a0ebea37faae288@40.71.39.161:9735`

{% embed url="https://blog.lightning.engineering/posts/2019/03/20/loop.html" %}

{% embed url="https://github.com/lightninglabs/loop" %}

Up to now, the min amount to loop in one itaration is 250000 and the max amount to loop: 2000000, it can be obtained installing the loop command line client and executing `loop terms` and a quote could be request with `loop quote <amount>`

#### LOOP IN
Loop in is a submarine swap, in this case joining Lightning BTC with BTC, so you can send a bitcoin payment on-chain and receive Lightning BTC off-chain into a LN channel, making use of it you could get outbound liquidity, refill a channel, or you could pay off-chain with your on-chain funds, or withdraw from an exchange into your Lightning channel using the --external option which allows the on-chain HTLC transacting to be published externally

##### HOW IT WORKS
Lets define two actors, the user AKA Alice (the one who want to refill a channel, using the loop client) and the provider of the submarine swap AKA Bob (in this case the loop server)

Happy path:

1. The user presents to the provider a Lightning Network payment invoice (of the mount of the swap), that in the case of being paid will reveal a secret/preimage
2. The user and the provider work together to construct an HTLC that creates a conditional on-chain payment (of the mount of the swap) to the provider, the conditions are that the secret/preimage (the same of the LN invoice) needs to be presented for the funds to end at the provider side or if a time condition is reached the funds will be returned back to the user
3. The user broadcast the previous HTLC (makes the conditional payment to the provider)
4 .The provider can only satisfy the conditional payment condition if he pays the LN invoice, so he pays that forcing the Lightning payment recipient (the user here) to reveal the secret/preimage
5. The provider now knows the secret so he use it to redeem the conditional on-chain payment from the user (satisfy the 1st condition of the HTLC)

If the provider does not pay the Lightning invoice before it expires, he is not able to redeem the conditional payment from the user, so the user waits for the HTLC to reach the time condition and redeem the conditional payment's funds back. Here we have a penalty for the user as it will lock his funds for that time window

##### TESTNET EXAMPLE
```
$ loop in 2000000
Max swap fees for 2000000 Loop In: 2562
CONTINUE SWAP? (y/n), expand fee detail (x): x

Max on-chain fee:                 462
Max swap fee:                     2100
CONTINUE SWAP? (y/n): y
Swap initiated
ID:           880476479d5492c0a1dbbf83d55c91504cb000c1beeca65f72a7f43487cf3195
HTLC address: 2MuuE7evoExqtVmFX2K1WsJA6jpzY2aosac
Run `loop monitor` to monitor progress.
```

Monitor Output:
```
2019-11-18T12:40:22-03:00 LOOP_IN INITIATED 0.02 BTC - 2MuuE7evoExqtVmFX2K1WsJA6jpzY2aosac
2019-11-18T12:40:22-03:00 LOOP_IN HTLC_PUBLISHED 0.02 BTC - 2MuuE7evoExqtVmFX2K1WsJA6jpzY2aosac
2019-11-18T12:45:55-03:00 LOOP_IN INVOICE_SETTLED 0.02 BTC - 2MuuE7evoExqtVmFX2K1WsJA6jpzY2aosac (cost: server -1997900, onchain 0, offchain 0)
2019-11-18T13:05:53-03:00 LOOP_IN SUCCESS 0.02 BTC - 2MuuE7evoExqtVmFX2K1WsJA6jpzY2aosac (cost: server 2100, onchain 0, offchain 0)
```
[The swap HTLC](https://blockstream.info/testnet/address/2MuuE7evoExqtVmFX2K1WsJA6jpzY2aosac)

[User funds the HTLC](https://blockstream.info/testnet/tx/b7a46dceffca8b738344011fc74ad88cd5eb0c158ceee50b84d5ece3699672ae)

[Loop sweeps the HTLC](https://blockstream.info/testnet/tx/4dc4c183d937747db543a2f08753e16aa06ba688670ae9a1d24937f7544d4619)

INVOICE for swap (hint: use the [invoice decoder](https://ion.radar.tech/developers#decode)): **lntb19979u1pwa9wm9pp53qz8v3ua2jfvpgwmh7pa2hy32pxtqqxphmk2vhmj5l6rfp70xx2sdq8wdmkzuqcqzpgxq97zvuqum3je4pe5kwf539taw0dqvj0kg9yyynvk323ngkaaq75kcwzcwmpjyp3c7fax8eeqhp0qxuzmx2xsl57v4w6da39tqlttsalyafd2tcpkl6ngz**

The HTLC bitcoin script:
```
OP_SIZE 
OP_PUSHBYTES_1 20 
OP_EQUAL 
OP_IF 
OP_HASH160 
OP_PUSHBYTES_20 55c84ba23c5afcbdbe5a45b4fc5b0248a69c1b54  (preimage hash) 
OP_EQUALVERIFY 
OP_PUSHBYTES_33 0288f35c514096ffed23a81dd94f266402569f873d68a706df9302c0fca1c111b5 (loop server / provider address)
OP_ELSE 
OP_DROP 
OP_PUSHBYTES_3 6b9018 (value for absolute timelock CLTV)
OP_CLTV 
OP_DROP 
OP_PUSHBYTES_33 02d591d603a0766042dc19b33ff5082900be3d279da55bb888981157d4d2c0ad60 (user wallet address)
OP_ENDIF 
OP_CHECKSIG
```
In simple words it says: if the preimage/secret hashes is equal to **55c84ba23c5afcbdbe5a45b4fc5b0248a69c1b54**, then the LN invoice was paid, so send the on-chain funds to the provider, else if the time condition is reached (absolute time lock for **6b9018**) return the funds to the user

#### LOOP OUT
Loop out is a reverse submarine swap, in this case joining Lightning BTC with BTC, so you can send a Lightning payment off-chain and receive BTC on-chain to your wallet, making use of it you could get inbound liquidity, reverse a channel, or you could pay on-chain with your off-chain funds (suppose you have all your funds into channels) providing an external BTC address to were that funds should go.

##### HOW IT WORKS
Lets define two actors, the user AKA Alice (the one who want Inbound Liquidity, using the loop client) and the provider of the reverse submarine swap AKA Bob (in this case the loop server)

###### Happy path:

1.The user generates a secret preimage, think in the secret as a random number that only the user knows, we call it preimage because we are going to use it as an input of a hash function, and we are going to make public (at the beginning) only the hash, hashes are one way functions, so knowing the hash give other no clues about which is the secret, but reached the point where the secret is revealed anyone can check that the secret originated that exact hash

2.The user sends off-chain (via Lightning) a conditional payment to the provider, implemented with a HODL invoice, the condition is that the payment need the secret as an input to be settled or it will return to the payer (the user) if an amount of time has elapsed. As soon as the provider discovers the secret (when the user reveals it) he could take that money off-chain, meanwhile it will be on hold (HODL). We will call this, the swap payment

3.The user sends off-chain (via Lightning) another payment, called the prepayment, in this case, this is a normal payment of at most a few thousands satoshis, with no condition as its purpose is to cover the provider on-chain fees that he needs to afford while constructing the swap structure. In case the swap fails or its cancelled, the user won’t get this prepayment back, as the provider has already (if he is fair) spent that in the on-chain fees of the tx described below

4.The provider broadcasts an on-chain hash locked output tx ,it is a transaction to an output that can only be spent using the secret preimage, (the one only the user knows) this is the payment to the user on-chain and the amount of this transaction is the amount of the intended swap. It also has a time condition in case the swap fails, so as we have described we are in front of a Hash Time Locked Contract (HTLC), this is constructed using the same hash mentioned in 1), so the secret needed to unlock it, is the same that the user generated and that at this point only the user knows. This contract is imposing the following condition to the user: “if you want the on-chain payment in your wallet, you have to let me settle the swap payment (off-chain conditional payment) by publishing your secret” in this way we have the same secret that unlocks the swap payment in favor of the provider and the on-chain payment in favor of the user, let’s see how it’s done next 

5.The user publishes the secret by disclosing the secret preimage in the spending transaction, HTLC (the on-chain transaction that put the money in his wallet), so now anyone can see the secret, especially the provider

6.The provider uses the same secret published by the user in 5) to settle the swap payment, the HODL invoice (his off-chain money in exchange for the money he locked on-chain)

###### Unhappy possible paths:

If the provider holds the swap payment and doesn’t publish the transaction that give the money back on-chain to the user, the swap payment time condition will time out and the funds will be returned to the user. In this way the service is non-custodial, but there is a penalty for the user as it will lock his funds for that time window. The user loses the prepayment!

If the user never publishes the secret, the HTLC will time out, the on-chain funds will be returned to the provider, but the user has already paid with the prepayment the tx fees spent by the provider, it will lock some provider funds for that time window but it would have cost money to the user (the prepayment), here is where swap minimum and maximum values comes in as conditions from the provider in order to be protected

If the user reveals the secret 5) disclosing the spending tx but it stays in the mempool and is not mined, his off-chain funds held could go to the provider (the swap payment could be settled as the secret now is public) so the user needs to make sure that the tx is mined before the refund period begins. He can leverage fee bumping tools such as RBF and CPFP, that means to replace the tx fee for a greater one in order to incentivise miners to include it in the next block. This must be done before the HTLC time condition reached, as if this happens, the user will lose his funds (they go back to the provider) and the swap payment could be settled, the result is that the provider ends with all the money by his side. “The risk of the sweep transaction not confirming is dealt with in Lightning Loop by publishing with RBF enabled and trying to replace the sweep transaction in every block with a new transaction that is based on the latest fee estimate” the user could check this condition (the tx being correctly constructed) as the transaction will be public in mempool before deciding to publish his secret.
The user could choose a safe time lock before starting the swap as he needs to have a reasonable opportunity to get the sweep transaction confirmed “The actual expiry height of the HTLC is picked by the server when the swap is initiated and checked against an acceptable minimum by the Loop client implementation. If the server proposes an expiry height that is too soon, the off-chain swap payment will not be paid and the swap will be aborted.”

##### TESTNET EXAMPLE
```
$ loop out 2000000 --channel 1768408322629828608
Max swap fees for 2000000 Loop Out: 42593
CONTINUE SWAP? (y/n), expand fee detail (x)
Max on-chain fee:                 447
Max off-chain swap routing fee:   40010
Max off-chain prepay routing fee: 36
Max swap fee:                     2100
Max no show penalty:              1337
CONTINUE SWAP? (y/n) y
Swap initiated
ID:           368dc49234d219937de2ade6ced83c88864791fc4b9b40dc4a98d6f47eda7399
HTLC address: tb1qd9tfq2fjfyyylmwekfukde69jetexg0zn0c8u48mya6v8r2wz65s8c6pka

Run `loop monitor` to monitor progress.
```

Monitor Output:
```
2019-11-14T01:10:34-03:00 LOOP_OUT INITIATED 0.02 BTC - tb1qd9tfq2fjfyyylmwekfukde69jetexg0zn0c8u48mya6v8r2wz65s8c6pka
2019-11-14T01:27:08-03:00 LOOP_OUT PREIMAGE_REVEALED 0.02 BTC - tb1qd9tfq2fjfyyylmwekfukde69jetexg0zn0c8u48mya6v8r2wz65s8c6pka
2019-11-14T01:43:59-03:00 LOOP_OUT SUCCESS 0.02 BTC - tb1qd9tfq2fjfyyylmwekfukde69jetexg0zn0c8u48mya6v8r2wz65s8c6pka (cost: server 2100, onchain 138, offchain 7)
```
Swap payment (hint: use the [invoice decoder](https://ion.radar.tech/developers#decode)): **lntb20007630n1pwue5aepp5x6xufy356gvexl0z4hnvakpu3zry0y0ufwd5phz2nrt0glk6wwvsdq8wdmkzuqcqzxgxq97zvuq7cn6xqanj28xw6hs47w64ag9zmzhqgxx6sl2s0437evmcma6wqk3hxwegm4ctrdf009gfvp955ezxn2mrv0s5x00zxvu9lureyq5ptqqx44865**

Prepayment (hint: use the [invoice decoder](https://ion.radar.tech/developers#decode)): **lntb13370n1pwue5aepp5vnsn7a56htw8rhck09ehzcuhy65tg2rjy2rae2nuljftcqte3c6qdq2wpex2urp0ycqzxgxq97zvuqvme3wmyfjp56a6s0s6nw0t736ptxn2gdn0yv5vrj0qz2h4yu2hvpk6wau5cdk9k7xasfdjqw9nlgf5tpevp5rwcugzjdgdwnf2mm3fqqtj860s**

[The swap HTLC](https://blockstream.info/testnet/address/tb1qd9tfq2fjfyyylmwekfukde69jetexg0zn0c8u48mya6v8r2wz65s8c6pka)

[Loop Server funds the HTLC](https://blockstream.info/testnet/tx/eb97d56b81daba1e937f8706bd90705ef3f492c9ea4ca1c5cb3d54b77aa8b049)

[User sweeps the HTLC](https://blockstream.info/testnet/tx/ebc884d3c565065b44244b46911c9601a044aca76d99f83d7be6b54edbdc48a7)

The HTLC bitcoin script:
```
OP_SIZE 
OP_PUSHBYTES_1 20 
OP_EQUAL
OP_IF 
OP_HASH160 
OP_PUSHBYTES_20 fe8d137ab98993ae0cf58f05c090aacd30833ea9  (preimage hash)
OP_EQUALVERIFY 
OP_PUSHBYTES_33 0389cb5046e0faf7e3293a31d4475474d66e2dd759fe6e7ab8cdd7dc4d80aaa029 (user wallet address)
OP_ELSE 
OP_DROP 
OP_PUSHBYTES_3 168b18  (value for absolute timelock CLTV)
OP_CLTV 
OP_DROP 
OP_PUSHBYTES_33 03da6b37bb38bccb24ffa2ac618a1fa338845d8f91934b8ca2063cbaa7b7668953 (loop server / provider address)
OP_ENDIF
OP_CHECKSIG
```
In simple words it says: if the preimage/secret hashes is equal to **fe8d137ab98993ae0cf58f05c090aacd30833ea9**, then the HODL invoice was settled, so send the on-chain funds to the user, else if the time condition is reached (absolute time lock for **168b18**) return the funds to the provider

**Alex Bosworth** released an early demo of submarine swaps using fully open-source code:

{% embed url="https://submarineswaps.org/" %}

{% embed url="https://github.com/submarineswaps/swaps-service" %}

Boltz Exchange has also open-sourced an implementation that is also compatible with Litecoin LN:

{% embed url="https://boltz.exchange/" %}

{% embed url="https://github.com/BoltzExchange" %}

## Resources

[London Bitcoin Devs - Submarine Swaps and Loop](http://diyhpl.us/wiki/transcripts/london-bitcoin-devs/2019-07-03-alex-bosworth-submarine-swaps/)

[Submarine Swaps](https://submarineswaps.org)

[Loop out in depth](https://blog.lightning.engineering/technical/posts/2019/04/15/loop-out-in-depth.html)

### Key People

* [Alex Bosworth](https://twitter.com/alexbosworth)

### See also

[Submarine Swaps Service](https://github.com/submarineswaps/swaps-service)

## References

\[1\] [https://submarineswaps.org/](https://submarineswaps.org/)

