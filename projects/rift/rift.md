 # Rift by [Rift Research](https://github.com/riftresearch)

**Summary:** Protocol for trustless swaps between Bitcoin and Ethereum

**Team Members:** Alpinevm([GitHub](https://github.com/alpinevm), [Twitter](https://x.com/alpinevm)), Bruidbarrett([GitHub](https://github.com/bruidbarrett), [Twitter](https://x.com/eth_tristan)), Basedcrypto([GitHub](https://github.com/sameesiddiqui), [Twitter](https://x.com/basedcrypto__))

**Repo Link:** [Rift protocol](https://github.com/riftresearch/protocol)

**Additional Resources:** 
- [Site](https://www.rift.exchange/)
- [Whitepaper](https://www.rift.exchange/whitepaper.pdf)
- [Video demo](https://x.com/riftdex/status/1842242143005614489)

---
## Problem

There's no trustless way to swap assets between Bitcoin and EVM chains.

This is because message passing is hard. A standard light client runs all the code to verify Bitcoin blocks in smart contracts, making it very expensive. Other solutions such as alt L1s or synthetic Bitcoins are highly centralized and far less secure than the native chains.

## Solution

A ZK light client solves this problem. It allows us to verify arbitrary Bitcoin state transitions for <700k gas. While this has been theoretically possible, in practice it has been very difficult to build complex, production ready ZK protocols due to the complexity of zkDSLs and circuit programming.

ZKVMs like SP1 make it 100x easier to build ZK protocols like ours.

## Performance Metrics

*Cycle count to prove 3 Bitcoin blocks:* **3.9m**

*Cycle count to prove 73 blocks (12 hours worth of blocks):* **5.4m**

*Cost of a swap (best case):* **625k gas** ($0.01 - $0.03 on Arbitrum)

*Cost of a swap (worst case):* **5.3m gas** ($0.10 - $0.30)
