# MIP-2 : Goverance Subsidy Correction

```
Number:  MIP-2
Title:   Goverance Subsidy Correction
Type:    Standard
Status:  Final
Authors: nibbles <keith@metrixcoin.com>
         seqSEE <sarah@sqdmc.net>
         squidicuz
Created: 2022-12-06
```

## Abstract

This MIP is a proposal to exclude a misbehaving governor `a66268b3c8a9501e492f81abdd81655ee41e35d2` from getting rewards.

## Motivation

The DGPv1 contracts did not handle contracts as governors properly so when `a66268b3c8a9501e492f81abdd81655ee41e35d2` was enrolled as a governor it created a subsidy error resulting in a governor reward being created every block, which would be sent to the staker instead of a governor. 

## Implications of not blocking the bad governor 

Without skipping this bad governor it would remain in the front of the reward queue, creating excess MRX and preventing other governors from recieving a reward.
