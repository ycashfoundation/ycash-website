# Download

## YecWallet

YecWallet is the offical Ycash wallet of the Ycash Foundation. YecWallet allows you to store, send, and receive Ycash.

For most users, YecWallet is the easiest way to join the Ycash network. (YecWallet includes a copy of ycashd, and will take care of configuring ycashd for you!)

**YecWallet v2.0.5.3 is now available!** [Download from GitHub](https://github.com/ycashfoundation/yecwallet/releases)

## ycashd

ycashd is the official Ycash node implementation of the Ycash Foundation.

Advanced users can choose to configure ycashd directly, and optionally use YecWallet with it.

**ycashd v2.0.5 is now available!** [Download from GitHub](https://github.com/ycashfoundation/ycash/releases/tag/2.0.5)

## "Bootstrap" Blockchain Download

To help users get started with running Ycash full nodes, there are two ways to speed your initial download of the Ycash blockchain.

### BitTorrent

The fastest way to obtain the blockchain is via BitTorrent:

[ycash_bootstrap_07192019.torrent](/ycash_bootstrap_07192019.torrent)

Special thanks to [Luxor Mining Pool](https://mining.luxor.tech/) for preparing this torrent.

### Zip File

For users not familiar with BitTorrent, the Ycash Foundation is making available a zip file containing blocks 1 to 564,300.

**Important Note #1: It is much better to download the torrent instead of this zip file. By using the files contained in the torrent, there is no need to index the blockchain from scratch. In contrast, if the zip file below is used, the blockchain must be indexed from scratch, which will take anywhere from a few hours to a few days depending on the characteristics the computer.**

**Important Note #2: If you have a decent connection to the internet, it will most likely be faster to sync with the network normally instead of using this zip file. This is because, for many computers setups, network speeds will exceed disk speeds. In other words, for many computers, it is faster to receive blocks over the network than it is to read the from disk.**

Zip file:

[http://downloads.ycash.xyz/download-ycash-blocks](http://downloads.ycash.xyz/download-ycash-blocks) (~15GB)

then follow these instructions:

1. Unzip the zip file:

    ```unzip ycash-blocks-564300.zip```

2. IMPORTANT: Verify the integrity of the download. From the `ycash-blocks` folder:

    Linux users, run:

    ```sha256sum -c sha256sum.txt```

    Mac users, run:

    ```gsha256sum -c sha256sum.txt```

3. Make sure that ycashd is NOT running.

4. To start importing the blocks, invoke ycashd with the --loadblock flag and the path to the first block file:

    ```./ycashd --loadblock=/path/to/ycash-blocks/blk00000.dat```

    (Note that YecWallet users using YecWallet's "embedded" `ycashd` will need to invoke the embedded `ycashd` directly.)

5. Wait for the import to finish. It will take several hours.

6. Restart `ycashd` normally.
