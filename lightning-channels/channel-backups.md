---
category: lightning-channels
contributors: "Ryan Shea (ryan-shea)"
created: 2019-01-01
description: ""
discussions-to: "GitHub URL"
latest-revision: 2019-01-27
original-author: "Ryan Shea (ryan-shea)"
status: "Accepted"
title: "Channel Backups"
type: article
---

# Channel Backup

## Overview

Channel backup features aim to provide a simple safe to allow users to recover settled funds in channels in the case of partial or complete data loss.

## Details

### Technical Challenges

Backing up Lightning channels is difficult due to the complexity compared to backing up on-chain funds. Two problems arise when backing up of Lightning funds. First, the backup needs to be updated every time the state of the channel changes \(which happens several times during a single payment\). Second: if you restore channels from a backup that you think is up to date, but is actually an outdated stale state, then your counterparty could believe you are attempting to cheat on them and take all your money as a punishment.

Workarounds for this are being built in various implementations of the Lightning protocol.

### lnd Implementation

Lightning Labs has implemented a new safe scheme for static channel backups \(SCB's\) for `lnd`. The backups are encrypted using the a key derived from the user's seed, protecting the privacy of the users channels in the back up state, ensuring that a random node can't attempt to import another user's channels.

Given their **seed and the latest back up file**, the users are able to recover both their on-chain funds and funds that are fully settled within their channels.

{% hint style="info" %}
"Fully settled" refers to funds that are in the base commitment outputs, not HTLCs.
{% endhint %}

`lnd` can only restore funds as right after the channel is created. Resolving HTLCs is currently not possible.

Users can also recover from certain kinds of database corruption. Core code for handling recoveries is now in place, and combined with future planned developments, recovery of all funds in cases of data or device loss will be possible.

## Resources

[Lightning Labs Announcement](https://blog.lightning.engineering/announcement/2018/09/14/lnd-v0.5.html)

[ACINQ Channel Backups](https://medium.com/@ACINQ/enabling-automated-backup-on-eclair-wallet-9f58dc3d8407)

### See also

[Channel Backups in c-lightning](https://github.com/ElementsProject/lightning/issues/1156)

## References

\[1\] [https://github.com/lightningnetwork/lnd/pull/2313](https://github.com/lightningnetwork/lnd/pull/2313)

\[2\] [https://medium.com/@ACINQ/enabling-automated-backup-on-eclair-wallet-9f58dc3d8407](https://medium.com/@ACINQ/enabling-automated-backup-on-eclair-wallet-9f58dc3d8407)
