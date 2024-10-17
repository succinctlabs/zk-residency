# ZKpassport

**Summary:** Anynomous and unforgeable proof of identity using government-issued passports and ID cards.

**Team Members:** Michael Elliot ([GitHub](https://github.com/michaelelliot), [Twitter](https://x.com/michaelelliot)), Théo Madzou ([GitHub](https://github.com/madztheo), [Twitter](https://x.com/madztheo))

**Repo Link:** [https://github.com/zkpassport](https://github.com/zkpassport)

---

## Problem

[Describe the problem that you were working on]

## Solution

[How did you solve your problem, what did you use SP1 for?]

## Performance Metrics

**Passport verification**

RSA 2048-bit signature verification with data integrity check using three SHA-256 and some basic array manipulations:

- **Cycles:** ~1.8 millions
- **Proof generation time:** ~2 minutes on a MacBook Pro M1 Max
- **RAM:** up to 13GB
