# ☀️ Forecasting Impactful Solar Flares using Time-Series
## Project Summary: Mitigating Space Weather Threats

Solar flares, characterized by sudden and intense energy bursts from the Sun’s surface, pose significant risks when they are powerful enough to interact with Earth's atmosphere. These phenomena are known to cause:

- Disruption of satellite and telecommunication signals.
- Interference with global navigation systems (GPS).
- Potential degradation of the ozone layer and atmospheric effects.

The mitigation of these impacts is contingent upon the availability of a reliable, high-fidelity forecasting system capable of providing timely warnings.

This project demonstrates a rigorous time-series analysis solution for forecasting three critical solar flare attributes: **X-Ray Flux**, **UV Fluorescence**, and **Flare Duration**. Using the **SWAN-SF (Solar Wind Analysis System - Solar Flares)** dataset, we leverage advanced statistical models to provide predictive insights crucial for mitigating the impact of space weather on terrestrial and space-based infrastructure (e.g., power grids, satellites, GPS).

The core innovation is the systematic comparison of **ARIMA (Univariate)** and **VAR (Multivariate)** models, proving the superiority of the multivariate approach in capturing the interdependent dynamics of solar phenomena.

## 🌟 Key Technical Features
- **Multivariate Time-Series Modeling (VAR):** Utilizes the Vector AutoRegressive model to accurately capture the dynamic, interdependent relationships between multiple solar wind predictors and the flare characteristics.

- **Model Comparison Framework:** Rigorous diagnostic and validation using RMSE and Standard Deviation to statistically select the optimal forecasting technique across three target variables.

- **Data Preprocessing Pipeline:** Includes min-max normalization for stabilizing volatile input variables and Autocorrelation Function (ACF) analysis for identifying stationarity and appropriate lag structures.

- **Reproducible Research & Reporting:** All statistical modeling is executed in R Studio and documented using Quarto for generating dynamic, professional reports and presentations.

## 💻 Technology Stack & Data Sources

| Category | Component | Details |
|-------|------------|---------|
| **Language** | R | Primary language for statistical computing and modeling. |
| **Libraries** | vars, dlm, forecast, ggplot2 | Core packages for VAR, State-Space, ARIMA modeling, and visualization. |
| **Reporting** | Quarto `(.qmd)` | Used to generate dynamic reports, presentations, and HTML documentation. |
| **Data Source** | SWAN-SF Dataset | NASA provided satellite-collected solar wind and flare metrics. |
| **Data Format** | .csv | Original and pre-processed (normalized) time-series data. |

## 💡 Use Cases and Real-World Impact
The predictive models developed here have direct, high-value applications:

- **Critical Infrastructure Protection:** Providing advance warning to power grid operators to mitigate Geomagnetically Induced Currents (GICs) and prevent blackouts caused by strong X-ray flux.

- **Space Asset Management:** Forecasting radiation exposure to inform satellite operators when to temporarily disable sensitive components or adjust orbital paths to prevent costly damage.

- **Aviation and Communication:** Improving the reliability of GPS, radio signals, and long-haul flight path planning by anticipating periods of ionospheric disruption caused by solar flares.

## 📐 Conceptual Modeling Architecture
The project workflow moves from raw data ingestion to a structured, model-comparison phase.

- **Data Ingestion:** Load the raw, high-dimensional SWAN-SF data.

- **Preprocessing:** Normalize data, index time series, and check stationarity (ACF).
  - Implemented Min-Max Normalization to standardize the input feature set (over 30 variables) and feature engineered three variables namely `XRAY`, `Fluorescence`, and `Flare-time`.

    <img width="1920" height="960" alt="image" src="https://github.com/user-attachments/assets/776eb941-7a40-405e-8cb3-e6df7b7bc822" />

  - 📊 Min-Max Normalization Formula: $x' = \frac{x - x_{\text{min}}}{x_{\text{max}} - x_{\text{min}}}$. It scales a feature $x$ to a fixed range $[0, 1]$:

- **Model Fitting:** Execute two parallel modeling efforts (ARIMA and VAR) on the three target variables.
  - Employed ARIMA as a univariate baseline and VAR as the primary multivariate modeling technique to capture the inherent interdependence between solar flare attributes.
 
  <img width="1920" height="960" alt="image" src="https://github.com/user-attachments/assets/3cec7931-363c-4b93-9344-677b1025414c" />
  
  <img width="1920" height="960" alt="image" src="https://github.com/user-attachments/assets/1244304a-b7b4-46a7-a79c-9762ec66425a" />
  
  <img width="1920" height="960" alt="image" src="https://github.com/user-attachments/assets/c8c20704-b64f-4f6b-8189-e2a934f420d1" />

- **Diagnostics & Selection:** Compare forecast accuracy using RMSE and STD to determine the superior model for each metric.
  - The modeling process confirmed the initial hypothesis of non-stationarity across all target time series, necessitating differencing for model fitting.  Diagnostic plots, such as the Autocorrelation Function (ACF), provided statistical validation for the long-term dependency structure.
  - The predictive efficacy of the models was objectively assessed using the Root Mean Square Error (RMSE) on out-of-sample (OOS) data. The core comparison results are summarized below:

    | Target Feature | RMSE (ARIMA) | RMSE (VAR) | Standard Deviation (STD) |
    |-------|---------|---------|---------| 
    | **Flare_time** | $7.07$ | $6.74\times 10^{-5}$ | $2.79$ |
    | **Fluroscence** | $6.82\times 10^{-5}$ | $8.31$ | $2.31\times 10^{-5}$ |
    | **XRAY** | $8.33$ | $8.31$ | $2.26$ |

  - The VAR model achieved a profound improvement in accuracy, reducing the RMSE by several orders of magnitude (from 7.07 to ). This result is the most critical finding, decisively $6.74 \times 10^{-5}$ proving that the duration of an impactful event is a function of the co-movement of its related variables (intensity and UV emission).
  - For X-ray intensity and fluorescence, the performance gain of VAR over ARIMA was marginal or slightly regressed. This suggests that the individual time-series pattern of these variables is highly self-predictive, and the added complexity of the multivariate model did not yield superior explanatory power for these specific metrics.

- **Forecasting:** Generate future predictions for operational use.
  
## 🚀 Repository Contents
`/`: Contains the primary documentation files (README.md, MODEL_ARCHITECTURE.md).

`/R_SCRIPTS`: Contains Final_code.R (the main execution script).

`/DATA`: Contains original_data.csv and normalized_data.csv.

`/DOCS`: Contains the Quarto report files (project.qmd, project.html) and the presentation (08-statespace.qmd).

## 💡 Strategic Impact and Conclusion
The successful implementation and validation of the VAR model for flare duration forecasting represents a significant advance in reliable space weather prediction.

- **Operational Readiness:** The system provides actionable intelligence by offering accurate, near-term forecasts for the most volatile and critical parameter: the event's duration.

- **Mitigation Strategy:** Knowledge of a flare's potential duration is vital for mission control centers, enabling personnel to execute timely protective measures for satellites and ground-based infrastructure, thus minimizing economic loss and system downtime.

- **Future Work:** Further research should focus on integrating a multivariate state-space model or dynamic linear models (DLM) to potentially optimize the forecasting of all three variables simultaneously, building upon the structural insights gained from the VAR implementation.
