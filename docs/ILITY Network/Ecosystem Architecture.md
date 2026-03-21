# Ecosystem Architecture

### ILITY Ecosystem Diagram

The ILITY Network architecture consists of several key layers and components:

*   **Source Chains**: Supports various networks including Ethereum Mainnet, Arbitrum, zkSync, Optimism, and other L2 solutions.
*   **Bridging Layer**: Facilitates cross-chain communication via AMB / OmniBridge, LayerZero OApp, Root Messaging, and Proof Transport.
*   **ZK Verification Layer**: Features Verifier Contracts on EVM, supporting Groth16, PLONK, and Halo2 proof systems, utilizing BN128 and KZG Precompiles.
*   **Data Availability & Indexing**: Employs Blob Storage (EIP-4844), a Proof Registry, and a State Registry with a Merkle Index.
*   **SSI Identity Layer**: Manages Self-Sovereign Identity (SSI) with ENS Mapping (contenthash) and IPFS Cluster Metadata.
*   **ZK Query & Aggregation**: Handles multi-chain asset aggregation, SSI-based policy queries, and recursive proof composition.
*   **Proof Generation & Aggregation**: Utilizes off-chain provers (Groth16 / PLONK / Halo2) with batch and recursive aggregators for cross-chain root normalization.
*   **Consumers**: Serves Wallets/dApps, DeFi integrations, and compliance/analytics platforms.
*   **Governance**: Managed through on-chain governance, circuit registries, SRS/Setup registries, and verifier versioning.

The architecture illustrates how these layers interact to provide a secure, private, and verifiable cross-chain data environment.
