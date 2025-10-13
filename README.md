# ☀️ Forecasting Impactful Solar Flares using Time-Series
## Project Executive Summary: Mitigating Space Weather Threats
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

- **Model Fitting:** Execute two parallel modeling efforts (ARIMA and VAR) on the three target variables.

- **Diagnostics & Selection:** Compare forecast accuracy using RMSE and STD to determine the superior model for each metric.

- **Forecasting:** Generate future predictions for operational use.
  
## 🚀 Repository Contents
`/`: Contains the primary documentation files (README.md, MODEL_ARCHITECTURE.md).

`/R_SCRIPTS`: Contains Final_code.R (the main execution script).

`/DATA`: Contains original_data.csv and normalized_data.csv.

`/DOCS`: Contains the Quarto report files (project.qmd, project.html) and the presentation (08-statespace.qmd).
