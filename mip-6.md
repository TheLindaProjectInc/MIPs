# MIP-6 : Governance Subsidy Winner Correction

```
Number:  MIP-6
Title:   Governance Subsidy Winner Correction
Type:    Standard
Status:  Final
Authors: nibbles <keith@metrixcoin.com>
         seqSEE <sarah@sqdmc.net>
         squidicuz <squid@sqdmc.net>
Created: 2023-05-25
```

## Abstract

This MIP is a proposal to remove legacy code in MetrixCore used to process governor subdidies. [MIP5](/mip-5.md) will introduce the DGPv3 which eliminates the issues that code was put into place to remedy. This MIP should be dependent on MIP5 passing because of this.

## Motivation

Previous versions of the Governance contract have had issues with selecting a current valid subsidy winner. With the upgrades to DGPv3, legacy code put in place to choose the governance subsidy winner could be removed, allowing less resources to be used by the nodes. Additionally this will allow less risk to forks due nodes choosing different governance winners.

## References
[MIPs Discussions](https://github.com/TheLindaProjectInc/MIPs/discussions/2)

[DGPv3](https://github.com/TheLindaProjectInc/metrix-dgp/blob/dgpv3/contracts/Governance.sol#L308-L309)

#### Metrix Core
 - [Legacy code disable 1](https://github.com/TheLindaProjectInc/Metrix/blob/1612283b7f808b76207cd7a9896694fce396f1b5/src/qtum/qtumDGP.cpp#L245)
 - [Legacy code disable 2](https://github.com/TheLindaProjectInc/Metrix/blob/1612283b7f808b76207cd7a9896694fce396f1b5/src/qtum/qtumDGP.cpp#L290)
 - [New winner lookup](https://github.com/TheLindaProjectInc/Metrix/blob/1612283b7f808b76207cd7a9896694fce396f1b5/src/qtum/qtumDGP.cpp#L375)
