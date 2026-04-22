# pcn-complexity

Graph-theoretic complexity scoring on protein contact networks

## Motivation

Protein folding rate varies by orders of magnitude across single-domain proteins.
Wang & Panagiotou (2022) show that folding rate correlates with the global topological complexity of the native state, as measured by the second Vassiliev measure $v_2$.
This repo investigates whether graph-theoretic descriptors on protein contact networks (PCNs) 
capture similar structural information as $v_2$ and how strongly they correlate with experimental folding rates.

## Approach

1. Parse alpha carbon backbone from PDB structures
2. Construct a contact graph $G = (V, E, W)$ with threshold-based edges and Gaussian distance weights
3. Compute spectral and topological complexity scores: Fiedler value, spectral gap, clustering coefficient, weighted contact order
4. Design a composite complexity score $\mathcal{C}(G)$ 
5. Correlate $\mathcal{C}(G)$ against experimental $\ln(k_f)$ and benchmark against the $v_2$ baseline from Wang & Panagiotou (2022)

## Dataset

Ground truth folding rates are drawn from two published curated datasets:

- **Maxwell et al. (2005)** — a standardized kinetic dataset of two-state single-domain proteins
- **Broom et al. (2015)** — extends coverage to multi-state proteins

These are the same datasets used in Wang & Panagiotou (2022), allowing direct comparison against their reported correlations.

PDB structures are fetched programmatically via BioPython's `PDBList` using the PDB IDs from the above datasets.
Experimental $\ln(k_f)$ values are stored locally in `data/folding_rates.csv`.

### `data/folding_rates.csv` format

```csv
pdb_id,ln_kf,kinetics
1VII,4.10,two-state
1l8w,0.80,two-state
1qop,1.20,multi-state
...
```

The `kinetics` column distinguishes two-state from multi-state proteins, as the paper reports meaningfully different correlations for each subset.
