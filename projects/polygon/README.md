# Polygon AggLayer

**Summary:** [1 sentence description, should mirror the description in the table]

**Team Members:** Arnau ([GitHub](https://github.com/arnaubennassar), [Twitter](https://x.com/arnau_eth)), Jesus ([GitHub](https://github.com/invocamanman), [Twitter](https://x.com/JesusLigero3)), Manav ([GitHub](https://github.com/manav2401), [Twitter](https://x.com/manav24_))

**Repo Link:** [Repo Link](https://github.com/invocarnau/succint-zk-residency)

**Additional Resources:** [AggLayer website](https://polygon.technology/agglayer)

---
## Problem

We've been PoCing a bunch of stuff that we want to add to the AggLayer soon, mostly:

- Proof Polygon PoS
- Proof OP roots posted on-chain
- Proving the bridge deployed on EVM chains
- Attaching EVM Type I using RSP
- Putting everything together: bridge from PoS (Amoy) <==> OP (Sepolia) <==> Sepolia

## Solution

Being able to generate circuits with plain Rust, makes our job incredibly easier. We would do that anyway, but it would take for ever and would be very hard to maintain and audit

