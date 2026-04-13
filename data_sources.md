# Data Sources — Private Equity in Healthcare Monte Carlo Simulation

Channel parameters in `mc_simulation.py` trace to the sources listed here.
The paper (Private Equity in Healthcare: Fiduciary Contradiction) is available on SSRN and contains the full
reference list and §4 calibration narrative.

---

## Channel Sources

### `C1_excess_mortality`

Nursing home deaths ($12.3-19.5B, Gupta 2021), ER deaths ($49-81B, Singh 2025), surgical deaths ($3.5-14.5B, Cerullo 2025). VSL=$11.6M. Sources: Gupta et al., Singh et al., Cerullo et al.

*Full citations: paper §4 (available SSRN).*

### `C2_hospital_morbidity`

HACs 25.4% increase ($2.3-7.5B, Kannan-Song 2023), failure-to-rescue morbidity ($3-8B), patient experience degradation ($1-3.5B). Sources: CDC HAC data, Kannan-Song, Wadhera.

*Full citations: paper §4 (available SSRN).*

### `C3_cost_inflation`

Physician practice price increases ($8-15B), EM billing/IDR ($5-10B), hospital consolidation ($6-12B), nursing home cost increases ($4-8B). Sources: Gupta JAMA 2022, Cooper-Morton 2025, AAI.

*Full citations: paper §4 (available SSRN).*

### `C4_access_loss`

Hospital/facility closures from REIT sale-leaseback (5.2x bankruptcy risk, Bruch 2025), rural hospital closures (130 PE-owned), community access loss. Sources: Bruch et al. BMJ, PESP 2024.

*Full citations: paper §4 (available SSRN).*

### `C5_workforce_degradation`

Wage suppression ($5-12B from 12% staffing cuts), moral injury/turnover ($0.5-1B), system capacity erosion ($2-4B). Sources: Singh et al. 2025, CMS data, AMA burnout estimates.

*Full citations: paper §4 (available SSRN).*

### `C6_governance_institutional_failure`

Dark money lobbying ($1-2B amortized), sub-HSR roll-up evasion ($3-8B), MSO/CPOM manipulation ($1-3B), captive insurance abuse ($0.5-2B), IDR gaming ($1.5-2B). Sources: PESP, Cooper-Morton, FTC.

*Full citations: paper §4 (available SSRN).*

---

## Industry Revenue (Π)

The private payoff Π = $31.0B/yr is global annual industry revenue.
Source: paper §2 and §4. See paper §DA-1 (Decision Audit Field 7) for full
revenue source documentation.

---

## SAPM Framework

- Postnieks, E. (2026). *The Private Pareto Theorem*. SAPM Foundation Paper. SSRN.
- Postnieks, E. (2026). *Private Equity in Healthcare (Fiduciary Contradiction)*. SAPM Working Paper. SSRN.

---

## Distribution Methodology

- Iman, R. L., & Conover, W. J. (1982). A distribution-free approach to
  inducing rank correlation among input variables. *Communications in
  Statistics — Simulation and Computation*, 11(3), 311–334.
- Cooke, R. M. (1991). *Experts in Uncertainty*. Oxford University Press.
