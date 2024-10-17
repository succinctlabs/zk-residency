# OpenPassport by [OpenPassport](https://openpassport.app)

**Summary:** Zero-knowledge passport proofs

**Team Members:** Rémi ([GitHub](github.com/remicolin), [$\mathbb{X}$](x.com/rems000)), Florent ([GitHub](github.com/0xturboblitz), [$\mathbb{X}$](x.com/turboblitzzz))

**Repo Link:** [Monorepo](https://github.com/zk-passport/openpassport), [SP1 implementation](https://github.com/zk-passport/spartan-sp1)


---
## Problem
In order to verify passports data integrity and signature, we need to perform several hash functions and signature verification (RSA/RSAPSS/ECDSA).
Using groth16 leads to too heavy zkey and proving time, so we are aiming to switch to spartan. Unfortunately, spartans' proofs are not succinct.

## Solution
Because SP1 already has a pipeline ready for groth16 wrapping, we tried proving Spartan in SP1. This avoids the need to implement a circom circuit verifying Spartan in circom. We tried verifying Spartan with Bn254, curve25519-dalek and secp256k1


## Performance Metrics
| **Curve** | **8192 constraints**, **~12.6kb proof** |
| --- | --- |
| Bn254 | 4.5B |
| curve25519-dalek | 854 293 255 cycles |
| secp256k1 | 984 149 042 cycles |

We're working with the Succinct team at their residency to see how we can use precompiles to make verification lighter. Right now the cycle count is too high to picture a proof being made for each user (proving time is at least minutes for such a high cycle count).
