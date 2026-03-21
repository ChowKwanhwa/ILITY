# Multi-Chain Asset Aggregation via ZK Circuits

### Definitions
- **Chains**: $\mathcal{C} = \{C_1, C_2, ..., C_m\}$
- **Wallets**: $A^{(j)} = \{a^{(j)}_1, ..., a^{(j)}_{n_j}\}$
- **Cluster**: $\mathcal{K} \subseteq \bigcup_j A^{(j)}$ (linked by DID $D$)

### Circuit Formulation
$$ \text{leaf}^{(j)}_{i,t} = \mathsf{Commit}\big(\mathrm{chainId}^{(j)},\, t,\, a^{(j)}_i,\, \text{bal}^{(j)}_{i,t},\, \mathrm{salt}^{(j)}_{i,t}\big) $$

Output proof:
$$ \pi = \mathsf{ZKProof}(S_t, D, \{R^{(j)}\}) $$

### Interpretation
DID $D$ privately owns multiple wallets across chains, whose total asset $S_t$ is verifiable against each chain’s root $R^{(j)}$.

**Notes:**
- **Domain separation**: include `chainId`, token identifier `t`, and per-leaf `salt` in commitments to prevent collisions and linkability.
- **Bounded sums**: if consumers require 64/128-bit totals, include range/overflow constraints in-circuit so that $S_t$ is safe outside the field modulus context.

### Aggregation
- Each chain’s sub-proof $\pi^{(j)}$ is recursively aggregated into a single proof $\Pi$.
- ILITY Verifier validates $\Pi$.
- Gas cost minimized using EIP-1108 optimization.
