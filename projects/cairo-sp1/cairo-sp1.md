# [Cairo-SP1] by [Danilo and Bartolomeo]

**Summary:** In the cairo SP1 project, verified a Cairo program proof in SP1, now allowing any Cairo program to generate Snark Proofs.

**Team Members:** [Danilo Kim] ([[GitHub](https://github.com/danilowhk)], [[Twitter](https://x.com/danilowhk2)]), [Bartolomeo Diaz] ([[GitHub](https://github.com/Okm165)], [[Twitter](https://x.com/bartolomeo_diaz)])

**Repo Link:** [[https://github.com/danilowhk/swiftness-sp1](https://github.com/danilowhk/swiftness-sp1)]

**Additional Resources:** [[Cairo Verifier](https://github.com/iosis-tech/swiftness)]

---

## Problem

[Today, it is expensive to verify a Cairo proof on-chain. This is because a Cairo proof requires a lot of data to be verified. For context, a proof from Starknet requires 5 million gas, costing between $100 and $500 depending on the gwei price.]

## Solution

[We ran the Cairo verifier previously implemented by Bartolomeo in SP1.]

## Performance Metrics

[We first verified a Cairo Fibonacci program, which took 800M cycles. Then we verified a ZeroSync proof, which proves the entire Bitcoin history. On our first attempt, it took 32 billion cycles to verify it. Later Bartolomeo prepared the SP1 patch of verifier utilizing the Keccak precompile, reducing the verification time to 1.3B cycles.

Lastly, we verified the Starknet OS proof, which took 3.2B cycles, reducing the cost by 3x to 40x compared to the current Ethereum L1 verification.]
