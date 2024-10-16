# zkVMs Benchmarks by Stackr

**Summary:** A not so succinct comparison of zkVMs: Developer experience, Performance and Compatibility.

**Team Members:** Kautuk Kundan ([GitHub](https://github.com/kautukkundan), [Twitter](https://x.com/kautukkundan)), Aashutosh Rathi ([GitHub](https://github.com/aashutoshrathi), [Twitter](https://x.com/AashutoshRathi), Prudhvi Rampey ([GitHub](https://github.com/0xRampey), [Twitter](https://x.com/0xRampey))

**Repo Link:** [@stackrlabs/succinct-residency](https://github.com/stackrlabs/succinct-residency-exps/)

**Additional Resources:** [Slides](https://docs.google.com/presentation/d/1crZZhQaNVXXfk49cOoEMu3oPZDxsVh-hP7IFeb-PTbY/edit), [Benchmarks](https://docs.google.com/spreadsheets/d/1HwZQkgiUro9Nl30tO3KdXizB_D-1_J3vIVXbTvuY2Mw/edit)

---

## Problem

zkVMs are a new and exciting technology that can be used to build scalable and privacy-preserving applications. However, there are many zkVMs out there, and it can be hard to choose the right one for your use case. We wanted to answer the following questions:

- Which zkVMs to use for your use case?
- What are their performance characteristics?
- Which ones are ready for production use?
- How the developer experience is like for each of them?
- What are the nuances while working with them?

## Solution

<!-- [How did you solve your problem, what did you use SP1 for?] -->
We conducted a benchmarking exercise to compare the performance of zkVMs. We conducted our benchmarking on the following zkVMs with some commonly used operations with varying complexities and input sizes:

- [SP1](https://docs.succinct.xyz/)
- [RISC Zero](https://dev.risczero.com/api/zkvm/quickstart)
- [Jolt](https://jolt.a16zcrypto.com/usage/quickstart.html)
- [Delphinus](https://zkwasmdoc.gitbook.io/delphinus-zkwasm/c1_beginner/c1_quickstart)
- [Nexus VM](https://nexus.xyz/zkvm)
- [Fluent](https://docs.fluentlabs.xyz/learn/knowledge-base/the-fluent-vm)
- [Valida](https://lita.gitbook.io/lita-documentation)

And we chose the following algorithms to benchmark against:

- nth Prime
- ECDSA Verification
- BLS Verification
- BLS Aggregation
- Keccak
- Poseidon
- Merklization
- Merkle Inclusion Proof

## Performance Metrics

During this benchmarking exercise, we measured a lot of metrics. Here's a Google Sheet with all the data: [Google Sheet](https://docs.google.com/spreadsheets/d/1HwZQkgiUro9Nl30tO3KdXizB_D-1_J3vIVXbTvuY2Mw/edit)
