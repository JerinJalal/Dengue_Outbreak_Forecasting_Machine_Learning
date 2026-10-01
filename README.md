<p align="center">
  <h1 align="center">Weekly Dengue Outbreak Forecasting in Bangladesh Using Classical Machine Learning on Climate and Case-History Features
</h1>
  <p align="center">
    <strong>Machine Learning-Based Weekly Dengue Outbreak Forecasting & Early Warning for Bangladesh</strong>
  </p>
  <p align="center">
    Climate-aware forecasting • Time-aware validation • Risk-level prediction
  </p>
</p>

---

##  Overview

**Dengue_Outbreak_Forecasting-BD** is a machine learning research project for forecasting weekly dengue cases and generating an early-warning risk signal for Bangladesh.

The project combines:

- Historical dengue surveillance data
- Weather and climate variables
- Lagged epidemiological features
- Machine learning regression models
- Time-aware model evaluation
- A risk-level classification layer

The goal is to investigate whether routinely available historical dengue and weather information can support **short-term weekly dengue outbreak forecasting** and provide an interpretable **Low / Medium / High risk signal**.

> **Project type:** Machine Learning / Public Health / Time-Series Forecasting  
> **Primary setting:** Bangladesh  
> **Forecasting unit:** Weekly  
> **Target:** Dengue cases / outbreak risk

---

## Objectives

The project focuses on four main objectives:

1. **Forecast weekly dengue cases** using historical surveillance and climate/weather information.
2. **Compare multiple machine learning approaches** under a time-aware evaluation framework.
3. **Identify important predictors** associated with dengue case variation.
4. **Convert model forecasts into an actionable risk signal** using Low, Medium, and High risk levels.

---

## Methodology

The general workflow is:

```text
                 ┌──────────────────────┐
                 │ Dengue Surveillance  │
                 │       Data           │
                 └──────────┬───────────┘
                            │
                            ▼
                 ┌──────────────────────┐
                 │ Weather / Climate    │
                 │       Data           │
                 └──────────┬───────────┘
                            │
                            ▼
                 ┌──────────────────────┐
                 │ Data Cleaning &      │
                 │ Temporal Alignment   │
                 └──────────┬───────────┘
                            │
                            ▼
                 ┌──────────────────────┐
                 │ Lagged & Derived     │
                 │ Feature Engineering  │
                 └──────────┬───────────┘
                            │
                            ▼
                 ┌──────────────────────┐
                 │ Time-Aware Train /   │
                 │ Validation / Test    │
                 └──────────┬───────────┘
                            │
                            ▼
              ┌─────────────┴─────────────┐
              │      ML Forecasting       │
              │                           │
              │  • Linear Regression      │
              │  • SVR                    │
              │  • Random Forest          │
              │  • XGBoost                │
              │  • Bayesian Classifier    │
              └─────────────┬─────────────┘
                            │
                            ▼
                 ┌──────────────────────┐
                 │ Weekly Case Forecast │
                 └──────────┬───────────┘
                            │
                            ▼
                 ┌──────────────────────┐
                 │ Risk-Level Mapping   │
                 │ Low / Medium / High  │
                 └──────────────────────┘
```

---

## Data Sources

The project is designed around dengue surveillance and environmental information.

### Dengue Data

Dengue case information is based on publicly available surveillance information, including data associated with the **Directorate General of Health Services (DGHS), Bangladesh**.

### Weather / Climate Data

Environmental predictors can include routinely available meteorological variables such as:

- Temperature
- Relative humidity
- Precipitation
- Other weather-derived variables used during feature engineering

Weather information is obtained from sources such as:

- **NASA POWER**
- **Open-Meteo**

> **Important:** External datasets are subject to their own terms, licenses, attribution requirements, and usage restrictions. The MIT license in this repository applies to the project's original code, not automatically to third-party datasets.

---

## Machine Learning Models

The core model set includes:

| Model | Task |
|---|---|
| Linear Regression | Weekly case forecasting |
| Support Vector Regression (SVR) | Weekly case forecasting |
| Random Forest | Non-linear forecasting |
| XGBoost | Gradient-boosted forecasting |
| Bayesian Classification | Risk-level classification |

The repository may also contain additional experimental models as the research implementation evolves.

---

## Time-Aware Evaluation

Because dengue forecasting is a temporal prediction problem, the project does **not** rely on ordinary random train/test splitting as the primary evaluation strategy.

The evaluation process respects chronological order:

```text
Past ───────────────────────────────────────────────► Future

[ TRAIN ] [ VALIDATION ] [ TEST ]
```

This helps simulate the real forecasting situation:

> Train using information that would have been available in the past → predict a future period.

The final evaluation should therefore reflect out-of-time forecasting performance rather than performance obtained from randomly shuffled observations.

---

## Risk-Level Early Warning

The forecasting output can be translated into a simple risk signal:

```text
             Predicted Dengue Activity
                       │
          ┌────────────┼────────────┐
          ▼            ▼            ▼
        LOW          MEDIUM        HIGH
       Risk           Risk          Risk
```

The purpose of this layer is to make model output easier to interpret for an early-warning use case.

Risk thresholds should be documented explicitly in the implementation and should be evaluated separately from the underlying continuous case forecast.

---

## Interpretability

The project also considers model interpretability so that predictions are not treated as unexplained outputs.

Potential analyses include:

- Feature importance
- Predictor contribution
- Weather-variable relationships
- Historical dengue lag effects
- Model-specific interpretation

These analyses are intended to help understand **which variables the models rely on**, not to establish causal relationships.

---

##  Project Structure

A recommended repository structure is:

```text
DengueForeSight-BD/
│
├── data/
│   ├── raw/
│   ├── processed/
│   └── README.md
│
├── notebooks/
│   ├── 01_data_exploration.ipynb
│   ├── 02_preprocessing.ipynb
│   ├── 03_feature_engineering.ipynb
│   ├── 04_model_training.ipynb
│   └── 05_evaluation.ipynb
│
├── src/
│   ├── data/
│   ├── features/
│   ├── models/
│   ├── evaluation/
│   └── visualization/
│
├── models/
│
├── figures/
│
├── results/
│
├── requirements.txt
├── README.md
└── LICENSE
```

The exact structure may change as the implementation develops.

---

## Installation

### 1. Clone the repository

```bash
git clone https://github.com/JerinJalal/Dengue_Outbreak_Forecasting_Machine_Learning.git
cd Weekly_Dengue_Outbreak_Forecasting_Machine_Learning
```


## Responsible Use

This project is intended for **research and educational purposes**.

Model predictions should not be treated as a substitute for:

- Official public-health surveillance
- Epidemiological investigation
- Medical diagnosis
- Government decision-making
- Professional public-health guidance

A machine learning forecast represents a model-based estimate and can be affected by data quality, reporting changes, distribution shifts, missing information, and model assumptions.

---


## 👤 Authors

| Member 1 | Member 2 | Member 3 | Member 4 |
|---|---|---|---|
| [Jerin Jalal](https://github.com/JerinJalal) | [Prionty Kundu Aurin](https://github.com/Source-Soul) | [Sadia Sultana](https://github.com/Steadfast404) | [Zarin Tasnim Ritu](https://github.com/ZarinRitu32) |

Bangladesh 🇧🇩


---

## Citation

If you use this repository in academic work, please cite the associated research work,

A BibTeX entry can be added here:

```bibtex
@misc{dengueforesightbd,
  title  = {Weekly Dengue Outbreak Forecasting in Bangladesh Using Classical Machine Learning on Climate and Case-History Features},
  author = {Jerin Jalal, Prionty Kundu Aurin, Sadia Sultana, Zarin Tasnim},
  year   = {2026},
  url    = {https://github.com/JerinJalal/Dengue_Outbreak_Forecasting_Machine_Learning.git}
}
```

---

