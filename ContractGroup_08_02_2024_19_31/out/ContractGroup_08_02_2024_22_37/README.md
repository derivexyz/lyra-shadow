# Description

This shadow group modifies the Portfolio Margin Manager to emit the "trustless" and "trusted" risk assessor results. 

To improve throughput, the lyra orderbook only tests most critical (3 of 27) risk scenarios for every trade, thus increasing throughput by 9x. Although the this reduced set of scenarios is enough to prevent any attacks on the solvency of the protocol, showing what would've been the "trustless" margin of the account will greatly increase the confidence in the "solvency" and "risk" of the Lyra Protocol. 

# Functional Overview

The lib.getMarginAndMarkToMarket() risk assessment is run multiple times but with the "full set of trustless" scenarios.

This would otherwise be impossible to do on chain due to gas limitations. Backwards calculating the same values is an extremely cumbersome process the exact solidity business logic would need to be replicated in Python / JS. Furthermore, the results would never exactly match what would have happened on-chain. 

# Coverage

Only the PMRM.sol contracts is modified

# Simulation 

Sample transaction with PM
```bash
cd ContractGroup_08_02_2024_19_31
shadow sim 0xcde1b5f14b489c5ea2fe7e02fb3c8cf25d533a2e735b855aa8106d094a7e6d65 --rpc-url https://rpc.lyra.finance
```