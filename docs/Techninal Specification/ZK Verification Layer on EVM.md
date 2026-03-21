# ZK Verification Layer on EVM

### Overview
ILITY implements zk-proof verification contracts directly on the EVM. This allows EVM compatibility while enabling privacy-preserving verification.

### Architecture
- **Off-chain Prover**: Generates ZK proofs (Groth16, Plonk, Halo2) based on user data (balances, state roots, history).
- **On-chain Verifier**: Smart contract that verifies proof validity via the `alt_bn128` (BN254) pairing precompile; KZG commitments for Plonkish proofs are handled inside recursive wrappers or off-chain services until dedicated precompiles become available.
- **State Registry**: Stores verified commitments linked to a user’s DID for selective proof sharing.

### Benefits
- Full EVM compatibility (tooling, compilers, audit flows)
- Modular upgradeable verifier contracts
- Lower gas cost and lighter runtime
