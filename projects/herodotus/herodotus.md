# Herodotus Data Processor in SP1

**Summary:** [Run computation over provably historical onchain data from SP1]

**Team Members:** Pia ([GitHub](https://github.com/rkdud007), [Twitter](https://x.com/piapark_eth)), Bartosz ([GitHub](https://github.com/Okm165), [Twitter](https://x.com/bartolomeo_diaz)), Marcello ([GitHub](https://github.com/marcellobardus), [Twitter](https://x.com/0xmarcello))

**Repo Link:** [https://github.com/HerodotusDev/hdp-sp1]

**Additional Resources:** [HDP Docs](https://docs.herodotus.dev/herodotus-docs/developers/data-processor)

---

## Problem

While zkVMs allow developers to shift the paradigm from execute offchain and verify onchain, developers still get the responsibility of designing their program such that it is able to injest onchain data, while this isn't particularly hard they will quickly face one limitation which is the inability to access historical data such as Ethereum block headers, receipts, state etc.
HDP-SP1 is a library for SP1 which bridges that gap and ensures soundness is preserved.

## Solution

We implemented in SP1 the following primitives:

- [Header proof verification](https://docs.herodotus.dev/herodotus-docs/protocol-design/historical-block-hash-accumulator)
- Ethereum blockhash decommitment logic
- State proof verification
- Consensus layer header verification
  On top of that we develop an SDK that allows to fetch preauthenticated data and use it from the "guest" programs.

![Diagram](https://github.com/marcellobardus/zk-residency/blob/main/.github/herodotus_diagram.png?raw=true)

## Performance Metrics

| Operation                      | Clock Cycle |
| ------------------------------ | ----------- |
| **Header Verification**        | 626,077     |
| **MPT Verification**           | 78,851      |
| **Beacon header Verification** | ~100k       |
| **Bloom Filter (Set)**         | 17,656      |
| **Bloom Filter (Check)**       | 20,119      |
