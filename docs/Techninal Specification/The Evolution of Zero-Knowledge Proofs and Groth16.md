# The Evolution of Zero-Knowledge Proofs and Groth16

### Historical Background
- **1985**: Goldwasser, Micali, Rackoff introduce Interactive Zero-Knowledge Proofs
- **1990s**: Schnorr Identification, Fiat–Shamir Heuristic
- **2010s**: zk-SNARKs enable non-interactive, succinct proofs

**Core properties:**
- **Completeness** – true statements always verify
- **Soundness** – false statements cannot be proven
- **Zero-Knowledge** – no private data is revealed

### Groth16 (2016)
Reference: [Jens Groth, On the Size of Pairing-based Noninteractive Arguments](https://www.ee.iitb.ac.in/~sarva/zk/groth16.pdf)

**Key properties:**
- **Proof size** ≈ 192–256 bytes (encoding-dependent)
- **Verification** reduces to one multi-pairing equation invoked through a single `bn254Pairing` precompile call
- **QAP (Quadratic Arithmetic Program)** representation of circuits
- **Trusted setup** required once per circuit

Used by Zcash, Filecoin, TornadoCash, and other zkSNARK systems.

### Significance and Trade-offs
Groth16 established the first industry-grade zk-proof scheme balancing speed, succinctness, and practicality. While foundational, the limitations of its circuit-specific trusted setup (requiring a new setup for every circuit change) led to the development of more flexible and scalable systems like PLONK, which ILITY predominantly utilizes for its dynamic environment.

**Primary advantages:**
- **Succinctness**: Proofs are extremely small (typically under 200 bytes), minimizing on-chain storage and transmission costs.
- **Fast Verification**: Verification is exceptionally fast, as it primarily involves a constant number of pairing operations, making it gas-efficient on EVM-based chains.

**Main limitation:**
- **Circuit-Specific Setup**: A unique, trusted setup ceremony is required for each and every circuit. If a developer needs to change the logic of the circuit, even slightly, a completely new setup process must be initiated. This lack of flexibility makes it cumbersome for systems that require frequent upgrades or support for a wide variety of proof types.
