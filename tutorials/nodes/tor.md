---
description: Improve your Lightning Network privacy and connectivity with Tor
---

# Lightning with Tor

## Overview

This tutorial explains how to install and run [Tor](https://www.torproject.org/) with [LND](lnd.md). This allows you to connect to the Lightning Network without revealing your IP address and therefore your location. As an added bonus, Lightning nodes on Tor can accept incoming connections from other nodes on Tor even if they are behind one or more routers and do not have a publicly-accessible IP address.

Note that your privacy can be compromised if you do not also connect your backend node—`bitcoind` or `btcd`—to Tor. `bitcoind` will automatically seek out a Tor connection with a default configuration, but `btcd` requires some configuration.

## Install Tor

[Linux](https://www.torproject.org/docs/debian.html.en)

```text
$ sudo apt install tor
```

[OSX](https://www.torproject.org/docs/tor-doc-osx.html.en)

```text
$ brew install tor
```

**Verify installation**

```text
  $ tor --version
```

**Add Tor Configuration to** `torrc`

* Linux: `/etc/tor/torrc`
* OSX: `/usr/local/etc/tor/torrc`

```text
  SOCKSPort 9050
  Log notice stdout
  ControlPort 9051
  CookieAuthentication 1
```

## Run Tor

On any platform, this will work:

```text
$ tor
```

If you are on Ubuntu or Arch Linux and you use `systemctl`:

```text
sudo systemctl enable tor.service
sudo systemctl start tor.service
sudo systemctl status tor.service
```

## Configuring Your Node

### LND with Tor

Enable LND to connect to Tor:

* `tor.active` allows LND to route through Tor
* `tor.v3` sets up a v3 onion service
* `tor.streamisolation` will create a new circuit for each connection
* `listen` to localhost to prevent unintentional leaking of identifying information

  ```text
  $ lnd --tor.active --tor.v3 --listen=localhost --tor.streamisolation
  ```

  or update your `lnd.conf`:

```text
[Tor]
tor.active=true
tor.v3=true
tor.streamisolation=true
listen=localhost
```

You can connect to Tor and also broadcast a public IP address so that your node can serve as a gateway between the Tor and public networks.  **THIS DOES NOT PROVIDE YOU WITH ANY OF TOR'S PRIVACY ADVANTAGES.**  To this, add this to `lnd.conf`:

```text
externalip=<your public IP or domain name>:<your port, default 9735>
```

If you want to run multiple instances of LND simulaneously on the same machine and have them use different Tor Hidden Service addresses, add this to `lnd.conf` \(a new private key will automatically be created if the file specified here does not exist\):

```text
tor.privatekeypath=<yourpath>/v3_onion_private_key
```

**Linux Permissions Issues**

If you are on Ubuntu or Arch Linux, you may encounter a "cookie authentication error" when LND attempts to connect to Tor:

`2019-02-18 01:23:27.503 [ERR] SRVR: unable to start server: unable to retrieve authentication cookie: open /var/lib/tor/control_auth_cookie: permission denied`

You will need to make it possible for your user that runs LND to access the control cookie.

Check and see what user is running Tor:

`ps aux | grep tor`

Now see what the permissions are on the control cookie listed in the error:

`ls -lA /path/to/tor/cookie`

**Debian and Ubuntu**

Debian and Ubuntu's Tor control cookie is in `/var/run/tor/control.authcookie` and is readable by the `debian-tor` user and group. If you run LND with your regular user, try adding your regular user to the `debian-tor` group:

`sudo usermod -a -G debian-tor yourusername`

Log out and log back in again or run `sudo su - yourusername` to update your groups, then try running LND again and see if it can connect to Tor.

**Arch Linux**

Arch Linux's Tor control cookie is in `/var/lib/tor/control_auth_cookie` and is only readable by the `tor` user. One option is to add your user to the `tor` group and change the permissions on the directory to make it readable by members of the `tor` group:

```text
sudo usermod -a -G tor yourusername
sudo chmod 750 /var/lib/tor
sudo chmod 740 /var/lib/tor/control_auth_cookie
```

**Verifying LND success**

You have LND configured correctly when you see this message when LND starts:

`2019-02-18 05:34:47.906 [INF] SRVR: Proxying all network traffic via Tor (stream_isolation=true)! NOTE: Ensure the backend node is proxying over Tor as well`

**Verify LND Node Information**

Get your public key

```text
  $ lncli getinfo | grep identity_pubkey

  "identity_pubkey": "0346095e50ed1f8cf4dbda1fca442cd2ebccf082912e33c1c2e19868f1f56a190a",
```

Get node information about your public key

```text
  $ lncli getnodeinfo 0346095e50ed1f8cf4dbda1fca442cd2ebccf082912e33c1c2e19868f1f56a190a

  {
    "node": {
        "last_update": 1548783346,
        "pub_key": "0346095e50ed1f8cf4dbda1fca442cd2ebccf082912e33c1c2e19868f1f56a190a",
        "alias": "0346095e50ed1f8cf4db",
        "addresses": [
            {
                "network": "tcp",
                "addr": "b53ztxul4vdcktgcgmvcvgjigi2vq2hy4ah6wg7frqpiiesdoxozx3ad.onion:9735"
            }
        ],
        "color": "#3399ff"
    },
    "num_channels": 7,
    "total_capacity": "11732911"
  }
```

Verify that your `addr` is an `onion` address \(ending in '.onion' as above\)

### BTCD with Tor

Setup is not as self-explanatory as LND, so read the official Tor guide for BTCD:

{% embed url="https://github.com/btcsuite/btcd/blob/master/docs/configuring\_tor.md" caption="" %}

It looks like BTCD does not support v3 onion services:

{% embed url="https://github.com/btcsuite/btcd/issues/1070" caption="" %}

If you're a Golang person, submit a PR!

## Connect to Tor Nodes

Connecting to a Tor node is the same as connecting to any other node: `publicKey@address:port`

Example:

```text
lncli connect 0346095e50ed1f8cf4dbda1fca442cd2ebccf082912e33c1c2e19868f1f56a190a@b53ztxul4vdcktgcgmvcvgjigi2vq2hy4ah6wg7frqpiiesdoxozx3ad.onion:9735
lncli openchannel --node_key 0346095e50ed1f8cf4dbda1fca442cd2ebccf082912e33c1c2e19868f1f56a190a --local_amt 20000
```

Alternatively:

```text
lncli openchannel --node_key 0346095e50ed1f8cf4dbda1fca442cd2ebccf082912e33c1c2e19868f1f56a190a --connect b53ztxul4vdcktgcgmvcvgjigi2vq2hy4ah6wg7frqpiiesdoxozx3ad.onion:9735 --local_amt 20000
```

Looking for Tor nodes to connect to? 1ML has a filter for that:

{% embed url="https://1ml.com/node?order=capacity&iponionservice=true" caption="" %}

## Reference

[https://github.com/lightningnetwork/lnd/blob/master/docs/configuring\_tor.md](https://github.com/lightningnetwork/lnd/blob/master/docs/configuring_tor.md)

