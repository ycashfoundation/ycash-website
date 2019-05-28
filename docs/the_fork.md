# The Fork

## Introduction

The Ycash/Zcash fork will occur at block height 570,000 of the Zcash blockchain (approximately July 18, 2019).

This page focuses on the mechanics of the fork. For the motivations behind the fork, see ["Announcing Ycash, The First “Friendly Fork” of the Zcash Blockchain" (2019-04-11)](https://medium.com/@YcashFoundation/announcing-ycash-the-first-friendly-fork-of-the-zcash-blockchain-ac386ed6368c).

## Key Changes at Launch

At launch, Ycash implements the following key changes to Zcash:

1. The mining algorithm is changed from Equihash(200,9) to Equihash(192,7).

2. The Zcash Founders Reward rate is reduced from 20% to a perpetual 5%, with
the entirety going to the nonprofit Ycash Foundation. The Zcash Founders Reward
is renamed the Ycash Development Fund.

3. In order to eliminate confusion between Ycash and Zcash going forward, the
address formats are changed (as described in the next section).

## Ycash Address Formats

Ycash uses different address formats than Zcash, making it impossible to
accidentally send Zcash to a Ycash address (or Ycash to a Zcash address).

1. Transparent addresses start with "s1" instead of "t1".

2. Multisig addresses start with "s3" instead of "t3".

3. Shielded sprout addresses start with "yc" instead of "zc".

4. Shield sapling addresses start with "ys" instead of "zs".

## Two-Way Replay Protection

Replay attacks involve an attacker using a publicly broadcasted  transaction
on one chain to perform an unauthorized transaction on another chain.

Ycash utilizes the two-way replay protection built in to Zcash's upgrade
mechanism (first introduced in Zcash's Overwinter upgrade). Therefore, users
and exchanges need not worry about replay attacks.


## Accessing Your Ycash

### Importing Zcash Private Keys into YecWallet

In YecWallet, click on the File menu and choose "Import private key". You'll be
prompted to input your private keys, each private key on a separate line.

### Exporting Zcash Private Keys from Zcash Wallets

Make sure that your Zcash wallet allows you to export private keys. (If not, you
will not be able to access your Ycash.) Follow the instructions provided by
your ZCash wallet.

If you are using ZecWallet, click on the File menu and choose "Export all private
keys".

### Hardware Wallets

No hardware wallet has announced native support for Ycash. For a discussion of
possible options, see [this discussion on Reddit](https://www.reddit.com/r/zec/comments/bdhzbn/how_to_get_zcash_friendly_fork_ycash_on_a_trezor/?utm_source=share&utm_medium=web2x).

## Mining at Launch

### Pools

2Miners has [announced](https://twitter.com/pool2miners/status/1116370525670887425) support for Ycash mining pools, both PPLNS and SOLO. 

Bitfly has [announced](https://twitter.com/etherchain_org/status/1118458199575879680) that they will provide a Ycash pool (and Ycash explorer).

Suprnova has also [announced](https://forum.zcashcommunity.com/t/announcing-ycash-the-first-friendly-fork-of-the-zcash-blockchain/33162/41) support for a Ycash mining pool

(If this list is incomplete, contact info at ycash dot xyz and let us know.)

### Mining Software

Several different GPU mining software packages support Equihash(192,7), including:

* [Gminer](https://bitcointalk.org/index.php?topic=5034735.0) (Nvidia/AMD) (Linux/Windows) (mandatory 2% dev fee)

* [EWBF's Cuda Equihash Miner](https://bitcointalk.org/index.php?topic=4466962.0) (Nvidia) (Linux/Windows) (optional dev fee, 2% by default)

* [miniZ](https://miniz.ch/) (Nvidia) (Linux/Windows) (mandatory 2% dev fee)

* [Optiminer/Zero](https://bitcointalk.org/index.php?topic=1896901.0) (Nvida 8GB/AMD 4GB and 8GB) (Linux/Windows) (mandatory 2.5% dev fee)

* [lolMiner](https://bitcointalk.org/index.php?topic=4724735.0) (AMD) (Linux/Windows) (mandatory 1% dev fee)

(If this list is incomplete, contact info at ycash dot xyz and let us know.)
