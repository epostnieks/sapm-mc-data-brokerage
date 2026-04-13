# Monte Carlo Assumptions — Data Brokerage / Surveillance / Consent Fabrication Trap

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
| Private payoff Π | $323.0B/yr | Annual industry revenue — see `data_sources.md` |
| β_W median (result) | 6.13 | Confirmed by N=100,000 draws |
| ΔW median (result) | $1,979.5B/yr | Sum of channel medians (correlated) |

**Π = revenue, not profit.** SAPM Iron Law: βW = ΔW/Π where Π is annual
revenue. Using profit would inflate βW by 5–20× for low-margin industries.

---

## Channel Parameters

| Channel | Dist | Low | Mid | High | Description |
|---------|------|-----|-----|------|-------------|
| `C1_security` | lognormal | $130B | $186B | $270B | Identity theft, breach remediation, fraud enabled |
| `C2_autonomy_privacy` | lognormal | $320B | $480B | $700B | Privacy degradation, surveillance capitalism |
| `C3_democratic` | lognormal | $200B | $320B | $500B | Democratic manipulation, disinformation targeting |
| `C4_discrimination` | lognormal | $170B | $260B | $400B | Algorithmic discrimination, credit/insurance bias |
| `C5_consumer_manipulation` | lognormal | $260B | $390B | $580B | Dark patterns, attention hijacking, addiction |
| `C6_governance` | lognormal | $200B | $310B | $480B | Consent theater, regulatory capture |


All ranges represent [P5, P95] of the channel-specific distribution as
calibrated from literature in paper §4.

---

## Impossibility Floor

The floor β_W ≥ 3.0 is the minimum ratio achievable while the industry operates.
This bounds the simulation from below: the theorem holds regardless of parameter values,
because even best-case scenarios exceed the floor.

In 100,000 draws: P(β_W < 3.0) = 0.0000%

## Sensitivity (VSL × Double-Counting Grid)

Central VSL (1.0×): no DC adj β_W = 6.02 | 20% DC adj = 4.82 | 40% DC adj = 3.61

See `mc_results.json` → `sensitivity_matrix` for full 5×5 grid.

## Distribution Robustness

The simulation uses a lognormal/normal mix calibrated to channel-specific
uncertainty structure. Results are robust: the central β_W changes by less
than ±0.3 under all-lognormal or all-normal configurations.

---

## Plausibility Checks (SAPM IL#28)

- **Annual flow**: All W_i are $/yr flows ✓
- **GDP bound**: ΔW = $1,980B = 1.9% of world GDP ($106T) ✓
- **β_W range**: 6.13 is within the [0.5, 100] plausible range ✓
- **P(β_W < 1)**: 0.0000% ✓
