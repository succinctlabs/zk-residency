# Sorella Log Verifier by Philogy from Sorella

**Summary:** Non-excluding verification of past contract events.

**Team Members:** Philogy ([GitHub](github.com/Philogy), [$\mathbb{X}$](x.com/real_philogy))

**Repo Link:** [Repo Link](https://github.com/Philogy/sp1-log0-summer)

**Additional Resources:** -

---
## Problem

Want to save gas on state updates that are not latency update. In our case collection & accounting
of validator rewards.

## Solution

- instead of a bunch of storage slot updates every block we emit a summary hash
- we can the prove the list of summary hashes via SP1 by proving the events from our contract via
SP1 (prove hash chain => prove receipt trie in relevant blocks)
- prove content of summary hash => sum
- commit to final sum within the program 

## Performance Metrics

1.4M cycles / block to be proven on average. Still a WIP and unoptimized.
