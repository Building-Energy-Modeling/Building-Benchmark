# Building thermal dynamics

This collection summarizes 100 journal articles published between 2022 and 2026 on building thermal dynamics and HVAC control. It covers modeling methods, datasets and evaluation results. A common study number links each entry to its reference.

[Methods](#methods) · [Datasets](#datasets) · [Reported results](#reported-results) · [References](#references)

## Methods

This section summarizes the methods used to model building thermal dynamics. Each entry identifies the modeling approach, the thermal quantity or control task it addresses, and the main principle behind the method.

| Method | Thermal quantity or task | Modeling idea |
| --- | --- | --- |
| <a href="#ref-1">[1]</a> Smart Model-Then-Control (SMC) | Zone temperatures | Train a thermal model on a surrogate of MPC cost |
| <a href="#ref-2">[2]</a> Personalized federated learning (DW_ada) | Building-equivalent indoor temperature | Share model parameters by building and data similarity |
| <a href="#ref-3">[3]</a> Residential 2R2C | Indoor and envelope temperatures | Fit a two-resistance, two-capacitance model per home |
| <a href="#ref-4">[4]</a> Single-zone PCNN | Bedroom temperature | Combine an LSTM with physically constrained heat flows |
| <a href="#ref-5">[5]</a> Multi-zone X-PCNN | Temperature in each room | Train zone models separately, then couple their heat flows |
| <a href="#ref-6">[6]</a> Context-aware Transformer | Mean indoor temperature | Train separate models for different building heights |
| <a href="#ref-7">[7]</a> PhysCon | Room temperature and cooling load | Add 2R2C heat-balance equations to the training loss |
| <a href="#ref-8">[8]</a> Fully adaptive MPC | Indoor temperature | Refit seven thermal parameters when prediction errors grow |
| <a href="#ref-9">[9]</a> Weather-adaptive 4R3C | Zone air temperature | Refit using days with similar weather |
| <a href="#ref-10">[10]</a> EnergyPlus internal-mass model | Temperature inside the thermal mass | Model transient conduction through an equivalent slab |
| <a href="#ref-11">[11]</a> ETP + TimesNet and two-stage control | Zone temperature | TimesNet learns occupant-driven temperature residuals. MPC sets bounds for a deep Q-network |
| <a href="#ref-12">[12]</a> Adaptive grey-box identification | Room temperature | Re-identify thermal and noise parameters separately during normal operation |
| <a href="#ref-13">[13]</a> Bottom-up heat-pump fleet model | Indoor temperature and flexible power | Aggregate dwelling heat losses, thermal storage and heat-pump operation |
| <a href="#ref-14">[14]</a> Physics-consistent neural model and differentiable control | Zone temperature with phase-change storage | A first-law encoder–decoder represents latent heat and optimizes HVAC setpoints |
| <a href="#ref-15">[15]</a> Greenhouse heat-balance model | Greenhouse air temperature | Fits crop evapotranspiration to sensor readings and models heat exchange with the host building |
| <a href="#ref-16">[16]</a> Multi-branch CNN–LSTM | Zonal temperature, humidity and illuminance | Cluster office sensor locations and fuse sensor inputs, then use separate branches to predict air temperature, relative humidity and illuminance |
| <a href="#ref-17">[17]</a> Coupled BES–CFD | Spatial air temperatures under hybrid HVAC | Exchanges boundary conditions and adjusts convective heat transfer to the local airflow |
| <a href="#ref-18">[18]</a> Transient Block–Gebhart model | Air and wall temperature · stratified cooling load | Adds envelope heat storage and transmitted solar gains to a zonal heat balance |
| <a href="#ref-19">[19]</a> EnergyPlus internal-mass plugin | Room temperature and night ventilation | An analytical conduction model couples thermal mass to zone air |
| <a href="#ref-20">[20]</a> Finite-difference thermal storage model | Effective storage capacity and discharge rate | Resolves heat exchange layer by layer and tests sensitivity to design and operation |
| <a href="#ref-21">[21]</a> Bayesian-optimized TCN–LSTM with self-attention | Exterior-wall heat flux | Wall heat-transfer physics guides input selection for a temporal neural network |
| <a href="#ref-22">[22]</a> Thermally activated slab model with Taguchi optimization | Slab, room and return-water temperatures | Couples the slab with heat pumps, PV and battery operation, then optimizes settings |
| <a href="#ref-23">[23]</a> 5R3C simulation with a deep Q-network | Radiant-floor heating control | A calibrated thermal network trains a controller using temperature trends and future targets |
| <a href="#ref-24">[24]</a> Dynamically weighted physics-informed LSTM | Room air temperature | Attention and time-varying weights balance a heat-transfer residual against data fit |
| <a href="#ref-25">[25]</a> Dynamic heating-curtailment simulation | Indoor temperature and heating flexibility | Vary thermal insulation, weather and curtailment timing to find feasible interruptions |
| <a href="#ref-26">[26]</a> Zone-level virtual batteries | Zone temperatures and HVAC flexibility | Aggregate thermal states into a virtual battery, then allocate its power schedule to zones |
| <a href="#ref-27">[27]</a> Chilled-water storage model | Water-loop and indoor temperatures | Couple advection and diffusion in chilled water to room heat balance during demand response |
| <a href="#ref-28">[28]</a> Stepwise scheduling reformulation | Coupled zone temperatures | Cluster thermally adjacent zones and convert probabilistic scheduling constraints to deterministic ones |
| <a href="#ref-29">[29]</a> Physics-informed primal–dual control | Zone comfort constraint violations | Use an RC model to predict the next constraint gradient and adjust the control update |
| <a href="#ref-30">[30]</a> Uncertainty-aware flexibility model | Temperature and reserve capacity | Use chance constraints and affine real-time feedback to quantify heating flexibility |
| <a href="#ref-31">[31]</a> Adaptive physically consistent neural network | Data-centre temperature | A Softplus network learns positive coefficients that adapt to operating conditions |
| <a href="#ref-32">[32]</a> EnergyPlus with neural residual correction | Room temperature | Compare four ways to combine EnergyPlus and data-driven predictors |
| <a href="#ref-33">[33]</a> Nonlinear RC network and deep reinforcement learning | Indoor temperature and cooling energy | Model changing optical and thermal envelope properties in the controller’s training environment |
| <a href="#ref-34">[34]</a> Physics-aware graph network and MPC | Zone temperatures and chiller operation | Represent zone coupling with a graph and embed constrained chiller and zone models in MPC |
| <a href="#ref-35">[35]</a> Modular reinforcement learning with a PCNN simulator | Room temperature and heating commands | Reuse the temperature policy and retrain a room-specific mapping to heating actions |
| <a href="#ref-36">[36]</a> Ontology-based digital twin | Zone temperature, CO₂ and actuator positions | Automatically connect component models and calibrate them with sensor records |
| <a href="#ref-37">[37]</a> Causal machine learning | Indoor temperature response to heating | Debias observational data and test the direction of the learned heating effect |
| <a href="#ref-38">[38]</a> Genetic programming with closed-loop identification | Zone temperature for heating MPC | Starts with a first-order model, then relearns the operating model from closed-loop responses |
| <a href="#ref-39">[39]</a> Adaptive graph convolution | Room temperature field | Learns spatial links between measurement points and selects a sparse sensor set |
| <a href="#ref-40">[40]</a> Single-mass subspace model (N4SID) | Mean indoor temperature and heating load | Identifies a state-space heat balance from indoor and outdoor temperature and heating load |
| <a href="#ref-41">[41]</a> CFD with ensemble Kalman filtering | Room temperature and humidity fields | Updates uncertain boundary conditions and spatial fields from a few observations |
| <a href="#ref-42">[42]</a> Equivalent solar heat source and CNN | Temperature field under moving sunlight | Converts direct solar gains into surface heat fluxes and combines them with temperature-field inputs |
| <a href="#ref-43">[43]</a> Response-coefficient CNN | Transient room temperature field | Combines separate heat-source responses to predict the field used for HVAC control |
| <a href="#ref-44">[44]</a> Gated multitask BiLSTM | Multi-point temperature and humidity | Shares features across sensors with task-specific gates and bidirectional recurrence |
| <a href="#ref-45">[45]</a> 2R2C-informed neural network | Indoor temperature and building load | Adds a calibrated two-resistance, two-capacitance heat balance to the network loss |
| <a href="#ref-46">[46]</a> Chance-constrained stochastic MPC | Temperature and relative humidity | Uses a coupled resistance–capacitance model and probabilistic comfort constraints |
| <a href="#ref-47">[47]</a> Humidity-enhanced RC mapping | Indoor temperature during cooling curtailment | Models latent heat and HVAC thermal storage with staged parameter identification |
| <a href="#ref-48">[48]</a> Probabilistic equivalent-thermal-parameter model | Adjustable cooling demand and comfort bounds | Historical setpoints and demand-response feedback update building-specific parameters |
| <a href="#ref-49">[49]</a> Noise-robust recursive RC identification | Indoor temperature and cooling power | A polynomial Kalman smoother estimates noise before recursive total least squares |
| <a href="#ref-50">[50]</a> Analytical shedding and rebound | Cooling-load changes after setpoint shifts | Solve second-order thermal dynamics for load reduction and rebound, then aggregate across buildings |
| <a href="#ref-51">[51]</a> Decision-oriented neural ODE | Building-equivalent indoor temperature and HVAC cost | Fit neural differential equations jointly to prediction errors and downstream operating costs |
| <a href="#ref-52">[52]</a> Latent-state optimization | Multi-zone temperatures and control actions | Train an autoencoder with a state-space model and optimize in the reduced space |
| <a href="#ref-53">[53]</a> Hygrothermal regulation model | Indoor humidity, temperature and HVAC power | Couple heat and moisture dynamics to equipment limits to estimate available regulation |
| <a href="#ref-54">[54]</a> HVAC–microclimate coupling | Urban canopy and envelope temperatures | Model heat exchange among AC units, façades and outdoor air when allocating response capacity |
| <a href="#ref-55">[55]</a> RC network with boundary-based clustering | Hourly heating and cooling loads | Group elements with similar boundaries and represent shared walls with controlled sources |
| <a href="#ref-56">[56]</a> Piecewise-linear virtual storage aggregation | Equivalent indoor temperature for each building and flexibility of the building fleet | Fit building-specific thermal responses, aggregate feasible power and disaggregate schedules |
| <a href="#ref-57">[57]</a> Economic MPC with RC and neural models | Zone temperature and HVAC cost | Solve RC-MPC by linear programming and ANN-MPC by projected stochastic gradient descent |
| <a href="#ref-58">[58]</a> Deep Q-network for multiple VAV boxes | Zone temperature and HVAC energy | Use a joint multi-zone action and penalize comfort violations and equipment cycling |
| <a href="#ref-59">[59]</a> Neural differential equations and MPC | Temperature and HVAC power | Learn continuous-time dynamics from meter data for temperature-setpoint planning |
| <a href="#ref-60">[60]</a> PDE-constrained learning and control | Spatial airflow, temperature and CO₂ | Fit airflow and transport equations and optimize supply air using adjoint gradients |
| <a href="#ref-61">[61]</a> Coupled dwelling and urban climate model | Dwelling overheating during heatwaves | Drives TRNSYS–CONTAM thermal and airflow simulations with urban weather generated by UWG |
| <a href="#ref-62">[62]</a> Four-storage-unit grey-box model | Mean indoor air temperature | Sensitivity screening and progressive dimension reduction identify essential parameters |
| <a href="#ref-63">[63]</a> Multi-objective room MPC | Room temperature and radiator water flow | A physical room predictor trades off comfort, energy and hydraulic stability |
| <a href="#ref-64">[64]</a> Distributed thermal-load coordination | Zone thermal state of charge | Use consensus among neighboring zones to allocate power cuts or hot-water flows |
| <a href="#ref-65">[65]</a> Neural ODE energy-hub MPC | Multi-zone retail temperatures | Combine a neural thermal model with a linearized energy hub for predictive control |
| <a href="#ref-66">[66]</a> Privacy-preserving aggregate regression | Aggregate indoor temperature | Estimate thermal parameters with encrypted block-coordinate updates and secure aggregation |
| <a href="#ref-67">[67]</a> Energy and reserve co-scheduling | Indoor air and building-mass temperatures | Include expected tracking and discomfort costs when scheduling HVAC reserve |
| <a href="#ref-68">[68]</a> Digital-twin dispatch with model and data fusion | Thermal flexibility of controlled loads | Combine temperature-state and equivalent-storage models for rolling dispatch |
| <a href="#ref-69">[69]</a> Parametric phase-change envelope model | Thermal performance indices | Fit two equations to a validated enthalpy model of PCM walls and roofs |
| <a href="#ref-70">[70]</a> Physically consistent deep learning and MPC | Zone temperatures and HVAC energy | Constrain the thermal network’s response to inputs and embed it in an MPC controller |
| <a href="#ref-71">[71]</a> Hybrid hygrothermal model and adaptive control | Zone air temperature and humidity | Combine heat and moisture balances with local data-driven linearization |
| <a href="#ref-72">[72]</a> Price–storage control in a multizone RC environment | Room temperature and heating cost | Select room heating actions from prices, thermal storage and occupant preferences |
| <a href="#ref-73">[73]</a> Dwelling stock thermal-mass model | Time-limited heating flexibility | Estimate cooldown and heat loss by dwelling group and aggregate flexible electric heat |
| <a href="#ref-74">[74]</a> Graph-recurrent HVAC control | Spatial indoor air temperature | Combines HVAC telemetry, sensor positions and building geometry in a graph for online control |
| <a href="#ref-75">[75]</a> MITP-Net | Multi-zone indoor temperatures | Fuses HVAC state, occupancy and indoor/outdoor measurements in an encoder–decoder |
| <a href="#ref-76">[76]</a> Site-specific artificial neural networks | Indoor air temperature and thermal comfort | Maps outdoor forecasts, sun position and calendar information to indoor conditions |
| <a href="#ref-77">[77]</a> Subspace identification with adaptive MPC | Room temperature and heat-station operation | Fit a nonlinear multi-input model to heating-network and weather measurements |
| <a href="#ref-78">[78]</a> Transient phase-change envelope model | Indoor temperature and comfort hours | Vary layer thickness, melting temperature and number of layers in a passive building |
| <a href="#ref-79">[79]</a> Radiator-network digital twin | Room and supply-water temperatures | Couple EnergyPlus and MATLAB and feed predicted room temperature back to supply control |
| <a href="#ref-80">[80]</a> Price-responsive MPC for floor heating | Heating schedule and indoor temperature | A thermal RC state-space model coordinates slab storage with prices and rooftop PV |
| <a href="#ref-81">[81]</a> Two-level water- and air-loop control | Zone, wall and water temperatures | Set water-side operation every five minutes and adjust fans for fast regulation |
| <a href="#ref-82">[82]</a> Two-step 2R1C identification | Envelope conductance, ventilation and heat capacity | Separate parameter groups using enthalpy differences, least squares and an analytic solution |
| <a href="#ref-83">[83]</a> Second-order residential RC model | Air and interior wall-surface temperatures | Estimate two-node model parameters by least squares and optimization search |
| <a href="#ref-84">[84]</a> RC identification with alternative occupancy inputs | Room temperature and occupant heat gains | Vary RC order and occupancy proxies, then test predictive and control performance |
| <a href="#ref-85">[85]</a> Continuous-time stochastic thermal model and LQG control | Temperature under solar disturbances | Embed stochastic disturbance forecasts in the controller |
| <a href="#ref-86">[86]</a> MPC with a linear phase-change wallboard model | Space heating and thermal storage | Optimize heating using wallboard dynamics and time-varying electricity prices |
| <a href="#ref-87">[87]</a> PhysNet and physics-regularized MLP | Room temperature | Encode approximate heat-transfer relations in the architecture or training objective |
| <a href="#ref-88">[88]</a> Attention-based LSTM encoder–decoder | Indoor air temperature | Uses multi-head attention and Bayesian hyperparameter selection for short-term forecasts |
| <a href="#ref-89">[89]</a> Multi-objective EnergyPlus calibration | Hourly room temperature and overheating | Screens parameters by variance sensitivity and uses a genetic algorithm to fit several rooms |
| <a href="#ref-90">[90]</a> CFD with ensemble Kalman filtering | Air velocity and temperature fields | Assimilates local observations to correct fields affected by uncertain boundary conditions |
| <a href="#ref-91">[91]</a> Lattice Boltzmann with data assimilation | Transient room temperature field | Updates the simulated field with 3D variational assimilation or ensemble Kalman filtering |
| <a href="#ref-92">[92]</a> Grey-box models with sensor dynamics | Next-day indoor temperature and thermal parameters | Compares time shifts, filters and sensor-response models in deterministic and stochastic identification |
| <a href="#ref-93">[93]</a> Coupled radiator and hydraulic network | Room temperature and terminal flow | Solve radiator heat storage, pipe hydraulics and multi-room heat transfer together |
| <a href="#ref-94">[94]</a> CFD coupled to a building energy model | Vertical air temperature and adjacent-zone load | Derive stratification and surface convection coefficients for the atrium energy balance |
| <a href="#ref-95">[95]</a> Reduced-order RC with effective thermal capacitance | Hourly heating and cooling demand | Identify effective capacitance by particle swarm optimization before testing load shifting |
| <a href="#ref-96">[96]</a> Nonlinear space-heating MPC | Indoor temperature and heating peak | Optimize against weather, occupancy and price using the building’s thermal mass |
| <a href="#ref-97">[97]</a> Single-zone ventilation and thermal mass model | Indoor air temperature | A simplified predictor includes thermal storage during natural ventilation |
| <a href="#ref-98">[98]</a> Ventilated-floor thermal network | Heating demand and thermal comfort | A reduced network couples floor storage and room heat transfer under fan operation |
| <a href="#ref-99">[99]</a> Semidefinite flexibility optimization | Indoor and wall temperatures | Couple an RC building model to HVAC equipment and solve for feasible peak reductions |
| <a href="#ref-100">[100]</a> Aggregate thermal regression | Building or cluster temperature | Map zone states to an aggregate state and fit a constrained regression by block updates |



## Datasets

This section describes the measured and simulated data used in the studies. It summarizes the building type, data source and evaluation setup, including sampling intervals, training and test periods, and forecast horizons where reported.


| Study | Building data | Evaluation setup |
| --- | --- | --- |
| <a href="#ref-1">[1]</a> SMC | DOE 22-zone hotel · EnergyPlus · 15 min | June training, July test · 8 h control horizon |
| <a href="#ref-2">[2]</a> DW_ada | 32 DOE buildings, 8 types · EnergyPlus · 15 min | June–July training, August test on the same buildings |
| <a href="#ref-3">[3]</a> Residential 2R2C | 220 Dutch homes · 1-min measurements resampled to 10 min · hourly inputs for model fitting | 187 models validated on a separate 10-day period |
| <a href="#ref-4">[4]</a> Single-zone PCNN | Swiss NEST/UMAR apartment · one bedroom · 15 min | Nearly 2,000 three-day validation windows |
| <a href="#ref-5">[5]</a> X-PCNN | Swiss NEST/UMAR apartment · two bedrooms and a living room · 15 min | Over 750 three-day validation windows with known inputs |
| <a href="#ref-6">[6]</a> Context-aware Transformer | 18 Swedish training buildings · 15-min measurements resampled to hourly inputs | Piteå low-rise test subset · 6 h forecast |
| <a href="#ref-7">[7]</a> PhysCon | Two experimental rooms · heavy and light thermal mass | Held-out day · 5 min ahead |
| <a href="#ref-8">[8]</a> Fully adaptive MPC | Oslo house · IDA ICE–MATLAB simulation | November–December · 61 days · 15 min control interval |
| <a href="#ref-9">[9]</a> Weather-adaptive 4R3C | Ningbo office · simulator calibrated on 5 min measurements | Four-day simulated cold snap |
| <a href="#ref-10">[10]</a> Internal-mass model | Test room · surface and internal temperature sensors | 30 days of measurements |
| <a href="#ref-11">[11]</a> ETP + TimesNet and two-stage control | CU-BEMS measurements, Chamchuri 5, Bangkok | Simulated control of zone 4 on two floors |
| <a href="#ref-12">[12]</a> Adaptive grey-box identification | Two measured office datasets with radiator heating | Two weeks to identify, then two weeks of updates |
| <a href="#ref-13">[13]</a> Bottom-up heat-pump fleet model | Swiss monitoring of heat loss, cooldowns and 243 residential heat pumps | Simulated curtailment at different outdoor temperatures |
| <a href="#ref-14">[14]</a> Physics-consistent neural model and differentiable control | EnergyPlus five-zone office with bio-based phase-change materials | Six US climates, typical summer and extreme heat |
| <a href="#ref-15">[15]</a> Greenhouse heat-balance model | UPC rooftop greenhouse, Spain · measured with and without crops | 70 combinations of training and validation data |
| <a href="#ref-16">[16]</a> Multi-branch CNN–LSTM | Office sensor readings and door, window and HVAC operating states | Spatially clustered office zones |
| <a href="#ref-17">[17]</a> Coupled BES–CFD | Full-scale open-plan office with radiant and convective HVAC · measured temperatures | Heating and cooling seasons · multiple measurement locations |
| <a href="#ref-18">[18]</a> Transient Block–Gebhart model | Two large-space buildings · measured air and wall temperatures and cooling loads | Seven operating cases in two buildings |
| <a href="#ref-19">[19]</a> EnergyPlus internal-mass plugin | Published field measurements of zone air temperature and EnergyPlus simulations | Validate on site time series and compare night cooling across months |
| <a href="#ref-20">[20]</a> Finite-difference thermal storage model | Demand-response tests in a 10 m² Hong Kong Polytechnic University room plus simulations | Compare measured responses of different mass components and run global sensitivity analysis |
| <a href="#ref-21">[21]</a> Bayesian-optimized TCN–LSTM with self-attention | Measured wall and environmental time series from housing in Harbin, China | Test four input configurations and compare estimators on the same case |
| <a href="#ref-22">[22]</a> Thermally activated slab model with Taguchi optimization | Two on-site heating and cooling response tests and simulated system designs | Validate water, slab and room response before testing optimized settings |
| <a href="#ref-23">[23]</a> 5R3C simulation with a deep Q-network | Measured dwelling heat use and living-room temperature plus calibrated simulations | Train in simulation and evaluate seven days of online control with weather normalization |
| <a href="#ref-24">[24]</a> Dynamically weighted physics-informed LSTM | Laboratory air-based thermally activated building system, ventilated and unventilated | Compare dynamic and fixed physics-loss weights across ventilation conditions |
| <a href="#ref-25">[25]</a> Dynamic heating-curtailment simulation | Simulated urban buildings with different envelope standards and weather conditions | Track temperature as heat supply is reduced or delayed |
| <a href="#ref-26">[26]</a> Zone-level virtual batteries | Five-zone commercial building with CityLearn weather and thermal disturbances | 30 min steps · 30 trials per commitment window |
| <a href="#ref-27">[27]</a> Chilled-water storage model | High-fidelity commercial HVAC simulation | Demand response scenarios with and without chilled-water storage |
| <a href="#ref-28">[28]</a> Stepwise scheduling reformulation | 100-zone building prototype · simulation | Online scheduling under uncertain prices and thermal dynamics |
| <a href="#ref-29">[29]</a> Physics-informed primal–dual control | Four synthetic thermal series and three datasets with measured external inputs | Also tested on coupled plants of up to 256 zones |
| <a href="#ref-30">[30]</a> Uncertainty-aware flexibility model | Swiss NEST/UMAR apartment · measurements and EnergyPlus digital twin | German reserve prices · alternative comfort bands and confidence levels |
| <a href="#ref-31">[31]</a> Adaptive physically consistent neural network | Six months of real data-centre records and a simulated dataset | MLP and LSTM bases, 15-min to 7-day horizons |
| <a href="#ref-32">[32]</a> EnergyPlus with neural residual correction | Five measured rooms in the Swiss NEST UMAR apartment and EnergyPlus | 15-min series, 2020 training and 2021 testing |
| <a href="#ref-33">[33]</a> Nonlinear RC network and deep reinforcement learning | Simulated radiative roof, thermochromic windows and combined envelope | Three passive-envelope configurations |
| <a href="#ref-34">[34]</a> Physics-aware graph network and MPC | EnergyPlus commercial building with coupled air and water loops | Simulated demand response with weather and occupancy inputs |
| <a href="#ref-35">[35]</a> Modular reinforcement learning with a PCNN simulator | Swiss NEST building measurements and simulations | Room-to-room transfer with a few weeks of target data |
| <a href="#ref-36">[36]</a> Ontology-based digital twin | One hospital floor, 12 HVAC zones and 45 sensor channels | Field validation of the automatically generated model |
| <a href="#ref-37">[37]</a> Causal machine learning | Simulated RC building and operational records from nine Dutch buildings | Heating interventions and SHAP analysis |
| <a href="#ref-38">[38]</a> Genetic programming with closed-loop identification | EnergyPlus non-domestic building · simulated commissioning and operating data | Eight successive model updates · independent 2017 test year |
| <a href="#ref-39">[39]</a> Adaptive graph convolution | Beijing multi-occupant office · ten days of measurements at 39 positions | Estimate the full field with a reduced sensor network |
| <a href="#ref-40">[40]</a> Single-mass subspace model (N4SID) | Seven-storey Harbin apartment block, 105 flats · four monitored rooms | Rolling versus cumulative training · multiple forecast windows |
| <a href="#ref-41">[41]</a> CFD with ensemble Kalman filtering | Full-scale residential room · numerical experiments and field measurements | Sensor locations and measurement configurations varied |
| <a href="#ref-42">[42]</a> Equivalent solar heat source and CNN | Tianjin University full-scale office chamber · CFD reference fields | Changing solar patches and previously unseen boundary conditions |
| <a href="#ref-43">[43]</a> Response-coefficient CNN | Tianjin University office test-platform case · reference CFD fields | Transient heat sources in an office HVAC control case |
| <a href="#ref-44">[44]</a> Gated multitask BiLSTM | Measured office temperature and humidity at multiple positions | 24 h ahead · complete training set and reduced data at one point |
| <a href="#ref-45">[45]</a> 2R2C-informed neural network | Historical operating data from a measured case building | Multi-step predictions with varied training length and regularization |
| <a href="#ref-46">[46]</a> Chance-constrained stochastic MPC | Office building in Xi’an, China · field control experiment | On/off, deterministic MPC and stochastic MPC comparisons |
| <a href="#ref-47">[47]</a> Humidity-enhanced RC mapping | Cooling-curtailment measurements from a large public building | Compare measured temperatures during demand response with two RC models |
| <a href="#ref-48">[48]</a> Probabilistic equivalent-thermal-parameter model | Shenzhen public-building temperature and setpoint records plus simulated cases | Evaluate building-specific comfort bounds and available capacity at different confidence levels |
| <a href="#ref-49">[49]</a> Noise-robust recursive RC identification | 354 m² office in Foshan, China · measured temperatures and cooling power calculated by the variable refrigerant flow (VRF) system | Test a second-order RC model with noisy measurements |
| <a href="#ref-50">[50]</a> Analytical shedding and rebound | Numerical building and aggregation cases | Vary regulation duration and permitted indoor temperature offset |
| <a href="#ref-51">[51]</a> Decision-oriented neural ODE | EnergyPlus · DOE house, mall, office, hotel and apartment | 15 min · train June–July, test August · up to 90 zones |
| <a href="#ref-52">[52]</a> Latent-state optimization | EnergyPlus · DOE 90-zone apartment and augmented 1,080-zone case | Train June–July, test August |
| <a href="#ref-53">[53]</a> Hygrothermal regulation model | Building HVAC case with weather, solar radiation and occupancy inputs | Day and night scenarios · simulated reserve deployment |
| <a href="#ref-54">[54]</a> HVAC–microclimate coupling | Macau Peninsula GIS · 4,739 buildings and satellite atmospheric data | Urban block simulations with and without AC heat feedback |
| <a href="#ref-55">[55]</a> RC network with boundary-based clustering | Four single-zone ASHRAE 140 cases and two multizone urban cases | Benchmark tests against EnergyPlus |
| <a href="#ref-56">[56]</a> Piecewise-linear virtual storage aggregation | 80 EnergyPlus buildings from four US DOE archetypes | Hourly, July 1–31 · day-ahead fleet dispatch and building-level allocation |
| <a href="#ref-57">[57]</a> Economic MPC with RC and neural models | BOPTEST simulated single-zone dwelling | Identical benchmark for the two MPC designs |
| <a href="#ref-58">[58]</a> Deep Q-network for multiple VAV boxes | OpenStudio simulation of a Greenville, South Carolina open-plan office | Six zones sharing open air boundaries |
| <a href="#ref-59">[59]</a> Neural differential equations and MPC | Two EnergyPlus residential prototypes and measurements from five commercial buildings in eastern Canada | Two-hour temperature forecasts on commercial building data with irregular or missing samples · winter demand-response simulation in a cold-climate residential prototype |
| <a href="#ref-60">[60]</a> PDE-constrained learning and control | UC Berkeley CO₂ measurements and numerical simulations | Use measurements to model the spatial CO₂ field and simulations to compare ventilation policies under comfort and air-quality constraints |
| <a href="#ref-61">[61]</a> Coupled dwelling and urban climate model | Renovated multifamily dwelling, Lyon · summer 2022 field measurements | Calibrated model subjected to future urban heatwave scenarios |
| <a href="#ref-62">[62]</a> Four-storage-unit grey-box model | Heating buildings connected to one secondary network with mean indoor-temperature records | Fit the lumped heat-storage parameters and evaluate predicted indoor temperature |
| <a href="#ref-63">[63]</a> Multi-objective room MPC | 15-minute measurements from an office in Espoo, Finland and a calibrated CARNOT room model | Evaluate simulated closed-loop control at a 15-minute interval with a 90-minute horizon |
| <a href="#ref-64">[64]</a> Distributed thermal-load coordination | Simulated residential inverter AC and commercial hydronic heating | Five-zone allocation test · emergency demand response scenarios |
| <a href="#ref-65">[65]</a> Neural ODE energy-hub MPC | Simulated multi-zone retail building | Temperature prediction and price-responsive operation |
| <a href="#ref-66">[66]</a> Privacy-preserving aggregate regression | REFIT Smart Home · seven UK households · 30 min | 1,080 training observations and 360 test observations |
| <a href="#ref-67">[67]</a> Energy and reserve co-scheduling | DOE medium office · PJM prices and New Jersey solar/weather data | Hourly market scheduling with intra-hour deployment |
| <a href="#ref-68">[68]</a> Digital-twin dispatch with model and data fusion | Simulated thermostatically controlled loads | Inject parameter errors and state noise separately |
| <a href="#ref-69">[69]</a> Parametric phase-change envelope model | 2,401 numerical envelope configurations | Compare approximate and numerical indices |
| <a href="#ref-70">[70]</a> Physically consistent deep learning and MPC | Simulation of Cornell University’s Carpenter Hall office building | Multizone control against three alternative controllers |
| <a href="#ref-71">[71]</a> Hybrid hygrothermal model and adaptive control | Multizone HVAC case with air handlers and fan-coil units | Model validation and setpoint step-response tests |
| <a href="#ref-72">[72]</a> Price–storage control in a multizone RC environment | Simulated multizone winter heating | Two comfort-band scenarios and two thermal capacities |
| <a href="#ref-73">[73]</a> Dwelling stock thermal-mass model | England and Wales EPC, SAP 2012 and UKERC heat-demand data | Hypothetical fully electrified residential heating stock |
| <a href="#ref-74">[74]</a> Graph-recurrent HVAC control | High-rise office · building automation, BIM and IoT data from an AHU–VAV system | Cloud-based trial on the operating air-conditioning system |
| <a href="#ref-75">[75]</a> MITP-Net | Public multi-zone office dataset · two weeks of operation at one-minute intervals | Eleven ablations · variable input and forecast lengths |
| <a href="#ref-76">[76]</a> Site-specific artificial neural networks | 121 monitored workplaces across agriculture, industry, warehousing and offices | One year of measurements · next-24-hour forecasts |
| <a href="#ref-77">[77]</a> Subspace identification with adaptive MPC | Residential heat-station operating records, indoor temperatures and weather data | Compare MPC variants and PID, including extreme-weather scenarios |
| <a href="#ref-78">[78]</a> Transient phase-change envelope model | Simulated passive building in China’s hot-summer, cold-winter climate zone | Compare annual comfort over alternative phase-change material layouts |
| <a href="#ref-79">[79]</a> Radiator-network digital twin | Six-storey, 12-flat building with four indoor-temperature sites and network water measurements | Compare feedback control with weather compensation in a validated secondary network |
| <a href="#ref-80">[80]</a> Price-responsive MPC for floor heating | Six days of measured weather and room temperature plus TRNSYS scenarios for London | Compare thermal masses, occupancy, water temperatures and future climate scenarios |
| <a href="#ref-81">[81]</a> Two-level water- and air-loop control | Commercial HVAC · MATLAB and Dymola co-simulation | 5 min energy-market signals · 4 s regulation signals |
| <a href="#ref-82">[82]</a> Two-step 2R1C identification | Field experiment in a 354.3 m² office test room in Foshan, China | Identify thermal characteristics during cooling operation |
| <a href="#ref-83">[83]</a> Second-order residential RC model | Measurements from an instrumented test home | 24-hour air-temperature forecasts with seasonal training |
| <a href="#ref-84">[84]</a> RC identification with alternative occupancy inputs | Measurements and simulations for offices, a classroom and a multizone floor | No occupancy input, schedules, power, CO₂ or ideal sensing |
| <a href="#ref-85">[85]</a> Continuous-time stochastic thermal model and LQG control | Simulated residential thermal model with measured weather | Compare embedded disturbance and persistence forecasts |
| <a href="#ref-86">[86]</a> MPC with a linear phase-change wallboard model | Simulated single-family house with PCM wallboards | Price-responsive heating with and without wallboards |
| <a href="#ref-87">[87]</a> PhysNet and physics-regularized MLP | Single-family home simulation and measured cold-storage facility | Vary training length and forecast horizon |
| <a href="#ref-88">[88]</a> Attention-based LSTM encoder–decoder | First-floor room in Yizheng, China · five-minute measurements, Sep–Oct 2020 | Short-term forecasts compared with LSTM and GRU |
| <a href="#ref-89">[89]</a> Multi-objective EnergyPlus calibration | Existing Canadian school · hourly room measurements and EnergyPlus output | Calibrated model checked against hourly indoor temperatures |
| <a href="#ref-90">[90]</a> CFD with ensemble Kalman filtering | Reduced-scale room experiments · measured flow and temperature under two airflow regimes | Mechanical ventilation and natural convection · sensor layout and ensemble size varied |
| <a href="#ref-91">[91]</a> Lattice Boltzmann with data assimilation | Idealized numerical room with synthetic sensor readings | Five changing window boundary conditions · one to five virtual sensors |
| <a href="#ref-92">[92]</a> Grey-box models with sensor dynamics | Highly insulated residence · measured room temperatures and heating signals | One-day-ahead tests across sampling intervals and preprocessing options |
| <a href="#ref-93">[93]</a> Coupled radiator and hydraulic network | Simulated multi-room radiator network with flow and supply-temperature scenarios | Compare terminal flow control, proportional control and on/off control |
| <a href="#ref-94">[94]</a> CFD coupled to a building energy model | Daytime measurements at a Nanjing transport-station atrium and seasonal simulations | Vary atrium height, glazing and season and check the modeled stratification |
| <a href="#ref-95">[95]</a> Reduced-order RC with effective thermal capacitance | Simulated buildings with three thermal capacitances in four Chinese climate zones | Compare precooling and preheating scenarios over one day |
| <a href="#ref-96">[96]</a> Nonlinear space-heating MPC | Simulation of a central Norwegian university building, with a lightweight sensitivity case | Benchmark the controller against the building’s existing rule-based strategy |
| <a href="#ref-97">[97]</a> Single-zone ventilation and thermal mass model | Seasonal measurements from lightweight and medium-weight test buildings in Dalian, China | Compare predictions with measured indoor temperature for both mass levels |
| <a href="#ref-98">[98]</a> Ventilated-floor thermal network | On-site measurements in a ventilated electric-floor test room plus supply scenarios | Vary floor geometry and fan operation with grid-only and wind-assisted supply |
| <a href="#ref-99">[99]</a> Semidefinite flexibility optimization | Single-zone building model · manufacturer equipment curves | Typical summer day · flexibility calculations at operating points |
| <a href="#ref-100">[100]</a> Aggregate thermal regression | Multi-zone building and building-cluster cases using real-world data | Separate simulations of individual-building and cluster control |

## Reported results

This section organizes the reported results into six categories. Each entry presents an outcome together with its evaluation conditions, metric and within-study comparison where available.

[Prediction accuracy](#prediction-accuracy) · [Model validation](#model-validation) · [Control performance](#control-performance) · [Thermal response and flexibility](#thermal-response-and-flexibility) · [Computation time](#computation-time) · [Qualitative findings](#qualitative-findings)

### Prediction accuracy

This section summarizes prediction errors for indoor temperatures and related thermal quantities. Results are listed with the forecast horizon, error metric and comparison method where reported.

| Study and case | Prediction metric | Reported result | Within-study reference |
| --- | --- | --- | --- |
| <a href="#ref-1">[1]</a> hotel, July | Zone temperature RMSE (°C) | 0.2288 | 0.1395 · MSE-trained model |
| <a href="#ref-2">[2]</a> six new setpoint schedules | Mean building RMSE (°C)| 1.1861 | 1.3585 · independent local models |
| <a href="#ref-4">[4]</a> 1 h ahead | MAE at forecast lead (°C) | 0.31 | 0.19 · RC model |
| <a href="#ref-4">[4]</a> 72 h ahead | MAE at forecast lead (°C) | 0.88 | 1.48 · RC model |
| <a href="#ref-5">[5]</a> three rooms | Best-run MAE over 72 h (°C) | 1.17 | 1.27 · LSTM |
| <a href="#ref-6">[6]</a> Piteå low-rise, 6 h | R² | 0.946 | 0.803 · pooled Transformer |
| <a href="#ref-7">[7]</a> heavy-mass room, 5 min | Room temperature MAE (°C) | 0.25 | 0.47 · unconstrained neural network |
| <a href="#ref-9">[9]</a> cold snap | Zone temperature RMSE (°C) | 0.259 | 0.344 · fit on the latest three days |
| <a href="#ref-12">[12]</a> 24-hour validation, dataset 1, configuration 2 | Average temperature NRMSE | ≈0.39 | PRBS-identified model ≈0.54 |
| <a href="#ref-15">[15]</a> Greenhouse with crops | Temperature RMSE | 2.0 °C | 2.2 °C in the study’s no-crop case |
| <a href="#ref-16">[16]</a> Office zones | Air-temperature RMSE | 0.23 °C | Measured zonal temperatures |
| <a href="#ref-21">[21]</a> Harbin residential wall | Heat-flux RMSE reduction | 25.0% | Standard LSTM |
| <a href="#ref-24">[24]</a> Air-based thermally activated system | Room-temperature RMSE reduction | 14.6% | Best fixed-weight PINN (weight 0.6) |
| <a href="#ref-31">[31]</a> Measured data, MLP base, 7-day horizon | Temperature MAE reduction | 79.2% | Fixed-coefficient PCNN |
| <a href="#ref-32">[32]</a> Five rooms · fullest sensor and documentation coverage | Room-temperature MAE | 0.85 °C | 1.25 °C · EnergyPlus / 0.92 °C · standalone neural network |
| <a href="#ref-33">[33]</a> Radiative roof and thermochromic windows | Thermal-response R² | 0.95 | 0.88 · global parameter identification |
| <a href="#ref-39">[39]</a> 82% fewer sensors | Temperature RMSE | 0.35 °C | Monitored office temperature field |
| <a href="#ref-40">[40]</a> Harbin apartment block | Indoor-temperature MAPE | 1.5–2.6% | Measured indoor temperatures |
| <a href="#ref-44">[44]</a> Three office floors · 24 h · full training set | Mean temperature MAE | 0.436 °C | Measured floor temperatures |
| <a href="#ref-45">[45]</a> Multi-step indoor temperature | RMSE | 0.94 °C | 1.27 °C · neural network / 1.91 °C · standalone 2R2C |
| <a href="#ref-47">[47]</a> Public-building cooling curtailment | Indoor-temperature RMSE | 0.118 °C | 0.737 °C with the conventional RC model |
| <a href="#ref-49">[49]</a> Noisy office measurements | Indoor-temperature MAE | 0.48 °C | Recorded indoor temperatures |
| <a href="#ref-51">[51]</a> 67-zone hotel · test period | RMSE of indoor temperature weighted by zone air mass (°C) | 0.3717 | 0.3779 · conventional model-then-optimize |
| <a href="#ref-52">[52]</a> 1,080-zone case · test set | Temperature RMSE (°C) | 0.3520 | 0.5605 · identification in original variables |
| <a href="#ref-62">[62]</a> Heating-network buildings | Mean absolute indoor-temperature error | 0.1 °C | Mean indoor air temperature in the case study |
| <a href="#ref-66">[66]</a> Seven-home aggregate · test set | Aggregate-state RMSE (°C) | 0.2944 | 0.2741 · non-private fit |
| <a href="#ref-75">[75]</a> Multi-zone office · 10 min ahead | Forecasts within 0.5 °C of measurements | &gt;80% in every test set | Both MITP-Net fusion methods |
| <a href="#ref-76">[76]</a> Workplaces, next 24 h | Average air-temperature MAE | 0.87 K | Measured indoor air temperatures |
| <a href="#ref-83">[83]</a> Aug 13–24, 2020 · parameters identified in the transition season | 24-hour air-temperature RMSE | 0.62 °C · optimal-search identification | 0.65 °C · least-squares identification on the same test period |
| <a href="#ref-87">[87]</a> Simulated single-family home | Room-temperature MAE | PhysNet 0.226 °C · PhysReg MLP 0.197 °C | 0.209 °C · standard MLP |
| <a href="#ref-88">[88]</a> Monitored room | R² | &gt;0.9 | Measured room temperatures |
| <a href="#ref-97">[97]</a> Naturally ventilated test buildings | Maximum indoor-temperature error | About 1.5 °C | Measured temperatures |
| <a href="#ref-100">[100]</a> Multi-zone building | Aggregate-state RMSE (°C) | &lt;0.72 | — |
| <a href="#ref-100">[100]</a> Building cluster | Aggregate-state RMSE (°C) | &lt;0.32 | — |



### Model validation

This section summarizes how the studies validated their thermal models against measurements or reference simulations. Each entry identifies the quantity evaluated, the validation metric and the reference used.

| Study and case | Validation metric | Reported result | Within-study reference |
| --- | --- | --- | --- |
| <a href="#ref-3">[3]</a> 187 Dutch homes | Indoor temperature RMSE | 0.54 °C (mean) | Independent ten-day measurements |
| <a href="#ref-10">[10]</a> Test-room thermal mass | Internal-mass temperature RMSE | 0.9 °C | Embedded temperature sensors |
| <a href="#ref-17">[17]</a> Both seasons, all locations | Temperature CV(RMSE) | &lt;2% | Full-scale measurements |
| <a href="#ref-18">[18]</a> Seven operating cases in two large buildings | Air-temperature MAE | 1.1 °C in each set | Measured temperatures |
| <a href="#ref-36">[36]</a> Hospital temperature sensors | Mean of the individual sensors’ temperature MAEs | 0.40 °C | Measured temperatures |
| <a href="#ref-41">[41]</a> Temperature-field reconstruction | RMSE reduction | About 69.8% | CFD without assimilation |
| <a href="#ref-42">[42]</a> Dynamic solar-gain cases | Temperature-field RMSE | 0.33 °C | Reference CFD solution |
| <a href="#ref-43">[43]</a> Transient office field | Temperature-field MAE | 0.27 °C | CFD temperature field |
| <a href="#ref-55">[55]</a> ASHRAE 140 Case 600 | Relative error in reported load results | Within 7.5% | EnergyPlus |
| <a href="#ref-69">[69]</a> PCM envelope configurations | Mean relative error | 7.7% | Numerical enthalpy model |
| <a href="#ref-82">[82]</a> Air heat capacity in the test room | Relative identification error | 3.31% | Experimental reference |
| <a href="#ref-89">[89]</a> School temperature calibration | Temperature RMSE | 0.3 °C | Measured hourly temperatures |
| <a href="#ref-98">[98]</a> Ventilated-floor test room | Upper floor-surface temperature MAPE | 3.3% | On-site measurements |
| <a href="#ref-98">[98]</a> Ventilated-floor test room | Indoor-air temperature MAPE | 3.8% | On-site measurements |

### Control performance

This section summarizes the operational performance of HVAC control methods. Reported outcomes include energy use, operating cost, thermal comfort and demand response performance under the conditions evaluated in each study.

| Study and case | Control outcome | Reported result | Within-study reference |
| --- | --- | --- | --- |
| <a href="#ref-1">[1]</a> hotel, July | Mean daily control cost| 1,017.18 | 1,037.31 · open-loop MPC |
| <a href="#ref-2">[2]</a> August price response | Mean monthly cost per building ($) | 2,418.14 | 2,572.73 · local models |
| <a href="#ref-8">[8]</a> 61 days | Cumulative discomfort (K·h) | 50.68 | 210.74 · fixed FullWinter MPC |
| <a href="#ref-8">[8]</a> same run | Energy use (kWh) | 353.89 | 328.56 · fixed FullWinter MPC |
| <a href="#ref-11">[11]</a> Simulated HVAC control | Deviation from preferred temperature | Within 0.5 °C | Occupants’ preferred temperatures |
| <a href="#ref-13">[13]</a> Four-hour event at 0 °C outdoors | Heat-pump power reduction | Up to 90% | Setpoint adjustment against baseline operation |
| <a href="#ref-14">[14]</a> Minneapolis, Q25 material with predictive control | Peak demand reduction | 37.84% | Baseline without phase-change material |
| <a href="#ref-22">[22]</a> Optimized heating design, simulation | Reduction in unmet-hour ratio | Up to 58.3% | Best-performing case in the initial design set |
| <a href="#ref-23">[23]</a> Seven-day field deployment | Heating-energy savings | 15.9% | Conventional on/off controller, weather-normalized |
| <a href="#ref-26">[26]</a> Five-zone building · one-day commitment | Mean electricity cost ($) | 61.08 | 57.71 · optimal RC schedule |
| <a href="#ref-29">[29]</a> Synthetic and measured-input cases | Cumulative comfort violation | 26–56% lower | Online convex controllers without thermal structure |
| <a href="#ref-35">[35]</a> Simulated transfer to bedroom 274 and living room 273 | Heating energy saving | ≈26% on average (32% in the bedroom and 19% in the living room) | Rule-based control |
| <a href="#ref-38">[38]</a> Fourth model update, test year | Temperature outside comfort band | 699.0 °C·min | 6,143.5 °C·min with on/off control |
| <a href="#ref-46">[46]</a> Office field experiment | Energy use | 39.1% lower | On/off control |
| <a href="#ref-46">[46]</a> Same office field experiment | Energy use | 33.3% lower | Deterministic MPC |
| <a href="#ref-51">[51]</a> 67-zone hotel · test period | Control cost | 0.66% lower | Conventional model-then-optimize |
| <a href="#ref-57">[57]</a> Single-zone dwelling, both MPC approaches | Energy-cost saving | 17–34% | Rule-based controller |
| <a href="#ref-58">[58]</a> Six-zone open office | HVAC energy reduction | 37% | Existing building HVAC schedule |
| <a href="#ref-59">[59]</a> Cold-climate EnergyPlus home, winter · controlled differential equation with 8% power slack | Demand-response events satisfied | 18 of 26 (4 infeasible) | 8 of 26 with no slack |
| <a href="#ref-60">[60]</a> Simulated control of supply airflow and temperature | Energy reduction | 7.9% | MPC using ordinary differential equations |
| <a href="#ref-63">[63]</a> Radiator-heated office, co-simulation | Heating-energy reduction | 2.8% | PID control |
| <a href="#ref-68">[68]</a> 15% random thermal-parameter error | Achieved dispatch objective | 98.4% of ideal | Ideal dispatch result |
| <a href="#ref-70">[70]</a> Carpenter Hall simulation | Energy reduction | 8.9% | LSTM-based MPC |
| <a href="#ref-72">[72]</a> High-capacitance winter heating | Electricity-cost reduction | Price–storage control 22% (ideal MPC &gt;39%) | Conventional two-point hysteresis control |
| <a href="#ref-74">[74]</a> Online office trial | Time at Grade I thermal comfort | 81.3% | 36.5% under existing control |
| <a href="#ref-77">[77]</a> Residential heat-station simulation | Energy-use reduction | 20.3% | Actual heating-plant operation |
| <a href="#ref-79">[79]</a> Residential radiator network, simulation | Heating-energy reduction | 5.4% | Weather-compensated supply temperature |
| <a href="#ref-80">[80]</a> Winter simulation, 50 °C inlet | Mean electricity price paid, medium-weight room | 16.15 pence/kWh | 16.75 heavyweight and 18.50 lightweight |
| <a href="#ref-81">[81]</a> Five-minute energy and four-second regulation signals | Room-temperature deviation | Within 0.05 °C | Both two-level and benchmark control |
| <a href="#ref-85">[85]</a> Simulated dwelling, varied objective weights | Realized control-objective savings | 5–26% | Same controller using persistence forecasts |
| <a href="#ref-86">[86]</a> Single-family house with PCM wallboards | Space-heating electricity-cost saving | Over 60% | Conventional control |
| <a href="#ref-93">[93]</a> Multi-room radiator network · simulation | Heating-energy savings | 8.4–13% | Supply-temperature control without terminal flow control |
| <a href="#ref-95">[95]</a> Precooling, four Chinese climate zones | Office-hours cooling-load reduction | 20–45% | Cases without advance cooling |
| <a href="#ref-96">[96]</a> Norwegian university, simulation | Peak heating-load reduction | 8.8% | Existing rule-based control |


### Thermal response and flexibility

This section summarizes how buildings respond to changes in heating, cooling and control settings. Reported quantities include temperature changes, available regulation capacity, peak demand reduction and the duration of load adjustments.

| Study and case | Reported quantity | Reported result | Within-study reference |
| --- | --- | --- | --- |
| <a href="#ref-19">[19]</a> Nighttime cooling of internal thermal mass · 21 working days in September | Mean delay of peak cooling power | 0.8 h | Comparison scenario pending verification |
| <a href="#ref-20">[20]</a> Passive storage · key design and operating factors | Share of each factor’s total effect attributable to interactions | &gt;20% for each factor | — |
| <a href="#ref-25">[25]</a> Simulated heating-supply curtailments | Longest continuous period of downward flexibility across scenarios | 22 h | — |
| <a href="#ref-27">[27]</a> Most simulated demand response scenarios | Estimated demand response potential | More than 2× | Model omitting chilled-water storage |
| <a href="#ref-53">[53]</a> 12:00–13:00 · 80% reserve deployment | Available regulation capacity | ≈10 kW during deployment | ≈55 kW before deployment |
| <a href="#ref-54">[54]</a> High-density Macau block | Increase in maximum canopy temperature | 2.96 °C | Case without AC–microclimate interaction |
| <a href="#ref-64">[64]</a> Five-zone allocation · 50 kW demand response | Iterations for weighted consensus | Within 100 | The aggregate allocation remained at 50 kW |
| <a href="#ref-67">[67]</a> Comfort limits each tightened by 1 °C | Regulation reserve capacity | ≈21% higher | Base-case temperature bounds |
| <a href="#ref-73">[73]</a> Existing stock at −5 °C outside | Potential demand reduction | About 85 GW | About 60 GW after stock efficiency upgrades |
| <a href="#ref-78">[78]</a> Best simulated two-layer envelope | Inner / outer thickness at longest annual comfort duration | 13.3 / 26.7 mm | 40 mm total phase-change material thickness |
| <a href="#ref-94">[94]</a> Adjacent air-conditioned zones | Calculated HVAC load per floor area | 115–146 W/m² | Model includes stratification and CFD-derived convection coefficients |


### Computation time

| Study and case | Timed operation | Reported result | Within-study reference |
| --- | --- | --- | --- |
| <a href="#ref-1">[1]</a> 22-zone hotel<sup>1</sup> | Online MPC solve · 8 h horizon | 1.09 s | 0.93 s · open-loop MPC |
| <a href="#ref-2">[2]</a> 32 buildings<sup>1</sup> | Offline federated training | 414.04 min | 574.31 min · weights updated every round |
| <a href="#ref-99">[99]</a> Single-zone flexibility calculation | Mean solver runtime | 0.0204 s · semidefinite programming | 0.2008 s · IPOPT |

<sub>¹ These two studies used a 3.40 GHz Intel Xeon CPU and 16 GB of RAM.</sub>

### Qualitative findings

This section summarizes reported findings on model behavior, control feasibility and sensitivity to operating conditions. Each entry identifies the evaluation case and the observed effect.


| Study and case | Quantity examined | Reported result | Within-study reference |
| --- | --- | --- | --- |
| <a href="#ref-28">[28]</a> 100-zone prototype | Scheduling speed and cost | Faster online solution while retaining economic optimality | Original coupled scheduling problem |
| <a href="#ref-30">[30]</a> 1 °C comfort range · 70% confidence · intraday trading | Net reserve-market revenue | Positive with feedback | Negative without feedback |
| <a href="#ref-34">[34]</a> Coupled water and air circuits · EnergyPlus | Dispatchable HVAC flexibility | Joint chiller and zone control increased available flexibility | — |
| <a href="#ref-37">[37]</a> Heating interventions | Direction of heating effect | Recovered the expected causal response | Conventional observational predictors |
| <a href="#ref-48">[48]</a> Shenzhen public buildings | Thermal comfort bounds | Identified separately for each building | Historical setpoint records |
| <a href="#ref-50">[50]</a> Single buildings and their aggregate | Load recovery after curtailment | Aggregate rebound depends on the preceding reduction | — |
| <a href="#ref-56">[56]</a> Virtual power plant dispatch | Schedule feasibility | Fleet schedule allocated to individual buildings | Building-level HVAC power limits |
| <a href="#ref-61">[61]</a> Future climate scenarios | Time above 28 °C | Reduced by operating windows and solar protection | Effect varied by future scenario |
| <a href="#ref-65">[65]</a> Multi-zone retail operation | Temperature prediction accuracy | Higher with the neural ODE | RC and conventional neural network models |
| <a href="#ref-71">[71]</a> Temperature and humidity setpoint steps | Steady-state tracking | Converged without steady-state bias | Requested zone setpoints |
| <a href="#ref-84">[84]</a> Classroom internal heat gains | Occupancy proxy inputs | Power and CO₂ were needed together for good performance | Alternative input combinations |
| <a href="#ref-90">[90]</a> Both airflow regimes | Spatial prediction error | Lower with measurement assimilation | Uncorrected CFD |
| <a href="#ref-91">[91]</a> 3D variational assimilation | Temperature-field RMSE | Similar with four and five sensors | A single poorly placed sensor could worsen the estimate |
| <a href="#ref-92">[92]</a> Stochastic model, coarse sampling | Physical plausibility of parameters | Improved by an anti-causal time shift | Low-pass filtering had a smaller effect |

## References

This section lists the full citation and DOI link for each study. Where available, a GitHub link at the end of the citation identifies the associated code, data or simulation model.

<a name="ref-1"></a>[1]. X. Cui, B. Liu, Y. Li, and Y. Wang, “[A “Smart Model-Then-Control” Strategy for the Scheduling of Thermostatically Controlled Loads](https://doi.org/10.1109/tsg.2025.3542544),” *IEEE Transactions on Smart Grid*, vol. 16, no. 3, pp. 2246–2260, 2025. [GitHub (code)](https://github.com/hkuedl/Smart-Model-then-Control)

<a name="ref-2"></a>[2]. X. Cui, D. Qin, J.-F. Toubeau, F. Vallée, and Y. Wang, “[Generalizable Thermal Dynamics Modeling via Personalized Federated Learning](https://doi.org/10.1109/tsg.2025.3585942),” *IEEE Transactions on Smart Grid*, vol. 16, no. 6, pp. 4698–4711, 2025. [GitHub (code)](https://github.com/hkuedl/Federated-Thermal-Dynamics-Modeling)

<a name="ref-3"></a>[3]. I. Pothof, D. Vreeken, and M. van Meerkerk, “[Data-driven method for optimized supply temperatures in residential buildings](https://doi.org/10.1016/j.energy.2023.129183),” *Energy*, vol. 284, Art. no. 129183, 2023.

<a name="ref-4"></a>[4]. L. Di Natale, B. Svetozarevic, P. Heer, and C. N. Jones, “[Physically Consistent Neural Networks for building thermal modeling: Theory and analysis](https://doi.org/10.1016/j.apenergy.2022.119806),” *Applied Energy*, vol. 325, Art. no. 119806, 2022. [GitHub (shared PCNN implementation)](https://github.com/Cemempamoi/pcnn)

<a name="ref-5"></a>[5]. L. Di Natale, B. Svetozarevic, P. Heer, and C. N. Jones, “[Towards scalable physically consistent neural networks: An application to data-driven multi-zone thermal building models](https://doi.org/10.1016/j.apenergy.2023.121071),” *Applied Energy*, vol. 340, Art. no. 121071, 2023. [GitHub (shared PCNN implementation)](https://github.com/Cemempamoi/pcnn)

<a name="ref-6"></a>[6]. S. S. V. Kalidindi, H. Banaee, H. Karlsson, and A. Loutfi, “[Indoor temperature prediction with context-aware models in residential buildings](https://doi.org/10.1016/j.buildenv.2023.110772),” *Building and Environment*, vol. 244, Art. no. 110772, 2023.

<a name="ref-7"></a>[7]. Y. Chen, Q. Yang, Z. Chen, C. Yan, S. Zeng, and M. Dai, “[Physics-informed neural networks for building thermal modeling and demand response control](https://doi.org/10.1016/j.buildenv.2023.110149),” *Building and Environment*, vol. 234, Art. no. 110149, 2023. [GitHub (code)](https://github.com/Bob05757/PINNs-for-building-thermal-modeling-and-Demand-Response)

<a name="ref-8"></a>[8]. X. Yu, Z. Ren, P. Liu, L. Imsland, and L. Georges, “[Comparison of time-invariant and adaptive linear grey-box models for model predictive control of residential buildings](https://doi.org/10.1016/j.buildenv.2024.111391),” *Building and Environment*, vol. 254, Art. no. 111391, 2024.

<a name="ref-9"></a>[9]. X. Wang, Y. Ye, W. Deng, Y. Wu, Z. Zhang, T. Wu, and Y. Ma, “[An adaptive grey-box model for nearly zero energy building operations in challenging climate](https://doi.org/10.1016/j.energy.2026.141151),” *Energy*, vol. 355, Art. no. 141151, 2026.

<a name="ref-10"></a>[10]. F. Qi, W. Wu, N. Yoon, W. Zhang, M. Li, C. Wang, and H. Wang, “[Enhancing EnergyPlus simulation of internal mass for dynamic thermal energy storage](https://doi.org/10.1016/j.energy.2026.141885),” *Energy*, vol. 361, Art. no. 141885, 2026.

<a name="ref-11"></a>[11]. Z. Guo, Y. Li, J. Ping, J. Zhu, Z. Yan, and M.-Y. Chow, “[A self-adaptive modeling and control framework for HVAC systems considering user stochasticity](https://doi.org/10.1016/j.apenergy.2026.127512),” *Applied Energy*, vol. 409, Art. no. 127512, 2026.

<a name="ref-12"></a>[12]. M. E. Bagle, I. Sartori, and F. Goia, “[Adaptive system identification to support model-based controls in buildings](https://doi.org/10.1016/j.apenergy.2026.127756),” *Applied Energy*, vol. 414, Art. no. 127756, 2026.

<a name="ref-13"></a>[13]. C. Meister, S. Schneeberger, A. Jokiel, and P. Schuetz, “[Bottom-up heat pump flexibility estimation for Swiss buildings considering monitored building data](https://doi.org/10.1016/j.apenergy.2026.127856),” *Applied Energy*, vol. 414, Art. no. 127856, 2026.

<a name="ref-14"></a>[14]. Y. Jin, Z. Jiang, X. Wang, and B. Dong, “[Empowering phase change material thermodynamics via physics-consistent neural network-enabled advanced building control](https://doi.org/10.1016/j.apenergy.2025.127143),” *Applied Energy*, vol. 404, Art. no. 127143, 2026.

<a name="ref-15"></a>[15]. R.-D. López-Carreño, M. Macarulla, S. Gassó-Domingo, B. Tejedor, and F. Pardo-Bosch, “[A grey-box temperature model for digital twins of building-integrated rooftop greenhouses](https://doi.org/10.1016/j.buildenv.2025.114036),” *Building and Environment*, vol. 289, Art. no. 114036, 2026.

<a name="ref-16"></a>[16]. H. Zhang, Y. Wang, H. Zhao, W. Yao, W. Gao, G. Yang, L. Sun, and Z. Jiang, “[A spatiotemporal indoor thermal and visual quality prediction framework based on a structured multi-branch CNN–LSTM network](https://doi.org/10.1016/j.buildenv.2026.114378),” *Building and Environment*, vol. 294, Art. no. 114378, 2026.

<a name="ref-17"></a>[17]. X. Yang, S. Yoon, S.-J. Yoo, Y. Arima, Y. Choi, and A. Ozaki, “[High-fidelity spatiotemporal prediction of thermal environments in hybrid HVAC-conditioned open-plan offices using a coupled BES–CFD framework](https://doi.org/10.1016/j.buildenv.2026.115138),” *Building and Environment*, vol. 304, Art. no. 115138, 2026.

<a name="ref-18"></a>[18]. Y. Miao, C. Huang, J. Zhu, T. Yang, Z. Zou, and F. Wang, “[Prediction of thermal environment and stratified air-conditioning load in existing large spaces based on unsteady-state Block-Gebhart model](https://doi.org/10.1016/j.buildenv.2026.114267),” *Building and Environment*, vol. 291, Art. no. 114267, 2026.

<a name="ref-19"></a>[19]. M. Li, W. Wu, A. Bakker, W. Zhang, D. Bishop, H. Wang, and B. Nastasi, “[Energy flexibility of nighttime cooling of internal thermal mass: Development of EnergyPlus Python Plugin](https://doi.org/10.1016/j.energy.2026.141263),” *Energy*, vol. 357, Art. no. 141263, 2026.

<a name="ref-20"></a>[20]. J. Pan, S. Wang, and H. Li, “[Grid-interactive characteristics of passive thermal storage in buildings and the key influential factors – An experimental and analytical assessment](https://doi.org/10.1016/j.energy.2026.140828),” *Energy*, vol. 351, Art. no. 140828, 2026.

<a name="ref-21"></a>[21]. D. Zhang, Y. Mei, X. Wang, Z. Wang, Y. Cheng, and C. Zhan, “[Heat loss identification method for heating building exterior walls based on BO-TCN-LSTM-SA](https://doi.org/10.1016/j.energy.2025.139759),” *Energy*, vol. 342, Art. no. 139759, 2026.

<a name="ref-22"></a>[22]. Y. Li, M. Lu, X. Gong, C. McLauchlan, and Z. Ma, “[Performance characterization and optimization of thermally activated building systems with hybrid geothermal-solar energy technologies in net/nearly zero energy buildings](https://doi.org/10.1016/j.energy.2026.140743),” *Energy*, vol. 350, Art. no. 140743, 2026.

<a name="ref-23"></a>[23]. S. Oh, J. Y. Park, Y.-S. Jeong, and Y.-K. Kim, “[Physics-aware deep reinforcement learning for radiant floor heating: A Sim-to-Real framework for proactive energy management](https://doi.org/10.1016/j.energy.2026.142465),” *Energy*, vol. 364, Art. no. 142465, 2026.

<a name="ref-24"></a>[24]. Y. Wang, J. Guo, Y. Jiang, and C. Sun, “[PINN with dynamic constraint optimization for complex air-based TABS thermal dynamics prediction](https://doi.org/10.1016/j.energy.2026.140989),” *Energy*, vol. 353, Art. no. 140989, 2026.

<a name="ref-25"></a>[25]. C. Sun, J. Peng, S. Cao, S. Yang, Y. Zhu, and H. Yan, “[Unlocking flexibility in urban heating facilities: Mitigating insufficient heat supply through building thermal inertia](https://doi.org/10.1016/j.energy.2026.141807),” *Energy*, vol. 360, Art. no. 141807, 2026.

<a name="ref-26"></a>[26]. Q. Zhu, Y. Yang, L. Yu, Q.-S. Jia, C. J. Spanos, and X. Guan, “[A Unified Virtual Battery Modeling Framework for Flexibility Characterization of Building HVAC Systems](https://doi.org/10.1109/tsg.2026.3704436),” *IEEE Transactions on Smart Grid*, vol. 17, no. 6, pp. 5448–5459, 2026.

<a name="ref-27"></a>[27]. B. Li, H. Tang, L. Zhu, B. Zhou, Q. Zhou, C. Zhang, J. Li, and Z. Shuai, “[Demand Response Potential Evaluation for Commercial HVAC Loads Considering Cooling Storage in Chilled Water Loops](https://doi.org/10.1109/tsg.2026.3676769),” *IEEE Transactions on Smart Grid*, vol. 17, no. 5, pp. 3941–3953, 2026.

<a name="ref-28"></a>[28]. X. Cui, L. Chen, Y. Wang, and B. Xu, “[Online Scheduling of Thermostatically Controlled Loads: A Stepwise Reformulation Approach](https://doi.org/10.1109/tsg.2026.3731515),” *IEEE Transactions on Smart Grid*, early access, 2026. [GitHub (code)](https://github.com/hkuedl/Online-Multi-zone-TCL-Scheduling)

<a name="ref-29"></a>[29]. X. Liu, Q. Chen, P. S. Nielsen, and R. Liu, “[Physics-Informed Online Optimization for Building Energy Management: Exploiting Thermal Dynamics as Constraint Structure](https://doi.org/10.1109/tsg.2026.3741935),” *IEEE Transactions on Smart Grid*, early access, 2026.

<a name="ref-30"></a>[30]. J. Rousseau, H. Cai, P. Heer, K. Orehounig, and G. Hug, “[Uncertainty-Aware Flexibility of HVAC Systems in Buildings: From Quantification to Provision](https://doi.org/10.1109/tsg.2025.3611455),” *IEEE Transactions on Smart Grid*, vol. 17, no. 1, pp. 269–282, 2026. [GitHub (building emulator)](https://github.com/uesl-empa/nestli)

<a name="ref-31"></a>[31]. D. Chen, C.-K. Chui, and P. S. Lee, “[Adaptive physically consistent neural networks for data center thermal dynamics modeling](https://doi.org/10.1016/j.apenergy.2024.124637),” *Applied Energy*, vol. 377, Art. no. 124637, 2025. [GitHub (code)](https://github.com/chendong-energy/Adaptive-PCNN)

<a name="ref-32"></a>[32]. L. Von Krannichfeldt, K. Orehounig, and O. Fink, “[Combining physics-based and data-driven modeling for building energy systems](https://doi.org/10.1016/j.apenergy.2025.125853),” *Applied Energy*, vol. 391, Art. no. 125853, 2025. [GitHub (code and data)](https://github.com/Leo-VK/hybrid_bem)

<a name="ref-33"></a>[33]. Y. Lu, W. Wang, C. Wang, Z. Li, Y. Zhou, X. Chen, T. C. Ho, and C. Y. Tso, “[Deep reinforcement learning for HVAC control with nonlinear parametric thermal network modeling for passive building envelopes](https://doi.org/10.1016/j.apenergy.2025.126863),” *Applied Energy*, vol. 402, Art. no. 126863, 2025.

<a name="ref-34"></a>[34]. L. Tang, H. Xie, Y. Wang, and Z. Xu, “[Deeply flexible commercial building HVAC system control: A physics-aware deep learning-embedded MPC approach](https://doi.org/10.1016/j.apenergy.2025.125631),” *Applied Energy*, vol. 388, Art. no. 125631, 2025.

<a name="ref-35"></a>[35]. M. Montazeri, C. Remlinger, B. Bejar Haro, and P. Heer, “[Fully data-driven and modular building thermal control with physically consistent modeling](https://doi.org/10.1016/j.apenergy.2025.125770),” *Applied Energy*, vol. 390, Art. no. 125770, 2025.

<a name="ref-36"></a>[36]. J. Bjørnskov, A. Thomsen, and M. Jradi, “[Large-scale field demonstration of an interoperable and ontology-based energy modeling framework for building digital twins](https://doi.org/10.1016/j.apenergy.2025.125597),” *Applied Energy*, vol. 387, Art. no. 125597, 2025. [GitHub (digital twin framework)](https://github.com/JBjoernskov/Twin4Build)

<a name="ref-37"></a>[37]. F. Jiang and H. Kazmi, “[What-if: A causal machine learning approach to control-oriented modelling for building thermal dynamics](https://doi.org/10.1016/j.apenergy.2024.124550),” *Applied Energy*, vol. 377, Art. no. 124550, 2025.

<a name="ref-38"></a>[38]. P. M. Khatavkar, P. Rockett, Y. Kaszubowski Lopes, and E. A. Hathway, “[A bootstrapped automated pipeline for developing model predictive controllers for non-domestic buildings](https://doi.org/10.1016/j.buildenv.2025.112947),” *Building and Environment*, vol. 278, Art. no. 112947, 2025.

<a name="ref-39"></a>[39]. S. Wen, W. Zhang, N. Zhou, and L. Yuan, “[Adaptive spatio-temporal graph convolutional network for rapid indoor temperature field prediction with limited sensors](https://doi.org/10.1016/j.buildenv.2025.113346),” *Building and Environment*, vol. 283, Art. no. 113346, 2025.

<a name="ref-40"></a>[40]. W. Jiang, P. Wang, X. Ma, and Y. Liu, “[Development of a grey-box heat load prediction model by subspace identification method for heating building](https://doi.org/10.1016/j.buildenv.2025.113119),” *Building and Environment*, vol. 280, Art. no. 113119, 2025.

<a name="ref-41"></a>[41]. W. Qian, C. Li, H. Gao, L. Zhuang, Y. Lu, S. Hu, and J. Liu, “[Estimating indoor air temperature and humidity distributions by data assimilation with finite observations: Validation using an actual residential room](https://doi.org/10.1016/j.buildenv.2024.112495),” *Building and Environment*, vol. 269, Art. no. 112495, 2025.

<a name="ref-42"></a>[42]. Y. Yuan, J. Gao, M. Li, G. Liu, Y. Yu, Z. Yu, and H. Zhang, “[Fast prediction of indoor temperature distribution under spatiotemporal variation of solar radiation using equivalent surface heat sources and multimodal CNN](https://doi.org/10.1016/j.buildenv.2025.113641),” *Building and Environment*, vol. 285, Art. no. 113641, 2025.

<a name="ref-43"></a>[43]. G. Liu, J. Gao, Z. Han, and Y. Yuan, “[Hybrid model-based predictive HVAC control through fast prediction of transient indoor temperature fields](https://doi.org/10.1016/j.buildenv.2024.112253),” *Building and Environment*, vol. 267, Art. no. 112253, 2025.

<a name="ref-44"></a>[44]. T. Zhao, B. Jiang, Y. Li, Y. Rezgui, C. Zhang, and P. Wang, “[Multi-point temperature or humidity prediction for office building indoor environment based on CGC-BiLSTM deep neural network](https://doi.org/10.1016/j.buildenv.2024.112259),” *Building and Environment*, vol. 267, Art. no. 112259, 2025.

<a name="ref-45"></a>[45]. Y. Chen, H. Wang, and Z. Chen, “[Sensitivity analysis of physical regularization in physics-informed neural networks (PINNs) of building thermal modeling](https://doi.org/10.1016/j.buildenv.2025.112693),” *Building and Environment*, vol. 273, Art. no. 112693, 2025.

<a name="ref-46"></a>[46]. N. He, J. Guo, Y. Li, Y. Quan, R. Li, and L. Yang, “[Stochastic model predictive control for the optimal operation of office buildings](https://doi.org/10.1016/j.buildenv.2024.112248),” *Building and Environment*, vol. 267, Art. no. 112248, 2025.

<a name="ref-47"></a>[47]. H. Wang, Z. Tan, J. Mo, M. Hu, Y. Ji, and C. Fan, “[An innovative humidity Enhancement-RC-mapping model with tailored identification framework for building HVAC demand response applications](https://doi.org/10.1016/j.energy.2025.138772),” *Energy*, vol. 338, Art. no. 138772, 2025.

<a name="ref-48"></a>[48]. Y. Yao, C. Ye, Y. Zhao, and Y. Ding, “[Customized grey-box model for demand response probabilistic potential assessment of urban public buildings](https://doi.org/10.1016/j.energy.2025.139400),” *Energy*, vol. 341, Art. no. 139400, 2025.

<a name="ref-49"></a>[49]. S. Guo, Z. Wei, H. Wu, H. Fang, and X. Zhai, “[Real-time prediction of thermal load and indoor temperature for buildings with a recursive identification method in noise conditions](https://doi.org/10.1016/j.energy.2025.138022),” *Energy*, vol. 335, Art. no. 138022, 2025.

<a name="ref-50"></a>[50]. B. Han, H. Li, and S. Wang, “[Analytical Solutions of Air-Conditioning Load Flexibility](https://doi.org/10.1109/tsg.2024.3474421),” *IEEE Transactions on Smart Grid*, vol. 16, no. 1, pp. 441–444, 2025.

<a name="ref-51"></a>[51]. X. Cui, J.-F. Toubeau, F. Vallée, and Y. Wang, “[Decision-Oriented Modeling of Thermal Dynamics Within Buildings](https://doi.org/10.1109/tsg.2024.3445574),” *IEEE Transactions on Smart Grid*, vol. 16, no. 1, pp. 369–382, 2025. [GitHub (code)](https://github.com/hkuedl/Decision-Oriented-Thermal-Dynamics-Modeling)

<a name="ref-52"></a>[52]. X. Cui, Y. Wang, and B. Xu, “[Dimension-Reduced Optimization of Multi-Zone Thermostatically Controlled Loads](https://doi.org/10.1109/tsg.2025.3579778),” *IEEE Transactions on Smart Grid*, vol. 16, no. 6, pp. 4685–4697, 2025. [GitHub (code and data)](https://github.com/hkuedl/Latent-Variable-based-Optimization)

<a name="ref-53"></a>[53]. T. Qi, H. Hui, and Y. Song, “[Exploring the Feasible Regulation Region of Building HVAC Systems Within Hygro-Thermal Comfort](https://doi.org/10.1109/tsg.2025.3569074),” *IEEE Transactions on Smart Grid*, vol. 16, no. 4, pp. 2926–2939, 2025.

<a name="ref-54"></a>[54]. Z. Zhang, H. Hui, and Y. Song, “[Response Capacity Allocation of Air Conditioners for Peak-Valley Regulation Considering Interaction With Surrounding Microclimate](https://doi.org/10.1109/tsg.2024.3482361),” *IEEE Transactions on Smart Grid*, vol. 16, no. 2, pp. 1155–1167, 2025.

<a name="ref-55"></a>[55]. X. Wang, S. Tian, J. Ren, X. Jin, X. Zhou, and X. Shi, “[A novel resistance-capacitance model for evaluating urban building energy loads considering construction boundary heterogeneity](https://doi.org/10.1016/j.apenergy.2024.122896),” *Applied Energy*, vol. 361, Art. no. 122896, 2024.

<a name="ref-56"></a>[56]. X. Cui, S. Liu, G. Ruan, and Y. Wang, “[Data-driven aggregation of thermal dynamics within building virtual power plants](https://doi.org/10.1016/j.apenergy.2023.122126),” *Applied Energy*, vol. 353, Art. no. 122126, 2024.

<a name="ref-57"></a>[57]. W. Zheng, D. Wang, and Z. Wang, “[Economic model predictive control for building HVAC system: A comparative analysis of model-based and data-driven approaches using the BOPTEST Framework](https://doi.org/10.1016/j.apenergy.2024.123969),” *Applied Energy*, vol. 374, Art. no. 123969, 2024. [GitHub (code)](https://github.com/wfzheng/EMPC_Comparision)

<a name="ref-58"></a>[58]. H. Wang, X. Chen, N. Vital, E. Duffy, and A. Razi, “[Energy optimization for HVAC systems in multi-VAV open offices: A deep reinforcement learning approach](https://doi.org/10.1016/j.apenergy.2023.122354),” *Applied Energy*, vol. 356, Art. no. 122354, 2024. [GitHub (code)](https://github.com/AIS-Clemson/DRL-BEMS)

<a name="ref-59"></a>[59]. V. Taboga, C. Gehring, M. L. Cam, H. Dagdougui, and P.-L. Bacon, “[Neural differential equations for temperature control in buildings under demand response programs](https://doi.org/10.1016/j.apenergy.2024.123433),” *Applied Energy*, vol. 368, Art. no. 123433, 2024.

<a name="ref-60"></a>[60]. Y. Bian, X. Fu, R. K. Gupta, and Y. Shi, “[Ventilation and temperature control for energy-efficient and healthy buildings: A differentiable PDE approach](https://doi.org/10.1016/j.apenergy.2024.123477),” *Applied Energy*, vol. 372, Art. no. 123477, 2024. [GitHub (code and data)](https://github.com/alwaysbyx/PDE-HVAC-control)

<a name="ref-61"></a>[61]. M. Hostein, M. Musy, B. Moujalled, and M. El Mankibi, “[Generating meteorological files of future climates with heatwaves in urban context to evaluate building overheating: An energy-efficient dwelling case study](https://doi.org/10.1016/j.buildenv.2024.111874),” *Building and Environment*, vol. 263, Art. no. 111874, 2024.

<a name="ref-62"></a>[62]. J. Wang, F. Kong, B. Pan, J. Zheng, P. Xue, C. Sun, and C. Qi, “[Low-order gray-box modeling of heating buildings and the progressive dimension reduction identification of uncertain model parameters](https://doi.org/10.1016/j.energy.2024.130812),” *Energy*, vol. 294, Art. no. 130812, 2024.

<a name="ref-63"></a>[63]. P. Hua, H. Wang, Z. Xie, and R. Lahdelma, “[Multi-criteria evaluation of novel multi-objective model predictive control method for indoor thermal comfort](https://doi.org/10.1016/j.energy.2023.129883),” *Energy*, vol. 289, Art. no. 129883, 2024.

<a name="ref-64"></a>[64]. Z. Zheng, R. Tang, X. Luo, H. Li, and S. Wang, “[A Distributed Coordination Strategy for Heterogeneous Building Flexible Thermal Loads in Responding to Smart Grids](https://doi.org/10.1109/tsg.2023.3306044),” *IEEE Transactions on Smart Grid*, vol. 15, no. 2, pp. 1620–1633, 2024.

<a name="ref-65"></a>[65]. B. He, N. Zhang, C. Fang, Y. Su, and Y. Wang, “[Flexible Building Energy Management With Neural ODEs-Based Model Predictive Control](https://doi.org/10.1109/tsg.2024.3401227),” *IEEE Transactions on Smart Grid*, vol. 15, no. 5, pp. 4690–4704, 2024.

<a name="ref-66"></a>[66]. Z. Hou, S. Lu, Y. Xu, H. Qiu, W. Gu, Z. Y. Dong, and S. Ding, “[Privacy-Preserved Aggregate Thermal Dynamic Model of Buildings](https://doi.org/10.1109/tsg.2024.3420743),” *IEEE Transactions on Smart Grid*, vol. 15, no. 6, pp. 5653–5664, 2024.

<a name="ref-67"></a>[67]. W. Aslam, P. Andrianesis, and M. Caramanis, “[Optimal HVAC Energy and Regulation Reserve Scheduling in Power Markets](https://doi.org/10.1109/tste.2023.3279060),” *IEEE Transactions on Sustainable Energy*, vol. 15, no. 1, pp. 201–214, 2024.

<a name="ref-68"></a>[68]. Y. Song, M. Xia, Q. Chen, and F. Chen, “[A data-model fusion dispatch strategy for the building energy flexibility based on the digital twin](https://doi.org/10.1016/j.apenergy.2022.120496),” *Applied Energy*, vol. 332, Art. no. 120496, 2023.

<a name="ref-69"></a>[69]. Y. Zhang, W. Jiang, J. Song, L. Xu, S. Li, and L. Hu, “[A parametric model on thermal evaluation of building envelopes containing phase change material](https://doi.org/10.1016/j.apenergy.2022.120471),” *Applied Energy*, vol. 331, Art. no. 120471, 2023.

<a name="ref-70"></a>[70]. T. Xiao and F. You, “[Building thermal modeling and model predictive control with physically consistent deep learning for decarbonization and energy optimization](https://doi.org/10.1016/j.apenergy.2023.121165),” *Applied Energy*, vol. 342, Art. no. 121165, 2023.

<a name="ref-71"></a>[71]. Y. Jiang, S. Zhu, Q. Xu, B. Yang, and X. Guan, “[Hybrid modeling-based temperature and humidity adaptive control for a multi-zone HVAC system](https://doi.org/10.1016/j.apenergy.2022.120622),” *Applied Energy*, vol. 334, Art. no. 120622, 2023.

<a name="ref-72"></a>[72]. M. Frahm, T. Dengiz, P. Zwickel, H. Maaß, J. Matthes, and V. Hagenmeyer, “[Occupant-oriented demand response with multi-zone thermal building control](https://doi.org/10.1016/j.apenergy.2023.121454),” *Applied Energy*, vol. 347, Art. no. 121454, 2023. [GitHub (code and control results)](https://github.com/Occupant-Oriented-Demand-Response/Conrol-Results)

<a name="ref-73"></a>[73]. A. Canet and M. Qadrdan, “[Quantification of flexibility from the thermal mass of residential buildings in England and Wales](https://doi.org/10.1016/j.apenergy.2023.121616),” *Applied Energy*, vol. 349, Art. no. 121616, 2023. [GitHub (code)](https://github.com/AlexandreLab/flexibilitydwellings)

<a name="ref-74"></a>[74]. J. Zhang, F. Xiao, A. Li, T. Ma, K. Xu, H. Zhang, R. Yan, X. Fang, Y. Li, and D. Wang, “[Graph neural network-based spatio-temporal indoor environment prediction and optimal control for central air-conditioning systems](https://doi.org/10.1016/j.buildenv.2023.110600),” *Building and Environment*, vol. 242, Art. no. 110600, 2023.

<a name="ref-75"></a>[75]. T. Xing, K. Sun, and Q. Zhao, “[MITP-Net: A deep-learning framework for short-term indoor temperature predictions in multi-zone buildings](https://doi.org/10.1016/j.buildenv.2023.110388),” *Building and Environment*, vol. 239, Art. no. 110388, 2023. [GitHub (code and data)](https://github.com/XingTian1994/MITP-Net)

<a name="ref-76"></a>[76]. M. Sulzer, A. Christen, and A. Matzarakis, “[Predicting indoor air temperature and thermal comfort in occupational settings using weather forecasts, indoor sensors, and artificial neural networks](https://doi.org/10.1016/j.buildenv.2023.110077),” *Building and Environment*, vol. 234, Art. no. 110077, 2023.

<a name="ref-77"></a>[77]. L. Sha, Z. Jiang, and H. Sun, “[A control strategy of heating system based on adaptive model predictive control](https://doi.org/10.1016/j.energy.2023.127192),” *Energy*, vol. 273, Art. no. 127192, 2023.

<a name="ref-78"></a>[78]. M. Li, W. Gong, and S. Liu, “[Analysis of temperature regulation and heat storage effect of the combined phase change envelope in hot summer and cold winter zone](https://doi.org/10.1016/j.energy.2022.126518),” *Energy*, vol. 266, Art. no. 126518, 2023.

<a name="ref-79"></a>[79]. Z. Liu, H. Zhang, Y. Wang, X. Fan, S. You, and A. Li, “[Data-driven predictive model for feedback control of supply temperature in buildings with radiator heating system](https://doi.org/10.1016/j.energy.2023.128248),” *Energy*, vol. 280, Art. no. 128248, 2023.

<a name="ref-80"></a>[80]. Z. Wei and J. Calautit, “[Predictive control of low-temperature heating system with passive thermal mass energy storage and photovoltaic system: Impact of occupancy patterns and climate change](https://doi.org/10.1016/j.energy.2023.126791),” *Energy*, vol. 269, Art. no. 126791, 2023.

<a name="ref-81"></a>[81]. W. Wang, G. Tian, Q. Z. Sun, and H. Liu, “[A Control Framework to Enable a Commercial Building HVAC System for Energy and Regulation Market Signal Tracking](https://doi.org/10.1109/tpwrs.2022.3156867),” *IEEE Transactions on Power Systems*, vol. 38, no. 1, pp. 290–301, 2023.

<a name="ref-82"></a>[82]. Z. Wei, F. Ren, Y. Zhu, B. Yue, Y. Ding, C. Zheng, B. Li, and X. Zhai, “[Data-driven two-step identification of building thermal characteristics: A case study of office building](https://doi.org/10.1016/j.apenergy.2022.119949),” *Applied Energy*, vol. 326, Art. no. 119949, 2022.

<a name="ref-83"></a>[83]. J. Wang, Y. Jiang, C. Y. Tang, and L. Song, “[Development and validation of a second-order thermal network model for residential buildings](https://doi.org/10.1016/j.apenergy.2021.118124),” *Applied Energy*, vol. 306, Art. no. 118124, 2022.

<a name="ref-84"></a>[84]. S. Zhan, Y. Lei, Y. Jin, D. Yan, and A. Chong, “[Impact of occupant related data on identification and model predictive control for buildings](https://doi.org/10.1016/j.apenergy.2022.119580),” *Applied Energy*, vol. 323, Art. no. 119580, 2022.

<a name="ref-85"></a>[85]. C. A. Thilker, J. B. Jørgensen, and H. Madsen, “[Linear quadratic Gaussian control with advanced continuous-time disturbance models for building thermal regulation](https://doi.org/10.1016/j.apenergy.2022.120086),” *Applied Energy*, vol. 327, Art. no. 120086, 2022.

<a name="ref-86"></a>[86]. S. Yang, H. O. Gao, and F. You, “[Model predictive control in phase-change-material-wallboard-enhanced building energy management considering electricity price dynamics](https://doi.org/10.1016/j.apenergy.2022.120023),” *Applied Energy*, vol. 326, Art. no. 120023, 2022.

<a name="ref-87"></a>[87]. G. Gokhale, B. Claessens, and C. Develder, “[Physics informed neural networks for control oriented thermal modeling of buildings](https://doi.org/10.1016/j.apenergy.2022.118852),” *Applied Energy*, vol. 314, Art. no. 118852, 2022. [GitHub (code and simulation data)](https://github.com/GargyaGokhale/PhysNet_Thermal_Models)

<a name="ref-88"></a>[88]. B. Jiang, H. Gong, H. Qin, and M. Zhu, “[Attention-LSTM architecture combined with Bayesian hyperparameter optimization for indoor temperature prediction](https://doi.org/10.1016/j.buildenv.2022.109536),” *Building and Environment*, vol. 224, Art. no. 109536, 2022.

<a name="ref-89"></a>[89]. F. M. Baba, H. Ge, R. Zmeureanu, and L. Wang, “[Calibration of building model based on indoor temperature for overheating assessment using genetic algorithm: Methodology, evaluation criteria, and case study](https://doi.org/10.1016/j.buildenv.2021.108518),” *Building and Environment*, vol. 207, Art. no. 108518, 2022.

<a name="ref-90"></a>[90]. W. Qian, M. Tang, H. Gao, J. Dong, J. Liang, and J. Liu, “[Improving indoor air flow and temperature prediction with local measurements based on CFD-EnKF data assimilation](https://doi.org/10.1016/j.buildenv.2022.109511),” *Building and Environment*, vol. 223, Art. no. 109511, 2022.

<a name="ref-91"></a>[91]. N. Salman, A. Khan, A. H. Kemp, and C. J. Noakes, “[Indoor Temperature Forecast based on the Lattice Boltzmann method and Data Assimilation](https://doi.org/10.1016/j.buildenv.2021.108654),” *Building and Environment*, vol. 210, Art. no. 108654, 2022. [GitHub (MATLAB code)](https://github.com/Nav-101/LBM-DA-matlabcode)

<a name="ref-92"></a>[92]. X. Yu, K. S. Skeie, M. D. Knudsen, Z. Ren, L. Imsland, and L. Georges, “[Influence of data pre-processing and sensor dynamics on grey-box models for space-heating: Analysis using field measurements](https://doi.org/10.1016/j.buildenv.2022.108832),” *Building and Environment*, vol. 212, Art. no. 108832, 2022.

<a name="ref-93"></a>[93]. Z. Liu, H. Zhang, Y. Wang, Z. Song, S. You, Y. Jiang, and Z. Wu, “[A thermal-hydraulic coupled simulation approach for the temperature and flow rate control strategy evaluation of the multi-room radiator heating system](https://doi.org/10.1016/j.energy.2022.123347),” *Energy*, vol. 246, Art. no. 123347, 2022.

<a name="ref-94"></a>[94]. B. Dai, Y. Tong, Q. Hu, and Z. Chen, “[Characteristics of thermal stratification and its effects on HVAC energy consumption for an atrium building in south China](https://doi.org/10.1016/j.energy.2022.123425),” *Energy*, vol. 249, Art. no. 123425, 2022.

<a name="ref-95"></a>[95]. Y. Ding, Y. Lyu, S. Lu, and R. Wang, “[Load shifting potential assessment of building thermal storage performance for building design](https://doi.org/10.1016/j.energy.2021.123036),” *Energy*, vol. 243, Art. no. 123036, 2022.

<a name="ref-96"></a>[96]. J. Hou, H. Li, and N. Nord, “[Nonlinear model predictive control for the space heating system of a university building in Norway](https://doi.org/10.1016/j.energy.2022.124157),” *Energy*, vol. 253, Art. no. 124157, 2022. [GitHub (models and data)](https://github.com/haoranli1988/Modelica-district-heating-optimization-MPC)

<a name="ref-97"></a>[97]. X. Fan and X. Li, “[Performance comparison analysis for different single-zone natural ventilation building indoor temperature prediction method combined thermal mass](https://doi.org/10.1016/j.energy.2022.124518),” *Energy*, vol. 255, Art. no. 124518, 2022.

<a name="ref-98"></a>[98]. J. Guo, J. Dong, H. Wang, Y. Wang, B. Zou, and Y. Jiang, “[Study on the demand response potential of an actively ventilated building: Parametric and scenario analysis](https://doi.org/10.1016/j.energy.2021.122043),” *Energy*, vol. 238, Art. no. 122043, 2022.

<a name="ref-99"></a>[99]. G. Tian, Q. Z. Sun, and W. Wang, “[Real-Time Flexibility Quantification of a Building HVAC System for Peak Demand Reduction](https://doi.org/10.1109/tpwrs.2021.3136464),” *IEEE Transactions on Power Systems*, vol. 37, no. 5, pp. 3862–3874, 2022.

<a name="ref-100"></a>[100]. S. Lu, W. Gu, S. Ding, S. Yao, H. Lu, and X. Yuan, “[Data-Driven Aggregate Thermal Dynamic Model for Buildings: A Regression Approach](https://doi.org/10.1109/tsg.2021.3101357),” *IEEE Transactions on Smart Grid*, vol. 13, no. 1, pp. 227–242, 2022.
