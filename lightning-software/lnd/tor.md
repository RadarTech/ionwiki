# Tor + LND

## Overview

This tutorial explains how to install [tor](https://wiki.ion.radar.tech/lightning-basics/onion-routing) with lnd. This allows anonymous networking connections.

## Install Tor

[Linux](https://www.torproject.org/docs/debian.html.en)

```text
$ sudo apt install tor
```

[OSX](https://www.torproject.org/docs/tor-doc-osx.html.en)

```text
$ brew install tor
```

## Verify installation

```text
  $ tor --version
```

## Add Tor Configuration to `torrc`

Linux: `/etc/tor/torrc`

OSX: `/usr/local/etc/tor/torrc`

```text
  SOCKSPort 9050
  Log notice stdout
  ControlPort 9051
  CookieAuthentication 1
```

## Run Tor

```text
$ tor
```

## Run lnd with Tor Configurations

Enable lnd to connect to Tor

* `tor.active` allows lnd to route through Tor
* `tor.v3` sets up a v3 onion service
* `tor.streamisolation` will create a new circuit for each connection
* `listen` to localhost to prevent unintentional leaking of identifying information

  ```text
  $ lnd --tor.active --tor.v3 --listen=localhost --tor.streamisolation
  ```

  or update your `lnd.conf`

  ```text
  tor.active=true
  tor.v3=true
  tor.streamisolation=true
  listen=localhost
  ```

## Verify lnd Node Information

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

## How to Connect

Connecting to a Tor node is the same as connecting to any other node: `publicKey@address:port`

Example:

```text
lncli openchannel --node_key 0346095e50ed1f8cf4dbda1fca442cd2ebccf082912e33c1c2e19868f1f56a190a --connect b53ztxul4vdcktgcgmvcvgjigi2vq2hy4ah6wg7frqpiiesdoxozx3ad.onion:9735 --local_amt 20000
```

## Reference

[https://github.com/lightningnetwork/lnd/blob/master/docs/configuring\_tor.md](https://github.com/lightningnetwork/lnd/blob/master/docs/configuring_tor.md)

