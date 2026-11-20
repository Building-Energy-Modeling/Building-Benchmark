# Building thermal dynamics

Ten journal studies on temperature prediction and HVAC control. Each result uses the evaluation conditions and comparison model from its own study.

## 1. Methods

| Method | Thermal quantity | Modeling idea |
|---|---|---|
| [01][p01] Smart Model-Then-Control (SMC) | Zone temperatures | Train a thermal model on a surrogate of MPC cost |
| [02][p02] Personalized federated learning (DW_ada) | Building-equivalent indoor temperature | Share model parameters by building and data similarity |
| [03][p03] Residential 2R2C | Indoor and envelope temperatures | Fit a two-resistance, two-capacitance model per home |
| [04][p04] Single-zone PCNN | Bedroom temperature | Combine an LSTM with physically constrained heat flows |
| [05][p05] Multi-zone X-PCNN | Temperature in each room | Train zone models separately, then couple their heat flows |
| [06][p06] Context-aware Transformer | Mean indoor temperature | Train separate models for different building heights |
| [07][p07] PhysCon | Room temperature and cooling load | Add 2R2C heat-balance equations to the training loss |
| [08][p08] Fully adaptive MPC | Indoor temperature | Refit seven thermal parameters when prediction errors grow |
| [09][p09] Weather-adaptive 4R3C | Zone air temperature | Refit using days with similar weather |
| [10][p10] EnergyPlus internal-mass model | Temperature inside the thermal mass | Model transient conduction through an equivalent slab |

MPC = model predictive control. PCNN = physically consistent neural network.

## 2. Datasets

The cases below are the ones used in the results tables. Sampling or control intervals are labeled separately from forecast horizons.

| Study | Building data | Evaluation setup |
|---|---|---|
| [01][p01] SMC | DOE 22-zone hotel · EnergyPlus · 15 min | June training, July test · 8 h control horizon |
| [02][p02] DW_ada | 32 DOE buildings, 8 types · EnergyPlus · 15 min | June–July training, August test on the same buildings |
| [03][p03] Residential 2R2C | 220 Dutch homes monitored · hourly measurements | 187 models validated on a separate 10-day period |
| [04][p04] Single-zone PCNN | Swiss NEST/UMAR apartment · one bedroom · 15 min | Nearly 2,000 three-day validation windows |
| [05][p05] X-PCNN | Same apartment · two bedrooms and living room · 15 min | Over 750 three-day validation windows with known inputs |
| [06][p06] Context-aware Transformer | 18 Swedish training buildings · hourly measurements | Piteå low-rise test subset · 6 h forecast |
| [07][p07] PhysCon | Two experimental rooms · heavy and light thermal mass | Held-out day · 5 min ahead |
| [08][p08] Fully adaptive MPC | Oslo house · IDA ICE–MATLAB simulation | November–December · 61 days · 15 min control interval |
| [09][p09] Weather-adaptive 4R3C | Ningbo office · simulator calibrated on 5 min measurements | Four-day simulated cold snap |
| [10][p10] Internal-mass model | Test room · surface and internal temperature sensors | 30 days of measurements |

## 3. Reported results

### Prediction accuracy

| Study and case | Metric | Reported | Comparison on the same case |
|---|---|---:|---|
| [01][p01] SMC · hotel, July | Zone temperature RMSE (°C) | 0.2288 | 0.1395 · MSE-trained model |
| [02][p02] DW_ada · six new setpoint schedules | Mean building RMSE (°C) | 1.1861 | 1.3585 · independent local models |
| [04][p04] PCNN · 1 h ahead | MAE at forecast lead (°C) | 0.31 | 0.19 · RC model |
| [04][p04] PCNN · 72 h ahead | MAE at forecast lead (°C) | 0.88 | 1.48 · RC model |
| [05][p05] X-PCNN · three rooms | Best-run MAE over 72 h (°C) | 1.17 | 1.27 · LSTM |
| [06][p06] Transformer · Piteå low-rise, 6 h | R² | 0.946 | 0.803 · pooled Transformer |
| [07][p07] PhysCon · heavy-mass room, 5 min | Room temperature MAE (°C) | 0.25 | 0.47 · unconstrained neural network |
| [09][p09] 4R3C · cold snap | Zone temperature RMSE (°C) | 0.259 | 0.344 · fit on the latest three days |

In [study 02][p02], RMSE is computed per building, then averaged over buildings and schedules. In [study 09][p09], both models use three training days.

### Validation against measurements

| Study | Measured quantity | Reported error |
|---|---|---|
| [03][p03] Residential 2R2C | Indoor air temperature in 187 homes | Mean validation RMSE 0.54 °C |
| [10][p10] Internal-mass model | Temperature inside the thermal mass | RMSE 0.9 °C |

### Control performance

| Study and case | Outcome | Reported | Comparison on the same case |
|---|---|---:|---|
| [01][p01] SMC · hotel, July | Mean daily control cost¹ | 1,017.18 | 1,037.31 · open-loop MPC |
| [02][p02] DW_ada · August price response | Mean monthly cost per building ($) | 2,418.14 | 2,572.73 · local models |
| [08][p08] Adaptive MPC · 61 days | Cumulative discomfort (K·h) | 50.68 | 210.74 · fixed FullWinter MPC |
| [08][p08] Adaptive MPC · same run | Energy use (kWh) | 353.89 | 328.56 · fixed FullWinter MPC |

¹ The daily objective includes electricity charges and a comfort penalty. Both [study 08][p08] outcomes use the same comfort penalty weight of 10⁸.

### Computation time

| Study and case | Timed operation | Reported | Comparison on the same case |
|---|---|---:|---|
| [01][p01] SMC · 22-zone hotel | Online MPC solve · 8 h horizon | 1.09 s | 0.93 s · open-loop MPC |
| [02][p02] DW_ada · 32 buildings | Offline federated training | 414.04 min | 574.31 min · weights updated every round |

Both studies report a 3.40 GHz Intel Xeon CPU and 16 GB of RAM.

<details>
<summary>Paper titles and locations of reported results</summary>

1. [A “Smart Model-Then-Control” Strategy for the Scheduling of Thermostatically Controlled Loads][p01]. *IEEE Transactions on Smart Grid* (2025). Tables III, V and VII.
2. [Generalizable Thermal Dynamics Modeling via Personalized Federated Learning][p02]. *IEEE Transactions on Smart Grid* (2025). Eq. 16 and Tables VII–IX.
3. [Data-driven method for optimized supply temperatures in residential buildings][p03]. *Energy* (2023). Section 3.2 and Fig. 5.
4. [Physically Consistent Neural Networks for building thermal modeling: Theory and analysis][p04]. *Applied Energy* (2022). Table 2 and Fig. 5.
5. [Towards scalable physically consistent neural networks: An application to data-driven multi-zone thermal building models][p05]. *Applied Energy* (2023). Section 5 and Table 1.
6. [Indoor temperature prediction with context-aware models in residential buildings][p06]. *Building and Environment* (2023). Table 4.
7. [Physics-informed neural networks for building thermal modeling and demand response control][p07]. *Building and Environment* (2023). Table 8.
8. [Comparison of time-invariant and adaptive linear grey-box models for model predictive control of residential buildings][p08]. *Building and Environment* (2024). Table 5.
9. [An adaptive grey-box model for nearly zero energy building operations in challenging climate][p09]. *Energy* (2026). Table 5.
10. [Enhancing EnergyPlus simulation of internal mass for dynamic thermal energy storage][p10]. *Energy* (2026). Model validation and Fig. 3.

</details>

[p01]: https://doi.org/10.1109/TSG.2025.3542544
[p02]: https://doi.org/10.1109/TSG.2025.3585942
[p03]: https://doi.org/10.1016/j.energy.2023.129183
[p04]: https://doi.org/10.1016/j.apenergy.2022.119806
[p05]: https://doi.org/10.1016/j.apenergy.2023.121071
[p06]: https://doi.org/10.1016/j.buildenv.2023.110772
[p07]: https://doi.org/10.1016/j.buildenv.2023.110149
[p08]: https://doi.org/10.1016/j.buildenv.2024.111391
[p09]: https://doi.org/10.1016/j.energy.2026.141151
[p10]: https://doi.org/10.1016/j.energy.2026.141885
