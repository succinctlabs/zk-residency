# Solidity IBC by IBC Team

**Summary:** Peer-to-peer, trustless, light client based communication between Ethereum and any Cosmos chain using IBC.

**Team Members:** Serdar Turkmenafsar ([Github](https://github.com/srdtrk), [Twitter](https://x.com/srdtrk)), Gjermund Garaba ([Github](https://github.com/gjermundgaraba), [Twitter](https://x.com/GjermundGaraba))

**Repo Link:** [sp1-ics07-tendermint](https://github.com/srdtrk/sp1-ics07-tendermint), [solidity-ibc-eureka](https://github.com/srdtrk/solidity-ibc-eureka)

**Additional Resources:** [Tendermint Light Client Docs](https://ibc.cosmos.network/main/ibc/light-clients/tendermint/overview/)

---
## Problem

The blockchain interoperability space is dominated by trusted solutions. IBC is a light-client based protocol that enables peer-to-peer communication between blockchains. It has been difficult to implement IBC in Ethereum due to the cost of running light clients. Even the most efficient existing zk-based solutions require a middleman chain.

These difficulties have led to Cosmos chains being siloed from Ethereum.

## Solution

We use SP1 to implement a generic and cheap IBC tendermint light client in Solidity that can be used by any Cosmos chain. We also implement a Solidity IBC module that can be used by any Ethereum contract to send and receive IBC packets.

## Performance Metrics

| **Program** | **Cycle Count** |
|:---:|:---:|
| `update_client` | 7,359,764 |
| `uc_and_membership` | 7,864,196 |
| `membership` | 506,363 |
| `misbehavior` | 1M - 10M |
