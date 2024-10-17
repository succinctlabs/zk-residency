![ZKpassport](https://github.com/user-attachments/assets/f2cede30-ca36-4a32-9c3f-5b12b55b97d3)

**Summary:** Private and unforgeable proof of identity using government-issued passports and ID cards.

**Team Members:** Michael Elliot ([GitHub](https://github.com/michaelelliot), [Twitter](https://x.com/michaelelliot)), Théo Madzou ([GitHub](https://github.com/madztheo), [Twitter](https://x.com/madztheo))

**Repo Link:** [https://github.com/zkpassport](https://github.com/zkpassport)

---

## Problem

Current identity verification systems rely heavily on centralized databases and leak personal information, posing privacy risks. Traditional KYC processes collect sensitive data, leading to custodial risks and increased exposure to identity theft. This results in a lack of privacy and security for users, and isn't congruent with the ethos of Web3 and blockchain technology.

## Solution

ZKpassport offers a privacy-first identity verification solution that leverages zero-knowledge proofs. By using a government-issued electronic passports and ID cards, users can privately verify their identity while selectively revealing only the necessary information.

Our core stack relies primarly on Noir and Barretenberg from Aztec, but during the residency, we also implemented a simple Rust version of it and used [Succinct’s SP1 prover](https://github.com/succinctlabs/sp1) to generate similar proofs.

## Performance Metrics

**Passport verification**

RSA 2048-bit signature verification with data integrity check using three SHA-256 and some basic array manipulations:

- **Cycles:** ~1.8 million
- **Proof generation time:** ~2 minutes on a MacBook Pro M1 Max
- **RAM:** up to 13GB
