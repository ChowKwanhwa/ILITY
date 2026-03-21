# PLONK and Plonkish Architectures

### Overview
PLONK (2019, Ariel Gabizon, Zachary Williamson, Oana Ciobotaru) introduced a universal setup SNARK:
“Permutations over Lagrange-bases for Oecumenical Non-interactive Arguments of Knowledge” 📄 [PDF](https://zkdl-camp.github.io/files/slides/12-plonk-arithm.pdf)

### Core Components & Key Advantages
PLONK's primary innovation is the universal and updatable trusted setup. Unlike Groth16, a single trusted setup ceremony can be performed once and then be used for any number of circuits, regardless of their logic or updates. This dramatically improves flexibility and scalability for evolving protocols like ILITY.

Its architecture is built on these components:
- **Permutation Arguments**: Ensures that the values on the "wires" of a circuit are consistent. It proves that one set of wires is a valid permutation of another, effectively confirming that the output of one gate is correctly passed as the input to the next.
- **Polynomial Commitments (KZG)**: Provides compact and easily verifiable commitments to the polynomials that represent the circuit's logic. This is the cryptographic foundation for the proof's succinctness.
- **Custom Gates & Lookup Tables**: PLONK is highly flexible. It allows the creation of "custom gates" to optimize specific, repeated computations far more efficiently than standard arithmetic gates. "Lookup tables" allow the circuit to prove that a value is part of a predefined set, which is highly effective for operations like range checks.

### Plonkish Extensions
- TurboPlonk / UltraPlonk / Halo2
- Support for IPA/KZG commitments and custom gates
- Integration with rollups and zkVMs

### Aztec’s Contribution
The Aztec Protocol co-developed PLONK and built Noir & UltraPlonk ecosystems for private transactions.
- [Aztec Research Hub](https://aztec.network/research)
