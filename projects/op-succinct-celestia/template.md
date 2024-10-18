# OP Succinct by [Team Name]

**Summary:** Enabling Celestia DA for chains using OP Succinct

**Team Members:** Diego Ferrer ([GitHub](https://github.com/Ferret-san/kona/commit/d630aac863321447d4b7a05a7df9d4d31a1565b4), [Twitter](https://x.com/dferrersan)),

**Repo Link:** [Repo Link](https://github.com/Ferret-san/kona/tree/kona-providers-v0.0.1-altda)

**Additional Resources:** [Slides](https://docs.google.com/presentation/d/18Ig6FFuSnn3kIoFqF-H-E6k_mNF98N4gTcNBdDTpfe0/edit?usp=sharing)

---

## Problem

While OP Succinct enables OP Stack based rollups to become ZK rollups, the cost and throughput of Ethereum DA is still an issue. In order to enable higher throughput at a reasonable cost, Validiums are needed.

## Solution

In order to enable Validiums (zk rollups with offchain DA) for OP Succinct, I worked on implementing an AltDA Client for Kona, the rust library for OP that is used by OP Succinct to generate proofs. By incorporating this implementation into the derivation pipeline and some additionaly verification logic, rollups can leverage OP Succinct x Celestia for both fast finality and scalability.

## Performance Metrics

TBD (Since current version does not perform additional verification for data inclusion, any benchmark would be similar to the current ones for OP Succinct)
