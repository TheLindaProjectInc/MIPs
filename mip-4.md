# MIP-4 : MIP Upgrade Activation Time

```
Number:  MIP-4
Title:   MIP Upgrade Activation Time
Type:    Standard
Status:  Draft
Authors: nibbles <keith@metrixcoin.com>
         seqSEE <sarah@sqdmc.net>
         squidicuz <squid@sqdmc.net>
Created: 2023-05-25
```

## Abstract

This MIP corrects the BIP9 activation time to be `~1 week` rather than `~2 days`. 

## Motivation

BIP9 is a Bitcoin standard and takes ~1 week to activate. The difference in blocktime between Bitcoin and Metrix was not considered when this was implemented, so it should be corrected. 

This will ensure that future BIP9 activations happen in the expected amount of time which is more reasonable for holders and miners. 

## Upgrade BIP9 System
### Update consensus.nRuleChangeActivationThreshold
Currently `nRuleChangeActivationThreshold` which is a number of blocks is set to `1916`. It will be changed to `6384` to be 95% of the blocks in approximately 1 week ((960 * 7 * 95) / 100).

### Update nMinerConfirmationWindow
Currently `nMinerConfirmationWindow` which is a number of blocks is set to `2016`. It will be changed to `6720` to be approximately 1 week (960 * 7).

## References
[bip-0009](https://github.com/bitcoin/bips/blob/master/bip-0009.mediawiki)

[Bitcoin Core](https://github.com/bitcoin/bitcoin/blob/25202cace9140870c75cb3a811e10045df88c226/src/kernel/chainparams.cpp#L93-L94)

