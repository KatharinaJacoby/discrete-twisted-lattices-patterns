# Pattern Recognition in Discrete Twisted Lattices: A Descriptive Study of Scaling Behavior and Finite-Size Effects

**Author:** Dr. Katharina Jacoby  
**Date:** April 9, 2026  
**Affiliation:** Independent Research  
**Contact:** k.jacoby@posteo.de  

---

## Abstract

This manuscript documents a numerical observation regarding the scaling behavior of discrete photonic lattices with anti-periodic boundary conditions ("twists"). Using a discrete Coupled Mode Equation (CME) framework, we simulated two topological configurations: the **Twisted Torus** (single twist) and the **Klein Bottle** (double twist) across lattice sizes $N=4$ to $N=1024$.

Initial coarse-resolution scans suggested the existence of "perfect" mathematical constants ($\alpha \approx 3/5\pi$ and $\alpha \approx 80/199\pi$). However, a re-evaluation using high-resolution binary search ($10^{-8}$ tolerance) revealed these to be **grid quantization artifacts**.

Corrected high-resolution data reveals a robust scaling law: the critical curvature $K_c$ depends on $\lfloor L/2 \rfloor$ rather than $L$. Furthermore, a universal ratio of $\approx \sqrt{2}$ is observed between the scaling products of the two topologies. This work highlights the necessity of high-resolution numerical methods in discrete topology studies and proposes a new empirical scaling law for twisted lattices.

---

## 1. Introduction

In continuous field theory, the critical curvature $K_c$ of a toroidal manifold scales inversely with the characteristic length $L$ ($K_c \propto 1/L$). When instantiated on a discrete grid, the geometry of the grid (Manhattan or Euclidean metric) interacts with the global topology (the twist).

This study addresses a critical gap in numerical topology: **How does the critical curvature $K_c$ scale as we increase the number of nodes $N$, and does the scaling depend on the lattice dimension $L$ or a derived quantity?**

Crucially, this study also serves as a case study in numerical rigor. Initial observations of "perfect" constants prompted a re-evaluation of the search algorithms used, leading to the discovery of significant grid artifacts and the subsequent identification of a more complex, yet robust, scaling law.

---

## 2. Methodology

### 2.1 Model and System
*   **Framework:** Discrete Coupled Mode Equations (CME).
*   **System:** 2D Square Lattice with nearest-neighbor coupling.
*   **Topologies:**
    *   **Twisted Torus:** Anti-periodic boundary in one dimension ($x$).
    *   **Klein Bottle:** Anti-periodic boundary in both dimensions ($x, y$).

### 2.2 Numerical Precision and Artifact Detection
A key component of this study was the verification of numerical stability.
1.  **Initial Scan:** Linear scans with coarse steps (0.05 for KB, 0.01 for Torus) were performed. These yielded "perfect" rational matches for $\alpha$.
2.  **Re-evaluation:** Suspecting grid quantization, we implemented a **two-stage binary search** with a tolerance of $10^{-8}$.
3.  **Result:** The "perfect" constants vanished, shifting to values with slight drifts. This confirmed that the initial results were artifacts of the search grid snapping to specific points.

**Conclusion:** All results presented in this paper are derived from the high-resolution binary search method to ensure physical accuracy.

### 2.3 Metrics
*   **Observed Critical Curvature ($K_c$):** The coupling strength where the system transitions from static to oscillatory (Min_Rho < 0).
*   **Theoretical Target ($K_{target}$):** $K_{target} = 4\pi/L$.
*   **Correction Factor ($\alpha$):** $\alpha = K_c / K_{target}$.
*   **Scaling Product ($P$):** $P = K_c \times \lfloor L/2 \rfloor$.

---

## 3. Results

### 3.1 The $\lfloor L/2 \rfloor$ Dependence
The high-resolution data reveals that $K_c$ does not scale with $L$, but with **$\lfloor L/2 \rfloor$**.

**Table 1: Paired $K_c$ Values (High-Resolution)**
| L | $\lfloor L/2 \rfloor$ | $K_c$ (Klein Bottle) | $K_c$ (Twisted Torus) |
|---|---|---|---|
| 2 | 1 | 1.1107207 | 0.785571 |
| 3 | 1 | 1.1107207 | 0.785571 |
| 4 | 2 | 0.5553604 | 0.392811 |
| 5 | 2 | 0.5553604 | 0.392811 |

**Observation:** Adjacent lattice sizes with the same $\lfloor L/2 \rfloor$ yield **identical** $K_c$ values within numerical precision. This implies the effective resolution of the twist boundary is determined by the integer floor of half the side length.

### 3.2 Product Stability and Drift
The product $P = K_c \times \lfloor L/2 \rfloor$ stabilizes to a near-constant value for each topology.

| Topology | Product $P$ (High-Res) | Stability |
|---|---|---|
| **Klein Bottle** | $1.1107207 \pm 10^{-7}$ | Highly stable |
| **Twisted Torus** | $0.7856 \pm 10^{-3}$ | Minor drift observed |

### 3.3 The Universal Ratio
The ratio of the scaling products between the two topologies is consistently $\approx 1.414$.

$$ \frac{P_{KB}}{P_{Torus}} \approx 1.414 \approx \sqrt{2} $$

While the data strongly suggests $\sqrt{2}$, further simulations at $N > 1024$ are required to confirm if this is an exact mathematical identity or a numerical coincidence.

---

## 4. Discussion

### 4.1 The Nature of the "Perfect" Constants
The initial discovery of "perfect" constants ($3/5\pi$, $80/199\pi$) serves as a cautionary tale in numerical topology. The coarse search grid (step size 0.05) inadvertently aligned with the true $K_c$ values in a way that produced rational approximations indistinguishable from exact constants at low precision. The high-resolution re-evaluation was necessary to uncover the true, slightly drifting physical behavior.

### 4.2 Physical Interpretation of $\lfloor L/2 \rfloor$
The dependence on $\lfloor L/2 \rfloor$ suggests that the discrete grid "sees" the twist boundary not at the full lattice dimension $L$, but at a halved resolution. This may be related to the number of distinct distance shells available under the anti-periodic boundary condition.

### 4.3 Limitations
*   **Simulation Specific:** Results are derived from a specific CME implementation.
*   **Finite Range:** The largest tested size is $N=1024$.
*   **No Analytical Proof:** The $\lfloor L/2 \rfloor$ law and $\sqrt{2}$ ratio are currently empirical.

---

## 5. Conclusion

This study documents a clear behavioral pattern in discrete twisted lattices: a transition from finite-size deviation to scale-invariant stability governed by $\lfloor L/2 \rfloor$.

1.  **Grid Artifacts:** Initial "perfect" constants were numerical artifacts.
2.  **Scaling Law:** $K_c \propto 1/\lfloor L/2 \rfloor$.
3.  **Universal Ratio:** A ratio of $\approx \sqrt{2}$ exists between the Klein Bottle and Twisted Torus scaling products.

Future work will focus on analytical derivation of the $\lfloor L/2 \rfloor$ dependence and verification of the $\sqrt{2}$ ratio at larger scales.

---

## Appendix: Data Availability

Raw simulation data is available in the repository accompanying this manuscript.
*   `scaling_results_klein_bottle_highres.csv`
*   `scaling_results_torus_highres.csv`

The data is provided in standard CSV format to allow full reproducibility of the statistical analysis.

