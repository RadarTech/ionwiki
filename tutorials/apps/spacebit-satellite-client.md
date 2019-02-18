# Spacebit Satellite Client

Ever want to pay magic internet money to send `HELLO WORLD` to the entire world by bouncing it off a satellite? It's 2019 and this is a thing you can do. Bid testnet bitcoin using Lightning payments in order to send messages through a fleet of five [Blockstream satellites](https://blockstream.com/satellite/) that broadcast over pretty much the entire planet; anyone listening in with a satellite dish will get your message.

Sending a message with this service couldn't be easier, but verifying your message was sent requires tools that aren't as user-friendly.

{% embed url="https://spacebit.live/" caption="Use this tool to pay for and broadcast messages" %}

{% embed url="https://1ml.com/testnet/node/039d2201586141a3fff708067aa270aa4f6a724227d5740254d4e34da262a79c2a" caption="This is the node that accepts testnet BTC payments for Spacebit " %}

## Receive Messages

{% embed url="https://blockstream.com/satellite/" caption="Use this tool to verify that your message has been broadcast" %}

{% embed url="https://github.com/Blockstream/satellite" caption="Use these tools to receive messages sent by you and others, with or without a satellite dish" %}

Once you've installed the Blockstream satellite Python utilities, run the following to receive messages sent over the satellite by connecting directly to a server, no satellite dish needed:

```text
blockstream-satellite/api/examples$ ./demo-rx.py
```

Then run the following to grab and save these messages:

```text
blockstream-satellite/api/examples$ ./api_data_reader.py --plaintext
Waiting for data...

[2019-02-04 23:22:42]: Got    2135 bytes        Saving as plaintext
Saved in downloads/20190204232242.
[2019-02-05 02:57:25]: Got    1024 bytes        Saving as plaintext
Saved in downloads/20190205025725.
```

Open the saved plaintext files to read the messages!

{% hint style="info" %}
If messages are encrypted, the saved text will be unintelligible. Only unencrypted plaintext messages, like those sent via spacebit.live, will be readable!
{% endhint %}

## Set up a Satellite Dish

Yes, this is a thing that you can do!  Requires ~$200 worth of equipment and quite a bit of technical expertise.

{% embed url="https://www.drgoss.org/\#h.p\_\_lWCP0Nx-gXF" %}

{% embed url="https://twitter.com/notgrubles/status/1091011511961731073" %}

## Things People Have Sent

Somebody has been using the satellite to blog:

{% embed url="https://twitter.com/adam3us/status/1088907796794490881" %}

Pavol Rusnak, CTO of SatoshiLabs \(creatos of the Trezor [hardware wallet](../../lightning-technology/research/hardware-wallets.md)\), even used the Blockstream satellites to relay the [Lightning Torch](lightning-torch.md):

{% embed url="https://twitter.com/pavolrusnak/status/1093568672923348997" %}

## News

{% embed url="https://bitcoinmagazine.com/articles/blockstream-satellites-now-cover-asia-pacific-send-messages-lightning/" %}



