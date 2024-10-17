# Cali-Creds by SFLuv

**Summary:** Using California's Mobile Driver's License as On-Chain Identity

**Team Members:** PJ O'Leary (github.com/pjol, twitter.com/_pjol)

**Repo Link:** https://github.com/pjol/Cali-Creds

**Additional Resources:** Coming soon...

---
## Problem

On-chain identity is a major hurdle to overcome in bringing blockchain to the mainstream, and unlocking new worlds of use-cases. At the same time, many legacy blockchain enthusiasts are such because of the privacy promises that blockchain offers, and rightfully have concerns about what on-chain identity could mean when it comes to those promises.

## Solution

With the power of zero-knowledge, harnessed using SP1, we can have the best of both worlds: a secure, reliable, and flexible way to prove relevant information about our identities, and a way to maintain perfect privacy about irrelevant information while doing so.

## Performance Metrics

  ~30m cycles for proof generation (expecting about 10x improvement after SP1 p256 library patch)
  ~450k gas for on-chain proof verification & issuing of credential token

Which puts total cost ceiling (unoptimized and on-demand proving) at ~$10-$15 on Ethereum, 40 cents on OP, 30 cents on POL
  And total cost floor (fully optimized and at-scale proving) at ~$10-$15 on Ethereum, 10 cents on OP, less than a cent on POL
