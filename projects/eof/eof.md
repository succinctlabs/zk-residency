# SP1 EOF by Cairo

**Summary:** SP1 performance benchmarks for EVM Object Format (EOF)

**Team Members:** Cairo ([GitHub](https://github.com/cairoeth), [Twitter](https://x.com/cairoeth))

**Repo Link:** [https://github.com/cairoeth/sp1-eof](https://github.com/cairoeth/sp1-eof)

**Additional Resources:** N/A

---
## Problem

Currently, there are no published performance benchmarks or examples of proving EOF contracts using zkVMs.

## Solution

To benchmark EOF, we implemented a Solidity smart contract computing the `n`-th Fibonacci number mod 7919, compiled with both stable and EOF-experimental `solc` versions. Using Revm's EOF-compatible interpreter, we created two Rust programs to deploy the respective bytecodes and call the Fibonacci function. These programs were compiled to RISC-V ISA, generating ELF files. We then developed an SP1 program to consume these ELF files, prove their correct execution, and generate STARK proofs for each. Finally, we verified the deserialized proofs and public values to ensure correctness.

## Performance Metrics

EOF is roughly 3x more efficient in terms of interpreter and total phase cycles, while running 2.69x faster than the current EVM version. Moreover, the STARK proof size generated with EOF is 50% smaller. Additionally, EOF uses 96.64% fewer opcodes. Specific benchmark results can be found [here](https://github.com/cairoeth/sp1-eof?tab=readme-ov-file#results).
