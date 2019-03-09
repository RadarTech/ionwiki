# Static Channel Backup

## Overview

Static channel backups is a way of backing up state channels. Users will be able to safely claim their on-chain _and_ _off-chain_ funds in case something goes wrong. 

### Problem

> I accidentally deleted my lightning app and lost my channels. How can I safely recover my funds?

Accidentally deleting a lighting app or moving it to another machine can be stressful since funds are both on-chain and off-chain. Recovering on-chain funds should be as simple as importing the seed phrase. Unfortunately, [using the seed phrase will not recover off-chain funds](https://wiki.ion.radar.tech/tech/channels/channel-backups). Recovering off-chain funds requires keeping track of the state of the channel but if the channel is outdated, then that can be seen as malicious. Below are ways to backup and recover on-chain and off-chain funds.

### Solution 1: Back Up channel.db

A possible solution is to backup `channel.db` every time there's a routed payment. This method can be risky because the state of the channels may not be up to date. If a user unknowingly broadcasts an old state, then the other party can punish the user by taking all of their funds.

### Solution 2: Static Channel Backups \(SCB\)

_Note: SCB is still a work in progress._

Instead of trying to maintain the latest channel state, the static channel backup package will attempt to notify remote peers for force close the channel. This will prevent users from accidentally broadcasting an old state and allow them to close out and receive their local balance.

### How SCB It Works

Instead of trying to maintain the latest channel state, the static channel backup package will attempt to notify remote peers to force close their channel. This will prevent users from accidentally broadcasting an old state and allow them to safely close out and receive their local balance.

* User gets their 24 seed phrase
* User uses `lncli create` to input their seed phrase and recover their wallet
  * This allows the user to access their on-chain funds
  * Now it's time to access your off-chain funds
* The lnd `chanbackup` package will
  * Initiate the data loss protection \(DLP\) protocol to mark channels as "recovered"
  * Insert a `LinkNode` to attempt to connect to establish connections to all previous peers
* Once connected to a remote peer
  * Remote peer will send their latest un-revoked commitment point to derive keys
  * Remote peer will force close the channel
* User can now safely sweep the funds. This will transfer off-chain funds to the on-chain wallet \(backed up by the seed phrase\).

### How to Backup/Recover

There are several ways to backup the static channels. The easiest way is to save the `exportchanbackup`

* chan\_points: Is the on chain transaction hash
* multi\_chan\_backup: Is used to backup the channels

```text
$ lncli exportchanbackup --all
{
	"chan_points": [
		"bd517db739c55cbe13a8140a4dfdbb8e3b894b7396ee4e345ff15b0c535e8c92:0"
	],
	"multi_chan_backup": "ed6de05fa60db305030c242b8bfd0c57f749814168791e3160d96a8b0be4d7ab25e72014b1a86f93519abd8f678cadae017d3532faa35f87ee7caa3e88906416c979a761ec4aa1fd429314e9d51cfbfb428b9247ef3eef85fe3f2c3512d4213830c483aec2900626a52d239eaabdc0e8c7a01ee0d6fbe11e38987ba2742efd284d527bb26d6b9db2aebcae9df67dc3639b213525420b6a534d0a3ac2bee6b371ff891d1f0d19085ec97184e25b3122afe338b3fda88a592607cc796ec5e7ee5ea9edd5c8fe0064793b7b551241681bc65a088ed5ab6638"
}
```

Recover your wallet using your seed phrase

```text
$ lncli create
Input wallet password:
Confirm wallet password:

Do you have an existing cipher seed mnemonic you want to use? (Enter y/n): y

Input your 24-word mnemonic separated by spaces: about memory oblige country brain news harsh recipe what label decide inject this enforce face sustain slice mansion rookie fox word win finger stove

Input your cipher seed passphrase (press enter if your seed doesn't have a passphrase):
Input an optional address look-ahead used to scan for used keys (default 250):

!!!YOU MUST WRITE DOWN THIS SEED TO BE ABLE TO RESTORE THE WALLET!!!

---------------BEGIN LND CIPHER SEED---------------
 1. about   2. memory    3. oblige   4. country
 5. brain   6. news      7. harsh    8. recipe
 9. what   10. label    11. decide  12. inject
13. this   14. enforce  15. face    16. sustain
17. slice  18. mansion  19. rookie  20. fox
21. word   22. win      23. finger  24. stove
---------------END LND CIPHER SEED-----------------

!!!YOU MUST WRITE DOWN THIS SEED TO BE ABLE TO RESTORE THE WALLET!!!

lnd successfully initialized!
```

Restore channels

_Note: This feature is not complete_

```
$ lncli restorechanbackup --multi_backup ed6de05fa60db305030c242b8bfd0c57f749814168791e3160d96a8b0be4d7ab25e72014b1a86f93519abd8f678cadae017d3532faa35f87ee7caa3e88906416c979a761ec4aa1fd429314e9d51cfbfb428b9247ef3eef85fe3f2c3512d4213830c483aec2900626a52d239eaabdc0e8c7a01ee0d6fbe11e38987ba2742efd284d527bb26d6b9db2aebcae9df67dc3639b213525420b6a534d0a3ac2bee6b371ff891d1f0d19085ec97184e25b3122afe338b3fda88a592607cc796ec5e7ee5ea9edd5c8fe0064793b7b551241681bc65a088ed5ab6638
```

### Resources

[https://github.com/lightningnetwork/lnd/pull/2313](https://github.com/lightningnetwork/lnd/pull/2313)

