# Sobol-capable samplers

| Sampler class | Sampler module | Paired analysis class | Analysis module | Sobol indices supported | Estimation approach |
| --- | --- | --- | --- | --- | --- |
| `PCESampler` | `easyvvuq/sampling/pce.py` | `PCEAnalysis` | `easyvvuq/analysis/pce_analysis.py` | First, Second, Total | Analytic, from Polynomial Chaos Expansion coefficients (`chaospy` `Sens_m`/`Sens_m2`/`Sens_t`) |
| `SCSampler` | `easyvvuq/sampling/stochastic_collocation.py` | `SCAnalysis` | `easyvvuq/analysis/sc_analysis.py` | First, Total (all orders via powerset) | Analytic, from Stochastic Collocation / equivalent PCE expansion |
| `MCSampler` | `easyvvuq/sampling/mc_sampler.py` | `QMCAnalysis` | `easyvvuq/analysis/qmc_analysis.py` | First, Total | Saltelli-type Monte Carlo estimator with bootstrap confidence intervals |
| `QMCSampler` | `easyvvuq/sampling/qmc.py` | `QMCAnalysis` | `easyvvuq/analysis/qmc_analysis.py` | First, Total | Saltelli-type quasi-Monte Carlo estimator with bootstrap confidence intervals |

## Samplers excluded and why

- `FDSampler` (`easyvvuq/sampling/fd.py`) is paired with `FDAnalysis`, which only computes finite-difference derivative-based sensitivity indices; the `sobols_first`/`sobols_second`/`sobols_total` fields remain unused zero placeholders.
- `SSCSampler` (`easyvvuq/sampling/simplex_stochastic_collocation.py`) is paired with `SSCAnalysis`; Sobol index retrieval is present in source but commented out / not implemented.
- `Grid_Sampler`, `RandomSampler`, `LHCSampler`, `HaltonSampler`, `CSVSampler`, `DataFrameSampler`, `ReplicaSampler`, `MultiSampler`, `EmptySampler`, and `MCMCSampler` are not paired with an analysis class that computes Sobol indices.
