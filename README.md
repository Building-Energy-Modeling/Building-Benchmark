# Building-Benchmark

A literature benchmark for building energy modeling and control. The tables link published results to the method, building data, and evaluation protocol that produced them. Each comparison uses values from the same paper.

## Method Zoo

| Method | Task and approach | Comparison used below | Paper and code |
| --- | --- | --- | --- |
| Smart Model-then-Control (SMC) | Learn building thermal dynamics for model predictive control (MPC). An input-convex neural network approximates control cost during training. | Open-loop MPC using a thermal model and disturbance forecasts trained on mean squared error (MSE). | [Cui, Liu, Li & Wang, IEEE TSG 2025][smc] · [Code][smc-code] |
| Personalized federated learning (`DW_ada`) | Model indoor temperature across buildings. Each building adaptively combines information about similarities in building physics and operating data. | `Local` trains each building independently. The runtime experiment also tests relearning the weights at every iteration. | [Cui, Qin, Toubeau, Vallée & Wang, IEEE TSG 2025][pfl] · [Code][pfl-code] |
| BuildingsBench Transformer-L (Gaussian) | Forecast day-ahead building load with a pretrained autoregressive Transformer that predicts a Gaussian distribution at each hour. | Persistence Ensemble uses the observations for the same hour on the preceding seven days. | [Emami, Sahu & Graf, NeurIPS 2023][bb] · [Code][bb-code] |

## Datasets

| Dataset or test case | Data and resolution | Role in the reported experiments | Source and access |
| --- | --- | --- | --- |
| SMC building prototypes | EnergyPlus simulations of U.S. Department of Energy (DOE) prototypes at 15-minute intervals. Indoor temperature, weather, occupancy heat gains, and HVAC cooling power. | The single-zone supermarket and 22-zone hotel use June 1–30 for training and July 1–31 for testing. For the 90-zone apartment, the paper labels the splits “Train” and “Test” and gives calendar dates only for the other two buildings. | [SMC, §IV-A and Tables II–III, pp. 2254–2256][smc] · [Authors’ data][smc-data] |
| Federated building prototypes | EnergyPlus simulations of 32 DOE buildings at 15-minute intervals, including offices, residences, and other commercial and public buildings. | Train June 1–July 31. Test August 1–31 with new temperature setpoints for incentive-based demand response, and with MPC for price-based demand response. | [Federated study, §IV-A–C and Tables IV–V, pp. 4705–4709][pfl] · [Authors’ data][pfl-data] |
| Buildings-900K | Simulated hourly consumption derived from the 2021 U.S. End-Use Load Profiles release. | Pretraining data for the BuildingsBench Transformer. | [BuildingsBench, §3, p. 3][bb-data-paper] · [OEDI data][bb-data] |
| BuildingsBench real commercial | Hourly meter data from Electricity (Portugal) and four U.S. Building Data Genome 2 sites. | Commercial subset for zero-shot evaluation. | [BuildingsBench, Table 2 and §4.1, pp. 4–5][bb-protocol] · [OEDI data][bb-data] |
| BuildingsBench real residential | Hourly meter data from Low Carbon London, SMART, IDEAL, Sceaux, and Borealis. | Residential subset for zero-shot evaluation. | [BuildingsBench, Table 2 and §4.1, pp. 4–5][bb-protocol] · [OEDI data][bb-data] |

## Results

### Modeling Accuracy

Lower error is better within each row. For BuildingsBench, the authors divide each building’s load RMSE by its mean observed load, express it as a percentage, and report the median across buildings. For the federated study, the authors average indoor-temperature RMSE across buildings and then across demand-response scenarios. [BuildingsBench, Eq. 2 and Table 3][bb-metric] · [Federated study, Eq. 16 and Table VII][pfl]

| Method | Test data and conditions | Metric | Method result | Same-experiment baseline | Original result |
| --- | --- | --- | ---: | --- | --- |
| SMC | Single-zone supermarket, July test | Indoor-temperature RMSE | 0.3554 °C | 0.3344 °C · MSE-trained MPC model | [Table IV, p. 2256, Model / Test][smc] |
| SMC | 22-zone hotel, July test | Indoor-temperature RMSE | 0.2288 °C | 0.1395 °C · MSE-trained MPC model | [Table V, p. 2257, Model / Test][smc] |
| SMC | 90-zone apartment, paper’s test split | Indoor-temperature RMSE | 0.9191 °C | 0.6204 °C · MSE-trained MPC model | [Table VI, p. 2257, Model / Test][smc] |
| `DW_ada` | 32 simulated buildings, six unseen daily setpoint schedules (DR 1–6) | Mean indoor-temperature RMSE | 1.1861 °C | 1.3585 °C · Local | [Table VII, p. 4707, Average][pfl] |
| Transformer-L (Gaussian) | Real commercial buildings, zero-shot, 168 h history → 24 h forecast | Median load NRMSE | 13.31% | 16.68% · Persistence Ensemble | [Table 3, p. 7, real commercial][bb-results] |
| Transformer-L (Gaussian) | Real residential buildings, zero-shot, 168 h history → 24 h forecast | Median load NRMSE | 79.34% | 77.88% · Persistence Ensemble | [Table 3, p. 7, real residential][bb-results] |

### Computational Efficiency

| Method | Data and timed stage | Hardware | Reported time | Same-experiment comparison | Original result |
| --- | --- | --- | ---: | --- | --- |
| SMC | Single-zone supermarket, MPC optimization over an 8 h horizon | 3.40 GHz Intel Xeon, 16 GB RAM | 0.15 s | 0.11 s · traditional MPC | [§IV-A and Table VII, pp. 2254, 2257][smc] |
| SMC | 22-zone hotel, MPC optimization over an 8 h horizon | 3.40 GHz Intel Xeon, 16 GB RAM | 1.09 s | 0.93 s · traditional MPC | [§IV-A and Table VII, pp. 2254, 2257][smc] |
| SMC | 90-zone apartment, MPC optimization over an 8 h horizon | 3.40 GHz Intel Xeon, 16 GB RAM | 10.19 s | 10.42 s · traditional MPC | [§IV-A and Table VII, pp. 2254, 2257][smc] |
| `DW_ada` | 32 simulated buildings, federated training with local weights learned at initialization | 3.40 GHz Intel Xeon, 16 GB RAM | 414.04 min | 574.31 min · relearn weights at every iteration | [§IV-A and Table VIII, pp. 4705, 4708][pfl] |
| Transformer-L | Buildings-900K, pretraining on one billion hours of simulated load using mixed precision | 1 × NVIDIA A100, 40 GB | 24 h | Standalone timing for the large model | [Appendix G, p. 25, Model pretraining][bb-compute] |

### Operational Performance

SMC’s daily control cost combines electricity expenditure and a penalty for violating temperature bounds. The federated study reports the economic cost per building over the August test period. Both studies evaluate the chosen temperature setpoints in EnergyPlus. [SMC, Eq. 2a and §IV-B][smc] · [Federated study, §IV-C and Table IX][pfl]

| Method | Dataset and control conditions | Reported metric | Method result | Same-experiment baseline | Original result |
| --- | --- | --- | ---: | --- | --- |
| SMC | Single-zone supermarket, July test, 8 h MPC horizon, 2023 NYISO real-time prices | Daily composite control cost¹ | 44.07 | 46.70 · open-loop MPC | [Table III, p. 2256, Single-zone / Test][smc] |
| SMC | 22-zone hotel, July test, 8 h MPC horizon, 2023 NYISO real-time prices | Daily composite control cost¹ | 1017.18 | 1037.31 · open-loop MPC | [Table III, p. 2256, 22-zone / Test][smc] |
| SMC | 90-zone apartment, paper’s test split, 8 h MPC horizon, 2023 NYISO real-time prices | Daily composite control cost¹ | 2332.84 | 2553.38 · open-loop MPC | [Table III, p. 2256, 90-zone / Test][smc] |
| `DW_ada` | 32 simulated buildings, August test, MPC with real-time electricity prices | Mean test-period economic cost per building | $2,418.14 | $2,572.73 · Local | [Table IX, p. 4709, Average][pfl] |

¹ Table III gives the composite cost without a currency label. For the supermarket, the authors report a **5.63%** reduction on the July test set and a **5.97%** reduction on the June training set. [SMC, §IV-B, p. 2255][smc]

Across the 32 simulated buildings, the federated study reports a **12.69%** reduction in mean indoor-temperature RMSE under the six incentive-based scenarios and a **6.01%** reduction in mean economic cost under price-based control. Both comparisons use the independently trained `Local` models. [Federated study, Tables VII and IX, pp. 4707, 4709][pfl]

[smc]: https://doi.org/10.1109/TSG.2025.3542544
[smc-code]: https://github.com/hkuedl/Smart-Model-then-Control
[smc-data]: https://github.com/hkuedl/Smart-Model-then-Control#data
[pfl]: https://doi.org/10.1109/TSG.2025.3585942
[pfl-code]: https://github.com/hkuedl/Federated-Thermal-Dynamics-Modeling
[pfl-data]: https://github.com/hkuedl/Federated-Thermal-Dynamics-Modeling#data
[bb]: https://proceedings.neurips.cc/paper_files/paper/2023/file/3f17bf868966df01ca125e5bbc9ee24e-Paper-Datasets_and_Benchmarks.pdf
[bb-data-paper]: https://proceedings.neurips.cc/paper_files/paper/2023/file/3f17bf868966df01ca125e5bbc9ee24e-Paper-Datasets_and_Benchmarks.pdf#page=3
[bb-protocol]: https://proceedings.neurips.cc/paper_files/paper/2023/file/3f17bf868966df01ca125e5bbc9ee24e-Paper-Datasets_and_Benchmarks.pdf#page=4
[bb-metric]: https://proceedings.neurips.cc/paper_files/paper/2023/file/3f17bf868966df01ca125e5bbc9ee24e-Paper-Datasets_and_Benchmarks.pdf#page=5
[bb-results]: https://proceedings.neurips.cc/paper_files/paper/2023/file/3f17bf868966df01ca125e5bbc9ee24e-Paper-Datasets_and_Benchmarks.pdf#page=7
[bb-compute]: https://proceedings.neurips.cc/paper_files/paper/2023/file/3f17bf868966df01ca125e5bbc9ee24e-Paper-Datasets_and_Benchmarks.pdf#page=25
[bb-code]: https://github.com/NatLabRockies/BuildingsBench
[bb-data]: https://data.openei.org/submissions/5859
