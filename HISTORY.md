# Research History: Pattern Recognition in Discrete Twisted Lattices

This document tracks the evolution of our findings from initial observations to current hypotheses.

---

## 📅 Timeline

### March 2026: Initial Observations (v1)
- **Method:** Coarse linear scan (41 steps for KB, 200 for Torus).
- **Finding:** "Perfect" constants appeared ($\alpha_{KB} \approx 3/5\pi$, $\alpha_{Torus} \approx 80/199\pi$).
- **Issue:** The exactness was suspicious. No analytical derivation existed.

### April 2026: Re-evaluation (v2)
- **Action:** Implemented binary search ($10^{-8}$ tolerance).
- **Discovery:** The "constants" were **grid quantization artifacts**.
- **Result:** Values shifted ($\alpha_{KB}: 0.191 \to 0.177$, $\alpha_{Torus}: 0.128 \to 0.125$).

### April 2026: New Patterns (v3 - Current)
- **Finding:** $\lfloor L/2 \rfloor$ dependence identified.
- **Finding:** Universal ratio $\approx 1.414$ ($\sqrt{2}$?) observed.
- **Status:** Active investigation.

---

## 📂 Data Versions

| Version | Date | Resolution | Status |
|---------|------|------------|--------|
| v1 | Mar 2026 | Coarse (0.01–0.05 step) | **Deprecated** (Artifacts) |
| v2 | Apr 2026 | High (Binary search) | **Current** |

---

## 📝 Lessons Learned

1. **Grid resolution matters:** Coarse scans can produce "perfect" numbers that are numerical accidents.
2. **Adjacent sizes matter:** Testing $L=2,3,4,5$ revealed the $\lfloor L/2 \rfloor$ pattern that $L=2,4,8,16$ hid.
3. **Transparency:** Documenting the artifact discovery prevents others from citing incorrect values.