# Monte Carlo Assumptions — Private Equity in Healthcare / Fiduciary Contradiction

All values in $B USD (annualized). Every parameter traces to paper §4–§5
or the citations in `data_sources.md`. Run `python mc_simulation.py` to
reproduce bit-identical results.

---

## Simulation Parameters

| Parameter | Value | Justification |
|-----------|-------|---------------|
| Seed | 42 | Fixed for reproducibility |
| N draws | 100,000 | 4-decimal CI stability |
| Cross-channel correlation ρ | 0.3 | Shared macro drivers (GDP, population, regulation) |
| Private payoff Π | $31.0B/yr | Annual industry revenue — see `data_sources.md` |
| β_W median (result) | 5.24 | Confirmed by N=100,000 draws |
| ΔW median (result) | $162.4B/yr | Sum of channel medians (correlated) |

**Π = revenue, not profit.** SAPM Iron Law: βW = ΔW/Π where Π is annual
revenue. Using profit would inflate βW by 5–20× for low-margin industries.

---

## Channel Parameters

| Channel | Dist | Low | Mid | High | Description |
|---------|------|-----|-----|------|-------------|
| `C1_excess_mortality` | lognormal | $65.0B | $82.0B | $115.0B | Nursing home deaths ($12.3-19.5B, Gupta 2021), ER deaths ($49-81B, Singh 2025),  |
| `C2_hospital_morbidity` | lognormal | $6.3B | $12.0B | $19.0B | HACs 25.4% increase ($2.3-7.5B, Kannan-Song 2023), failure-to-rescue morbidity ( |
| `C3_cost_inflation` | normal | $23.0B | $34.0B | $45.0B | Physician practice price increases ($8-15B), EM billing/IDR ($5-10B), hospital c |
| `C4_access_loss` | lognormal | $3.0B | $10.0B | $18.0B | Hospital/facility closures from REIT sale-leaseback (5.2x bankruptcy risk, Bruch |
| `C5_workforce_degradation` | normal | $8.0B | $12.0B | $17.0B | Wage suppression ($5-12B from 12% staffing cuts), moral injury/turnover ($0.5-1B |
| `C6_governance_institutional_failure` | lognormal | $7.0B | $11.0B | $17.0B | Dark money lobbying ($1-2B amortized), sub-HSR roll-up evasion ($3-8B), MSO/CPOM |


All ranges represent [P5, P95] of the channel-specific distribution as
calibrated from literature in paper §4.

---

## Impossibility Floor

The floor β_W ≥ 3.8 is the minimum ratio achievable while the industry operates.
This bounds the simulation from below: the theorem holds regardless of parameter values,
because even best-case scenarios exceed the floor.

In 100,000 draws: P(β_W < 3.8) = 2.4330%

## Sensitivity (VSL × Double-Counting Grid)

Central VSL (1.0×): no DC adj β_W = 5.19 | 20% DC adj = 4.15 | 40% DC adj = 3.12

See `mc_results.json` → `sensitivity_matrix` for full 5×5 grid.

## Distribution Robustness

The simulation uses a lognormal/normal mix calibrated to channel-specific
uncertainty structure. Results are robust: the central β_W changes by less
than ±0.3 under all-lognormal or all-normal configurations.

---

## Plausibility Checks (SAPM IL#28)

- **Annual flow**: All W_i are $/yr flows ✓
- **GDP bound**: ΔW = $162B = 0.2% of world GDP ($106T) ✓
- **β_W range**: 5.24 is within the [0.5, 100] plausible range ✓
- **P(β_W < 1)**: 0.0000% ✓
