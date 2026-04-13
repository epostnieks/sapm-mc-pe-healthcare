# SAPM Monte Carlo — Private Equity in Healthcare / Fiduciary Contradiction

**Public replication repository for quantitative results in:**

> Postnieks, E. (2026). *Private Equity in Healthcare (Fiduciary Contradiction).* SAPM Working Paper. SSRN.

This repository provides everything needed to independently reproduce, audit,
and extend the Monte Carlo simulation underlying the paper's core results.
The paper is available on SSRN.

---

## Results (N = 100,000 draws, seed = 42)

| Statistic | Value |
|-----------|-------|
| **β_W median** | **5.24** |
| β_W mean | 5.3 |
| β_W std | 0.85 |
| **90% CI** | **[4.0, 6.8]** |
| 99% CI | [3.6, 7.5] |
| P(β_W < 1) | 0.0000% |
| **ΔW median** | **$162.4B/yr** |
| Π (revenue) | $31.0B/yr |

**β_W = 5.24** means the private equity in healthcare industry destroys **$5.24 in system
welfare for every $1.00 in revenue** — across 6 channels and 100,000 Monte Carlo draws.

**Classification**: Class 2 — Intractability

---

## What Is β_W?

```
β_W = ΔW / Π
```

- **ΔW** = total annualized welfare destruction ($B/yr) across all channels
- **Π** = annual industry **revenue** ($B/yr) — not profit

β_W > 1: industry destroys more welfare than it captures in revenue.
β_W > 3: Strong Intractability threshold — reform requires structural replacement.

---

## Quick Start

```bash
git clone https://github.com/epostnieks/sapm-mc-pe-healthcare.git
cd sapm-mc-pe-healthcare
pip install numpy scipy
python mc_simulation.py
```

Expected output: `β_W median : 5.24` and `ΔW median : $162.4B/yr`

---

## Welfare Channels

| Channel | Median ($B/yr) | 90% CI | Distribution |
|---------|---------------|--------|--------------|
| C1_excess_mortality | $81.9B | [$58.3B, $114.9B] | Lognormal |
| C2_hospital_morbidity | $12.0B | [$7.6B, $19.1B] | Lognormal |
| C3_cost_inflation | $34.0B | [$23.0B, $45.0B] | Normal |
| C4_access_loss | $10.0B | [$5.5B, $18.0B] | Lognormal |
| C5_workforce_degradation | $12.0B | [$7.5B, $16.5B] | Normal |
| C6_governance_institutional_failure | $11.0B | [$7.1B, $17.0B] | Lognormal |
| **Total ΔW** | **$162.4B** | **[$124.3B, $210.4B]** | Correlated (ρ=0.3) |

---

## Impossibility Floor

The floor β_W ≥ 3.8 cannot be breached by any policy while the
industry continues to operate. In 100,000 draws, only **2.4330%**
fall below this floor — confirming the structural constraint.

## Repository Contents

| File | Description |
|------|-------------|
| `mc_simulation.py` | Self-contained simulation — no private pipeline imports |
| `mc_results.json` | Pre-run results (100K draws, seed=42) — matches paper |
| `mc_histogram.json` | Binned β_W distribution (80 bins) for companion chart |
| `assumptions.md` | Every parameter: value, derivation, source |
| `data_sources.md` | Full citation list for all empirical inputs |

---

## Replication Notes

Results are seeded and deterministic. Tested with:
```
numpy==1.26.4  scipy==1.12.0  Python 3.11.9
```

The `median` and `ci_90` (to 1 decimal) match exactly across compatible versions.

---

## License

CC BY 4.0. Cite as:

> Postnieks, E. (2026). *SAPM Monte Carlo — Private Equity in Healthcare (Fiduciary Contradiction)*.
> GitHub: epostnieks/sapm-mc-pe-healthcare.
> https://github.com/epostnieks/sapm-mc-pe-healthcare
