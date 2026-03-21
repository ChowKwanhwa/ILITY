# ZK Data Bridging and Verification

### Concept
ILITY aggregates and verifies ZK proofs and state roots from external blockchains (Arbitrum, zkSync, Optimism) via zk-bridging, transforming them into ILITY-standardized proofs.

### Data Extraction

| Chain | Type | Data Source |
| :--- | :--- | :--- |
| Arbitrum | Optimistic Rollup | L1 calldata (or blobs, where applicable) for batch roots |
| zkSync | zkRollup | ZK-SNARK validity proofs |
| Optimism | OP Stack | Finalized output roots; FPVM artifacts (where available) |

### Bridging Frameworks

**OmniBridge / AMB**
- Arbitrary Message Bridge reference.
- Handles cross-chain data payloads and callbacks.
- **Trust model**: relies on relayer/validator sets; not an on-chain light client. Applications must account for bridge security when accepting payloads.
- [Gnosis OmniBridge Docs](https://docs.gnosischain.com/bridges/token-bridge/omnibridge)

**LayerZero**
- Oracle + Relayer model ensures dual consensus on message validity.
- Supports OApp integration for on-chain verification.
- **Trust model**: security depends on the chosen Oracle/Relayer set and app configuration; not a trustless light client. Use with explicit threat-modeling.
- [LayerZero Docs](https://docs.layerzero.network/)

### Data Verification Flow
1. **Extraction**: collect L2 state roots and proofs.
2. **Transmission**: send payloads to ILITY via AMB or LayerZero.
3. **Storage**: publish as EIP-4844 blob for data availability (contracts retain only the commitment hash).
4. **Verification**:
    - zkRollup → verify validity proof.
    - Optimistic → verify finalized output roots; optionally accept FPVM proof artifacts depending on chain maturity.
5. **Indexing**: commit verified Merkle roots to ILITY registry.
