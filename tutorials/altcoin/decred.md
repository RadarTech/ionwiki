---
description: Join the Decred Lightning Network
---

# Decred LN

In late April 2019, the Lightning Network arrived for the Decred testnet; it is not currently \(as of May 6th 2019\) available for Mainnet.

### Installing DCRLND

Decred has chosen to enable users to connect to the Decred Lightning Network by maintaining `dcrlnd`, a Decred-specific fork of [LND](../nodes/lnd.md):

{% embed url="https://github.com/decred/dcrlnd" %}

Follow the installation instructions to install a Lightning Network node.  You will also need to have `dcrd` installed and synchronized to the blockchain.

{% embed url="https://github.com/decred/dcrlnd/blob/master/docs/INSTALL.md" %}

### Joining the Network

Use `dcrlncli newaddress p2pkh` to generate a new address for storing coins.  Testnet DCR coins are available from this official faucet:

{% embed url="https://faucet.decred.org/" %}

A Decred Testnet block explorer is available here:

{% embed url="https://testnet.decred.org/" %}

To connect to the Decred Lightning network, you'll need to use `dcrlncli connect` to establish a p2p connection to other nodes on the network and then `dcrlncli openchannel` to open payment channels to them.  Use these maps of the network to find other nodes to connect to:

{% embed url="http://explorer.dcr-test.ln.dead.cash/" %}

{% embed url="http://ln-map.jamieholdstock.com/" %}

### Other Resources

Join the Decred Slack to discuss the Decred Lightning Network and get support:

{% embed url="https://slack.decred.org" %}

Check out this other guide to installing DCRLND:

{% embed url="https://docs.google.com/document/d/12d4ZTnaPMPFtZHvPrMTkm5nsP2z3VUR1DB-Sf1U\_418/edit" %}



