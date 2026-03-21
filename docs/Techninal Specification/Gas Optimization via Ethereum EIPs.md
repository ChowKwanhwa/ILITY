# Gas Optimization via Ethereum EIPs

### Key EIPs

| EIP | Description | Benefit |
| :--- | :--- | :--- |
| [EIP-1108](https://eips.ethereum.org/EIPS/eip-1108) | Lowers `alt_bn128` precompile costs (ECADD 500→150, ECMUL 40000→6000, pairing base 80000→45000) | Cheaper BN254-based proof verification |
| [EIP-4844](https://eips.ethereum.org/EIPS/eip-4844) | Introduces blob storage (Proto-Danksharding) | Cheaper L2 and proof data posting |

### Implementation
- Verifier contracts invoke the `alt_bn128` pairing precompile (BN254) for Groth16-style proofs, batching points into a single call to minimize gas.
- Proof payloads and Merkle roots are published as EIP-4844 blobs for data availability; contracts persist only the `blob_versioned_hash`, while long-term storage is maintained off-chain by the prover network.
- Future upgrades track proposals such as EIP-2537 (BLS12-381 precompiles); until then, Plonkish/KZG proofs rely on off-chain verification or recursive wrapping into BN254-friendly circuits. As of 2025‑11, EIP‑2537 is not deployed on Ethereum mainnet.

### Outcome
Gas-optimized verification enables:
- On-chain proof validation at lower cost
- Efficient batch and recursive aggregation
- Economic scalability for zk-bridging applications
