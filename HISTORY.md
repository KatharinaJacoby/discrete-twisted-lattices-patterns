# Research History: Pattern Recognition in Discrete Twisted Lattices

Welcome to the evolving story of this project. This document tracks our journey from initial curiosity to refined understanding. We believe that sharing the *process*—including the dead ends and corrections—is just as valuable as the final results.

---

## 📅 Timeline of Discoveries

### March 2026:
- **What we did:** Ran initial simulations using coarse linear scans.
- **What we saw:** "Perfect" mathematical constants appeared to emerge naturally ($\alpha_{KB} \approx 3/5\pi$, $\alpha_{Torus} \approx 80/199\pi$).
- **The feeling:** Exciting, but there was no clear ratio for the torus.


### April, 2026: 
- **What we did:** Doubled down on precision, implementing a high-resolution binary search ($10^{-8}$ tolerance).
- **What happened:** The "perfect" constants vanished. The values shifted slightly, revealing small but consistent drifts.
- **The lesson:** Those initial numbers were probabably **grid quantization artifacts**—numerical coincidences caused by our search grid aligning with specific data points.
- **A new pattern:** In the noise, a new pattern emerged: the **$\lfloor L/2 \rfloor$ dependence**. We noticed that adjacent lattice sizes (like $L=2$ and $L=3$) shared identical $K_c$ values.
- **The Puzzle:** We noticed a $\sqrt{2}$ ratio between the Klein Bottle and Twisted Torus scaling products. Was this a universal topological truth?
- **The Action:** We rewrote the Torus script to run with *both* metrics, using the exact same binary search algorithm and lattice range ($N=4$ to $N=1024$) as the Klein Bottle.
- **The Result:** 
  - **Euclidean Torus:** Converged to the *same* scaling product as the Klein Bottle ($P \approx 1.11072$).
  - **Manhattan Torus:** Converged to a different constant ($P = \pi/4 \approx 0.7854$).
- **The Conclusion:** The $\sqrt{2}$ ratio was an artifact of comparing a Manhattan Torus to a Euclidean Klein Bottle. When we harmonized the metrics, the ratio disappeared.
- **The Core Finding:** The **$\lfloor L/2 \rfloor$ scaling law** is robust. It holds true regardless of the metric or topology.
- **The Nuance:** The specific *value* of the scaling constant depends on the metric, but the *form* of the scaling does not.

---

If you spot something we missed, have a different interpretation, or just want to chat about the physics, please reach out! We are happy to share our source code to help you verify these results or run your own variations.

**Email:** k.jacoby@posteo.de
