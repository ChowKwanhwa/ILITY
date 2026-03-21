# Preface

ILITY Network defines a privacy-preserving verification infrastructure for multi-chain environments. It leverages Zero-Knowledge Proofs (ZKPs), Decentralized Identifiers (DIDs), and cross-chain state verification. This allows users to prove, aggregate, and monetize their data ownership without disclosing sensitive information.

This document details the technical foundation of ILITY:
- PLONK-based ZK verification layer on top of EVM
- Cross-chain data bridging and verification
- DID/ENS/IPFS-based identity clustering
- Multi-chain ZK aggregation framework

### Conventions & Assumptions
- **Curve/precompile naming**: alt_bn128 on Ethereum refers to the BN254 curve. We consistently use “BN254” (also known as alt_bn128). Groth16 verifiers on EVM typically call the BN254 pairing precompile once with a multi-pairing equation.
- **Plonkish and KZG**: Plonk/Plonkish systems commonly use KZG commitments over BLS12-381. Ethereum L1 does not currently expose BLS12-381 precompiles; KZG verification for EIP-4844 blobs occurs in consensus, while on-chain general KZG verification requires heavy contracts or is wrapped recursively into BN254-friendly circuits.
- **EIP-4844 blobs**: Blobs provide data availability, not permanent storage or on-chain readability. Contracts can reference only the `blob_versioned_hash`; blob contents must be obtained off-chain and are retained by nodes for a limited time. Long-term pinning must be handled off-chain.
- **Bridges**: AMB/OmniBridge and LayerZero deliver messages across chains but are not on-chain light clients. Security inherits each bridge’s trust model (relayers/oracles/validators); ILITY’s contracts must treat delivered payloads accordingly.
