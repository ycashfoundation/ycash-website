# Ycash Mining Pool Implementation Details

Ycash is a chain fork of Zcash. To implement a mining pool for Ycash, the
following Ycash-specific changes need to be implemented.

## 1. Equihash Parameters
Ycash uses Equihash <192, 7>. So the mining pool code needs to update the
Equihash parameters to n=192, k=7. Note that this also includes changing the
personalization string. While the first 8 bytes of the personalization string
remains the same (“ZcashPoW”), bytes 8-12 should be updated to (little
endian)192 and bytes 12-16 should be updated to (little endian)7.

See: [https://github.com/ycashfoundation/ycash/blob/master/src/crypto/equihash.cpp#L36](https://github.com/ycashfoundation/ycash/blob/master/src/crypto/equihash.cpp#L36)

## 2. Address formats
Ycash transparent addresses begin with “s” (instead of Zcash’s “t”). So the
coinbase mining reward transaction should pay the mining reward to an “s”
address.

## 3. Founders reward
There are 2 changes:

1. At the time of the Ycash/Zcash fork in July 2019, the Zcash Founders Reward was
20% of blocks until the first block halving at block height 850,000. In contrast, the Ycash
Development Fund donation rate is 5% perpetually and is paid out to a new set
of addresses. So the coinbase "founders reward" should be updated to:
    - Pay 5% (instead of 20%)
    - Pay to vYcashFoundersRewardAddress[] ( instead of vFoundersRewardAddress[]). The
addresses rotate every  17917  blocks. See
[https://github.com/ycashfoundation/ycash/blob/master/src/chainparams.cpp#L642](https://github.com/ycashfoundation/ycash/blob/master/src/chainparams.cpp#L642)

2. Ycash Development Fund addresses are regular addresses (not multisig addresses like in
Zcash). So, if you are building the coinbase Txn manually (and not using
getblocktemplate), the coinbase output script should change from:

    Zcash:  `OP_HASH160 scriptID OP_EQUAL`

    To Ycash: `OP_DUP OP_HASH160 keyID OP_EQUALVERIFY OP_CHECKSIG`
