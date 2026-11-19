# Building-Benchmark

Published results for building energy modeling and control, with the datasets and baselines used in each study.

## Method Zoo

| Method | Task | Baseline |
| --- | --- | --- |
| Smart Model-then-Control (SMC) [[1]](#ref-1) | Learn thermal dynamics for cost-aware HVAC control | Open-loop model predictive control (MPC) with a model trained on mean squared error |
| Personalized federated learning (`DW_ada`) [[2]](#ref-2) | Predict indoor temperature across buildings | Independent training for each building (`Local`) |
| BuildingsBench Transformer-L [[3]](#ref-3) | Forecast day-ahead building load | Persistence Ensemble |

## Datasets

| Dataset | Coverage | Use |
| --- | --- | --- |
| SMC prototypes [[1]](#ref-1) | EnergyPlus, 15 min. Single-zone supermarket, 22-zone hotel, 90-zone apartment | Results below use the supermarket, trained in June and tested in July |
| Federated building prototypes [[2]](#ref-2) | 32 DOE buildings simulated in EnergyPlus, 15 min | Train June–July, test in August under incentive- and price-based demand response |
| Buildings-900K [[3]](#ref-3) | Simulated U.S. building loads, hourly | Transformer pretraining |
| BuildingsBench real buildings [[3]](#ref-3) | Metered commercial and residential buildings, hourly | Zero-shot evaluation using 168 h of history to forecast 24 h |

## Results

Each row summarizes one method. Percentage reductions are relative to its baseline in the Method Zoo. Paired values show the method first and the baseline second. A dash indicates that the paper did not evaluate that outcome.

| Method | Modeling Accuracy | Computational Efficiency | Operational Performance |
| --- | --- | --- | --- |
| SMC [[1]](#ref-1) | Indoor-temperature RMSE 0.3554 vs 0.3344 °C | 0.15 s for MPC optimization (8 h horizon, Xeon CPU) | 5.63% lower daily control cost, including electricity and discomfort penalties |
| `DW_ada` [[2]](#ref-2) | 12.69% lower mean indoor-temperature RMSE across six setpoint schedules | 414.04 min to train across 32 buildings (Xeon CPU) | 6.01% lower mean economic cost per building under price-based control |
| Transformer-L (Gaussian) [[3]](#ref-3) | Median load NRMSE (%)<br>Commercial 13.31 vs 16.68<br>Residential 79.34 vs 77.88 | 24 h to pretrain Transformer-L on Buildings-900K (1 × A100, 40 GB) | — |

## References and Code

1. <a name="ref-1"></a>X. Cui, B. Liu, Y. Li, and Y. Wang. A “Smart Model-Then-Control” Strategy for the Scheduling of Thermostatically Controlled Loads. *IEEE Transactions on Smart Grid*, 16(3), 2246–2260, 2025. [Paper](https://doi.org/10.1109/TSG.2025.3542544) · [Code](https://github.com/hkuedl/Smart-Model-then-Control)
2. <a name="ref-2"></a>X. Cui, D. Qin, J.-F. Toubeau, F. Vallée, and Y. Wang. Generalizable Thermal Dynamics Modeling via Personalized Federated Learning. *IEEE Transactions on Smart Grid*, 16(6), 4698–4711, 2025. [Paper](https://doi.org/10.1109/TSG.2025.3585942) · [Code](https://github.com/hkuedl/Federated-Thermal-Dynamics-Modeling)
3. <a name="ref-3"></a>P. Emami, A. Sahu, and P. Graf. BuildingsBench: A Large-Scale Dataset of 900K Buildings and Benchmark for Short-Term Load Forecasting. *NeurIPS*, Datasets and Benchmarks Track, 2023. [Paper](https://proceedings.neurips.cc/paper_files/paper/2023/hash/3f17bf868966df01ca125e5bbc9ee24e-Abstract-Datasets_and_Benchmarks.html) · [Code](https://github.com/NatLabRockies/BuildingsBench)
