# SAPM Monte Carlo — POPs Beyond PFAS / Bioaccumulation Ratchet

**Public replication repository for quantitative results in:**

> Postnieks, E. (2026). *POPs Beyond PFAS (Bioaccumulation Ratchet).* SAPM Working Paper. SSRN.

This repository provides everything needed to independently reproduce, audit,
and extend the Monte Carlo simulation underlying the paper's core results.
The paper is available on SSRN.

---

## Results (N = 100,000 draws, seed = 42)

| Statistic | Value |
|-----------|-------|
| **β_W median** | **6.23** |
| β_W mean | 6.37 |
| β_W std | 1.35 |
| **90% CI** | **[4.4, 8.8]** |
| 99% CI | [3.8, 10.2] |
| P(β_W < 1) | 0.0000% |
| **ΔW median** | **$435.8B/yr** |
| Π (revenue) | $70.0B/yr |

**β_W = 6.23** means the pops beyond pfas industry destroys **$6.23 in system
welfare for every $1.00 in revenue** — across 5 channels and 100,000 Monte Carlo draws.

**Classification**: Class 1 — Impossibility

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
git clone https://github.com/epostnieks/sapm-mc-pops.git
cd sapm-mc-pops
pip install numpy scipy
python mc_simulation.py
```

Expected output: `β_W median : 6.23` and `ΔW median : $435.8B/yr`

---

## Welfare Channels

| Channel | Median ($B/yr) | 90% CI | Distribution |
|---------|---------------|--------|--------------|
| C1_health_bioaccumulation | $149.2B | [$90.4B, $245.4B] | Lognormal |
| C2_ecosystem_contamination | $128.0B | [$77.6B, $211.5B] | Lognormal |
| C3_remediation_costs | $85.3B | [$51.7B, $140.7B] | Lognormal |
| C4_intergenerational_exposure | $42.7B | [$25.9B, $70.6B] | Lognormal |
| C5_regulatory_lag | $21.4B | [$17.1B, $25.7B] | Normal |
| **Total ΔW** | **$435.8B** | **[$309.5B, $617.6B]** | Correlated (ρ=0.3) |

---

## Impossibility Floor

The floor β_W ≥ 3.4 cannot be breached by any policy while the
industry continues to operate. In 100,000 draws, only **0.1490%**
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

> Postnieks, E. (2026). *SAPM Monte Carlo — POPs Beyond PFAS (Bioaccumulation Ratchet)*.
> GitHub: epostnieks/sapm-mc-pops.
> https://github.com/epostnieks/sapm-mc-pops
