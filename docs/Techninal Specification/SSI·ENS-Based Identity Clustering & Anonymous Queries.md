# SSI·ENS-Based Identity Clustering & Anonymous Queries

### Architecture
- **DID/SSI**: Self-sovereign identity anchor
- **ENS**: Maps DID → IPFS CID
- **IPFS**: Stores encrypted wallet cluster metadata

### Workflow
1. Each wallet $a_i$ → commit $C_i = H(pk_i \,\|\, \text{salt}_i)$ using a ZK-friendly hash (e.g., Poseidon).
2. User proves “all $C_i$ belong to the same DID” via ZKP.
3. Store `{did, commitments[], metadata}` JSON on IPFS.
4. Map CID to ENS record.
5. Queries operate per-DID, not per address.
6. Results verified via zk-query proof.

### Result
DID-level privacy with verifiable ownership continuity while individual addresses remain undisclosed.
