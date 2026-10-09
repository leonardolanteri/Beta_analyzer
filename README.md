# Beta Analyzer

Analysis scripts for ETL beta-source measurements.

## Contents

| File | Description |
|---|---|
| `beta_analyzer.ipynb` | Main analysis notebook — Landau fit on collected charge, Gaussian fit on CFD time difference, DUT time resolution |
| `beta_2026_plotter.ipynb` | Comparison plots across sensors and irradiation levels |

## beta_analyzer

Reads ROOT files produced by the beta setup (tree `Analysis`, branches `pmax`, `area_new`, `cfd`, `tmax`).

**Pipeline:**
1. Configure channels (N_CHANNELS, MCP_CHANNEL) in the config cell
2. Plot `tmax` distributions → set `cuts_tmax`
3. Plot `pmax` filtered by tmax cuts → set `cuts_pmax`
4. Run full analysis: Landau fit on `area_new`, Gaussian fit on Δcfd
5. Summary table: voltage | MPV | σ | MPV/4.7 | σ/4.7 | DUT res [ps] | σ cfd [ns]

**DUT resolution** (when MCP present):

$$\sigma_\text{DUT} = \sqrt{\sigma_\text{CFD}^2 - \sigma_\text{MCP}^2}$$

## Requirements

```
uproot
awkward
numpy
matplotlib
scipy
```
