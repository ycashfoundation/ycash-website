---
title: "Diversified Addresses"
canonical_url: "https://y.cash/fact-sheet"
---

# Diversified Addresses

## What are diversified addresses?
Diversified addresses are a feature of Sapling addresses that let you generate multiple Sapling addresses from the same private key. That is, a single Sapling spending or viewing key can create 1000s of Sapling addresses. These addresses are called "diversified addresses".

Diversified addresses are indistinguishable from regular addresses. In addition, they are also unlinkable&mdash;that is, it is not possible to identify two addresses as diversified, without having access to their private keys.

## What are the uses for diversified addresses?
Generally, it is a good idea to hand out a unique address to each party you are transacting with, so that even if they collude, they will not be able to link all your addresses together. For example, you might want to give out a different address to each exchange you interact with.

While you can generate regular addresses, each time you generate a new address, you need to take care to backup its private key.

This process is especially problematic if you are using an address from a paper wallet, as it might be too expensive or time consuming to generate a new paper address.

With diversified addresses, you can simply generate a new address each time you want to give someone your Sapling address, without having to worry about backing up the private key.

## How do I use diversified addresses?
ycashd 2.0.6 introduces two new RPC calls to manage diversified addresses. `z_getnewdiversifiedaddress` and `z_getalldiversifiedaddresses`.

#### `z_getnewdiversifiedaddress`
This RPC call will generate a new diversified address from an existing Sapling address. Remember that both of these addresses will share the same private key (both spending key and viewing key).

```
$ ./ycash-cli z_getnewdiversifiedaddress ys179dzraxjvg9hhsdny0582v4ngrmh9fgmdnwq7rcnessfdfcsktyxshzzjpjvdyslkchnqnxfnml

ys16eu760jpej3keda4crmcmsj3ef2wyrfj7uy8gd9qrzfwfwrggjnevnf75ywer59gqwes7l7mtnw
```

This will generate a new address that shares the same private key as the address you supplied, and will add the new address into your wallet.

#### `z_getalldiversifiedaddresses`
This RPC call will get all the diversified addresses that the given address is associated with. You can call this RPC call with any sapling address, and it will return all the other addresses in the wallet that share the same private key with the given address. That is, it will return all the diversified addresses associated with the given address.

```
$ ./ycash-cli z_getalldiversifiedaddresses ys179dzraxjvg9hhsdny0582v4ngrmh9fgmdnwq7rcnessfdfcsktyxshzzjpjvdyslkchnqnxfnml
[
  "ys1k33cd4r4jm44fvzypdtq970k555jlpeq483xdj8h7km3gg6lnpdm24pctq7evhnkwuptvy57z6v",
  "ys179dzraxjvg9hhsdny0582v4ngrmh9fgmdnwq7rcnessfdfcsktyxshzzjpjvdyslkchnqnxfnml"
]
```

Note that diversified addresses don't have a "master" address or "sub-addresses". All of them are peer addresses associated with the same private key. Which means you can call `z_getalldiversifiedaddresses` with any of the diversified address to get the full set of diversified addresses that share the same private key.

## What are the Pros and Cons of using diversified addresses?
#### PROs
- Generate essentially an infinite number of addresses from the same private key
- No need to backup private keys when generating new diversified addresses
- Makes it easy to give each party you inteact with a new address

#### CONs
- All the diversified addresses share the same private key, so you can't for example, disclose the viewing key for just one address. If you give out the viewing key for one addresses, all the diversified addresses associated with that key will become visible.
- In the event that zk-SNARKs (the technology underlying Sapling shielded addresses) are ever broken, an attacker might be able to craft some interactive attacks which may make it possible to link together diversified addresses. There is a plan to address this in future releases. Please see: [Zcash Issue #3719](https://github.com/zcash/zcash/issues/3719).
