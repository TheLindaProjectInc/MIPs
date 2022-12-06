# MIP-3 : DGP Version 2

```
Number:  MIP-3
Title:   DGP Version 2
Type:    Standard
Status:  Final
Authors: nibbles <keith@metrixcoin.com>
         seqSEE <sarah@sqdmc.net>
         squidicuz <squid@sqdmc.net>
Created: 2022-12-06
```

## Abstract

This MIP is a proposal to redefine the Budget, DGP and Governance contracts which process block rewards as well as provide and control the EVM gas schedule, block size, minimum gas price, block gas limit, transaction fee rates, governor collateral and budget fees. 

## Motivation

DGP Version 1 (DGPv1) was entered into an irrecoverable error state. Multiple vulnerabilities were also found which if exploited, could have allowed an attacker to halt the blockchain or make governance impossible.

## Issues solved in DGPv2
### Use new Solidity compiler allowing to benefit from bugfixes and optimizations
Using a newer compiler allows for any benefits that can be gained from bugfixes and optimizations made to the compiler. SafeMath will no longer be used as Solidity v0.8.0 and greater include checks for overflow by default.

### Allow both externally owned accounts and smart contracts to enroll as governors
It is not possible to determine if an EVM address smart contract in all edge cases. Allowing smart contract comes with functionality benefits to MRX holders.

- Convert transfer methods to call to allow gas forwarding
- Use msg.sender rather than tx.origin

### Fallback for failed governor subsidy reward
Failing to send a subsidy reward would irrecoverably leave the Governance contract in an error state. In the case that a governor rejects a subsidy reward it is burned by sending it to the 0x0 address.

### Fallback for failed governor collateral return
Failing to send a return of a governor's collateral would irrecoverably leave the Governance contract in an error state. In the case that a governor's collateral return is rejected, it is sent to the Budget to be potentially recovered through a budget proposal.

### Fallback for failed budget settlement
Failing to send a budget settlement would irrecoverably leave the Budget contract in an error state. In the case that a governor rejects a subsidy reward it is burned by sending it to the 0x0 address.

### Minimum and maximum values for chain parameters and fallbacks for when they are out of bounds
Setting the EVM gas schedule, block size, minimum gas price, block gas limit, transaction fee rates, governor collateral and budget fees to certain values could halt the chain and/or render the DGP contracts irrecoverably in an error state. Because external contract calls are made by the DGP contract, a check needs to be done both at the time of the propsal and also every time the value is retrieved from the external contract. 

In the case that during a proposal the value returned is out of bounds, it can not be made. 

In the case that a proposal has already passed, but later returns an out of bounds value, a defaults which match the original chain parameters are provided from the state of the DGP contract.

### Check if lastreward > 0 also when checking governor winner
If lastreward is 0, it would allow a governor to exploit the Governance contract and claim rewards unfairly. To prevent this a check was added to make sure the governor has existed for 48 hours also. 

## References

A [change to Qtum Core](https://github.com/qtumproject/qtum/pull/252) which hardcoded certain parameters was referenced to ascertain the blockchain parameter minimum and maximums. 

These changes have been implemented in the [metrix-dgp](https://github.com/TheLindaProjectInc/metrix-dgp/tree/46ed50d4114a8ffcd14e578a70c77a858e362832) contracts which were deployed to the original TestNet and confirmed to work properly.
