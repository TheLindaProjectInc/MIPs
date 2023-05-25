# MIP-5 : DGP Version 3

```
Number:  MIP-5
Title:   DGP Version 3
Type:    Standard
Status:  Draft
Authors: nibbles <keith@metrixcoin.com>
         seqSEE <sarah@sqdmc.net>
         squidicuz <squid@sqdmc.net>
Created: 2023-05-25
```

## Abstract

This MIP is a proposal to redefine the Budget, DGP and Governance contracts which process block rewards as well as provide and control the EVM gas schedule, block size, minimum gas price, block gas limit, transaction fee rates, governor collateral and budget fees. 

## Motivation

DGP Version 2 (DGPv2) was found to have a bug in the governance winner selection process. When new governors enroll towards the end of the rewards cycle (48 hours) the issue causes a high risk for competing forks, EVM transactions to be delayed significantly and the mempool to fill up.

## Issues solved in DGPv3

### Check if governor is mature before presenting them as the winner
If an immature governor is selected as the winner, it becomes stuck in the front of the queue. This check can be done by using the `isValidWinner` function to do the missed checks.

## References
[DGPv3](https://github.com/TheLindaProjectInc/metrix-dgp/blob/dgpv3/contracts/Governance.sol#L301-L309)
