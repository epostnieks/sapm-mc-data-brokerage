# SAPM Monte Carlo — Data Brokerage / Surveillance / Consent Fabrication Trap

**Public replication repository for quantitative results in:**

> Postnieks, E. (2026). *Data Brokerage / Surveillance (Consent Fabrication Trap).* SAPM Working Paper. SSRN.

This repository provides everything needed to independently reproduce, audit,
and extend the Monte Carlo simulation underlying the paper's core results.
The paper is available on SSRN.

---

## Results (N = 100,000 draws, seed = 42)

| Statistic | Value |
|-----------|-------|
| **β_W median** | **6.13** |
| β_W mean | 6.21 |
| β_W std | 1.02 |
| **90% CI** | **[4.7, 8.0]** |
| 99% CI | [4.2, 9.0] |
| P(β_W < 1) | 0.0000% |
| **ΔW median** | **$1,979.5B/yr** |
| Π (revenue) | $323.0B/yr |

**β_W = 6.13** means the data brokerage / surveillance industry destroys **$6.13 in system
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
git clone https://github.com/epostnieks/sapm-mc-data-brokerage.git
cd sapm-mc-data-brokerage
pip install numpy scipy
python mc_simulation.py
```

Expected output: `β_W median : 6.13` and `ΔW median : $1,979.5B/yr`

---

## Welfare Channels

| Channel | Median ($B/yr) | 90% CI | Distribution |
|---------|---------------|--------|--------------|
| C1_security | $185.8B | [$127.8B, $269.6B] | Lognormal |
| C2_autonomy_privacy | $479.7B | [$328.7B, $701.9B] | Lognormal |
| C3_democratic | $319.9B | [$204.9B, $499.7B] | Lognormal |
| C4_discrimination | $260.2B | [$168.8B, $399.5B] | Lognormal |
| C5_consumer_manipulation | $389.4B | [$262.6B, $578.2B] | Lognormal |
| C6_governance | $309.7B | [$200.4B, $480.0B] | Lognormal |
| **Total ΔW** | **$1,979.5B** | **[$1,517.0B, $2,591.0B]** | Correlated (ρ=0.3) |

---

## Impossibility Floor

The floor β_W ≥ 3.0 cannot be breached by any policy while the
industry continues to operate. In 100,000 draws, only **0.0000%**
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

> Postnieks, E. (2026). *SAPM Monte Carlo — Data Brokerage / Surveillance (Consent Fabrication Trap)*.
> GitHub: epostnieks/sapm-mc-data-brokerage.
> https://github.com/epostnieks/sapm-mc-data-brokerage
