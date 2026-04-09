# Pattern Recognition in Discrete Twisted Lattices: A Descriptive Study of Scaling Behavior and Finite-Size Effects

**Author:** Dr. Katharina Jacoby  
**Date:** April 9, 2026  
---
>Publication Note: This manuscript serves as a formal correction and refinement of the preliminary report *Pattern Recognition in Discrete Twisted Lattices: A Descriptive Study of Scaling Behavior and Finite-Size Effects* (Jacoby, March 2026). 
---

## Abstract

This manuscript documents a re-evaluation of numerical scaling behaviors in discrete photonic lattices with anti-periodic boundary conditions ("twists"), serving as a descriptive update to the preliminary report (Jacoby, March 2026). In the initial study, we noted a transition from finite-size deviation to a stable regime, with apparent "perfect" mathematical constants emerging for the Klein Bottle topology. However, the lack of a corresponding clear ratio for the Twisted Torus prompted a deeper investigation into potential numerical artifacts.

Using a high-resolution binary search (tolerance $10^{-8}$), we observed that the previously reported "perfect" constants were likely artifacts of grid quantization in lower-resolution scans, arising from the alignment of the search grid with specific data points. The refined numerical data indicates that the critical curvature $K_c$ does not scale continuously with lattice length $L$, but rather exhibits a step-wise dependence on $\lfloor L/2 \rfloor$. Within the tested range ($N=4$ to $N=1024$), this pattern yields stable products for both topologies, with the Klein Bottle exhibiting a ratio of approximately $\sqrt{2}$ relative to the Twisted Torus. 

It is important to note that these findings are numerical observations specific to the Discrete Coupled Mode Equation (CME) framework tested. No analytical proof is provided for the $\lfloor L/2 \rfloor$ dependence or the $\sqrt{2}$ ratio. This work aims to document the sensitivity of discrete topology studies to numerical resolution and to propose $\lfloor L/2 \rfloor$ as a candidate descriptor for the effective resolution of twisted boundaries, pending further theoretical derivation and verification at larger scales.

---

## 1. Introduction

In continuous field theory, the critical curvature $K_c$ of a toroidal manifold is theoretically expected to scale inversely with the characteristic length $L$ ($K_c \propto 1/L$). When such a field is instantiated on a discrete grid, the interaction between the grid geometry (Manhattan or Euclidean metric) and the global topology (the twist) introduces complexities that are not present in the continuous limit.

This study addresses a descriptive question: **How does the critical curvature $K_c$ numerically behave as the number of nodes $N$ increases, and does this behavior depend on the lattice dimension $L$ or a derived quantity?**

Crucially, this manuscript also serves as a record of the numerical verification process. Initial observations of "perfect" constants in the March 2026 report prompted a re-examination of the search algorithms. This re-evaluation led to the identification of grid quantization artifacts and the subsequent documentation of a more complex, yet consistent, numerical pattern.

---

## 2. Methodology

### 2.1 Model and System
*   **Framework:** Discrete Coupled Mode Equations (CME).
*   **System:** 2D Square Lattice with nearest-neighbor coupling.
*   **Topologies:**
    *   **Twisted Torus:** Anti-periodic boundary in one dimension ($x$).
    *   **Klein Bottle:** Anti-periodic boundary in both dimensions ($x, y$).

### 2.2 Numerical Precision and Artifact Detection
A central component of this study was the verification of numerical stability through iterative refinement.
1.  **Initial Scan:** Linear scans with coarse steps (0.05 for Klein Bottle, 0.01 for Torus) were performed. These scans yielded values that appeared to match "perfect" rational constants.
2.  **Re-evaluation:** Suspecting that the coarse search grid might be inducing quantization artifacts, we implemented a **two-stage binary search** with a tolerance of $10^{-8}$.
3.  **Observation:** The "perfect" constants disappeared upon high-resolution scanning, shifting to values with slight, non-zero drifts. This suggests that the initial results were numerical coincidences resulting from the search grid snapping to specific points, rather than exact physical constants.

**Note:** All results presented in this paper are derived from the high-resolution binary search method to minimize grid-induced bias.

### 2.3 Metrics
*   **Observed Critical Curvature ($K_c$):** The coupling strength where the system transitions from static to oscillatory (defined as Min_Rho < 0).
*   **Theoretical Target ($K_{target}$):** $K_{target} = 4\pi/L$.
*   **Correction Factor ($\alpha$):** $\alpha = K_c / K_{target}$.
*   **Scaling Product ($P$):** $P = K_c \times \lfloor L/2 \rfloor$.

---

## 3. Observations

### 3.1 The $\lfloor L/2 \rfloor$ Dependence
The high-resolution data indicates that $K_c$ does not vary continuously with $L$, but appears to remain constant for pairs of lattice sizes that share the same value of $\lfloor L/2 \rfloor$.

**Table 1: Paired $K_c$ Values (High-Resolution)**
| L | $\lfloor L/2 \rfloor$ | $K_c$ (Klein Bottle) | $K_c$ (Twisted Torus) |
|---|---|---|---|
| 2 | 1 | 1.1107207 | 0.785571 |
| 3 | 1 | 1.1107207 | 0.785571 |
| 4 | 2 | 0.5553604 | 0.392811 |
| 5 | 2 | 0.5553604 | 0.392811 |

**Observation:** Adjacent lattice sizes with identical $\lfloor L/2 \rfloor$ values yield $K_c$ values that are identical within the limits of numerical precision ($10^{-8}$). This suggests that, numerically, the effective resolution of the twist boundary is determined by the integer floor of half the side length.

### 3.2 Product Stability and Drift
The product $P = K_c \times \lfloor L/2 \rfloor$ appears to stabilize to a near-constant value for each topology within the tested range.

| Topology | Product $P$ (High-Res) | Stability Observation |
|---|---|---|
| **Klein Bottle** | $1.1107207 \pm 10^{-7}$ | Highly stable across tested $N$ |
| **Twisted Torus** | $0.7856 \pm 10^{-3}$ | Minor drift observed at larger $N$ |

### 3.3 The Ratio Between Topologies
The ratio of the scaling products between the two topologies consistently approximates $1.414$.

$$ \frac{P_{KB}}{P_{Torus}} \approx 1.414 \approx \sqrt{2} $$

While the data strongly suggests a relationship to $\sqrt{2}$, it remains an open question whether this is an exact mathematical identity or a numerical coincidence specific to the CME implementation. Further simulations at $N > 1024$ would be required to assess the persistence of this ratio.

---

## 4. Discussion

### 4.1 The Nature of the "Perfect" Constants
The initial appearance of "perfect" constants ($3/5\pi$, $80/199\pi$) in the March 2026 report appears to be a cautionary example of grid quantization. The coarse search grid (step size 0.05) likely aligned with the true $K_c$ values in a manner that produced rational approximations indistinguishable from exact constants at low precision. The high-resolution re-evaluation was necessary to reveal the underlying, slightly drifting numerical behavior.

### 4.2 Interpretation of $\lfloor L/2 \rfloor$
The observed dependence on $\lfloor L/2 \rfloor$ suggests that the discrete grid "perceives" the twist boundary at a halved resolution relative to the full lattice dimension $L$. This may relate to the number of distinct distance shells available under the anti-periodic boundary condition, though a theoretical derivation is currently lacking.

### 4.3 Limitations
*   **Simulation Specific:** These observations are derived from a specific implementation of the Discrete Coupled Mode Equations.
*   **Finite Range:** The largest tested lattice size is $N=1024$.
*   **Empirical Nature:** The $\lfloor L/2 \rfloor$ dependence and the $\sqrt{2}$ ratio are currently numerical observations. They have not been analytically proven.
*   **Metric Dependence:** It is unknown whether these patterns persist under different grid metrics (e.g., Euclidean vs. Manhattan).

---

## 5. Conclusion

This manuscript documents observed numerical patterns in discrete twisted lattices, specifically a transition from finite-size deviation to a stable regime governed by $\lfloor L/2 \rfloor$.

1.  **Grid Artifacts:** Initial "perfect" constants were identified as numerical artifacts of low-resolution scanning.
2.  **Observed Pattern:** The data suggests $K_c \propto 1/\lfloor L/2 \rfloor$ within the tested range.
3.  **Ratio Observation:** A ratio of approximately $\sqrt{2}$ is observed between the Klein Bottle and Twisted Torus scaling products.

These findings are presented as descriptive records of numerical behavior. Future work should focus on deriving an analytical basis for the $\lfloor L/2 \rfloor$ dependence and verifying the $\sqrt{2}$ ratio at larger scales to determine if these patterns reflect universal properties or implementation-specific characteristics.

---

## Appendix: Data Availability

Raw simulation data supporting these observations is available in the repository accompanying this manuscript.
*   `scaling_results_klein_bottle_highres.csv`
*   `scaling_results_torus_highres.csv`

The data is provided in standard CSV format to allow for independent verification of the statistical analysis.

> **Data Availability Note:** The raw simulation data and source code are hosted in a public GitHub repository. Researchers interested in reproducing these specific results or accessing the raw data for collaborative verification are invited to use the repository.
