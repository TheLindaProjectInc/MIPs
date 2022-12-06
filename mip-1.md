# MIP-1 : Chain Path Correction

```
Number:  MIP-1
Title:   Chain Path Correction
Type:    Standard
Status:  Final
Authors: nibbles <keith@metrixcoin.com>
         seqSEE <sarah@sqdmc.net>
         squidicuz <squid@sqdmc.net>
Created: 2022-12-06
```

## Abstract

This MIP is a proposal which applies a chain path correction by applying checkpoints for blocks `264694` `a11eae2326f4d3162b4f3e264b38a1cdc0e0cc5c77b6319ba6f2b59bf511f6cd` and `264695` `4ebc8cc894f27303995a1b948f8b3c52b6493cd6663c70204a909474cb20ced6`.

## Motivation

Metrix Core is unable to sync from genesis due to an Address Abstraction Layer (AAL) mismatch caused by a staking reward and governor reward winners being the same address. The longest chain, which has passed both these blocks could be used to create checkpoints which do not contain the bad block.

## Checkpoints

Checkpoints are created from the longest chain for `264695` as well as 1 block before and also near the tip.

## Protocol Enforcement

Protocol will be incremented and activate once this MIP is activated. This will ensure that the consensus changes regarding a staking winner being a governor winner as well, as it causes bad consensus.
