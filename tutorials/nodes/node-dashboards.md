---
category: lightning-software
contributors: Gareth James (sirgarethjames)
created: 2019-04-05
description: 
discussions-to: 
latest-revision: 
original-author: ""
status: 
title: Node Dashboards 
type: article 
---

# Node Dashboards

## Overview

Node dashboards are software that allow users to view or interact with a Lightning Network node without relying on the command line interface. They require the user to already have an instance of [LND](lnd.md), or the relevant Lightning Network daemon, running. They are not a substitute for LND or applications like [Zap Desktop wallet](../wallets/zap-desktop.md). 

## Details

Included below are existing examples of node dashboard options.

#### LND Explorer 

LND Explorer is a web interface for interacting with the Lightning Network \(via an underlying node\). They host demo nodes and a network graph explorer at [lndexplorer.com](https://lndexplorer.com/).

{% embed url="https://github.com/altangent/lnd-explorer" %}

#### LND Web Client (lncli-web) 

LND Web Client is a light-weight node monitoring and management solution that provides users a heads-up-display within their browser. It is written in NodeJS and Angular.

{% embed url="https://github.com/mably/lncli-web" %}

#### Ride The Lightning (RTL) 

RTL is a browser-based Lightning Network node dashboard designed to function across different device types. The home page furnishes information such as wallet balance, peers, channel balances, chain sync status, and other network information. It has a number of other pages that provide greater granularity and ability to manage the connected node. 

{% embed url="https://github.com/ShahanaFarooqui/RTL" %}

#### Lightning Dashboard (lndash)

Lightning Dashboard provides a basic, browser-based interface to view node information without additional visual detail. This includes standard identification data for a node, plus LND version details, simple peer & channel stats, and a pubkey QR code. Where lndash shines is in the more complex tabs on the dashboard: Channels, Events, Query, and Map. The Channels tab has some helpful metrics and graohs if you want to inspect, or even share, channel specific data. These include private metrics such as total payments within a channel, data sent and received, fee rate, min HTLC, time lock delta, and a simple slider bar for visualizing local and remote balance. 

{% embed url="https://github.com/djmelik/lndash" %}

#### LND-For-WP

A WordPress plugin that allows you to access your node from the administration panel. 

{% embed url="https://github.com/rstmsn/lnd-for-wp" %}

