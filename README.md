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
5. Benchmark against the $v_2$ baseline on the two-state / multi-state dataset from Wang & Panagiotou (2022)

## Reference

Wang, J. & Panagiotou, E. (2022). *The protein folding rate and the geometry and topology of the native state.* Scientific Reports, 12, 6384. https://doi.org/10.1038/s41598-022-09924-0
