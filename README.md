# Predictive AI/ML for Offshore Asset Integrity
## Metocean Data Analysis, Extreme Value Analysis and Fatigue Assessment

### Project Overview

This project explores the application of Python-based data analytics, statistical modelling and machine learning techniques to metocean data for offshore asset integrity assessment.

Using one year of hourly Jubilee TRP3 metocean data (2025), the project investigates environmental conditions, extreme wave events and their relationship with offshore structural fatigue.

The work is organised into three case studies, progressing from exploratory data analysis and feature engineering to extreme value analysis and predictive fatigue modelling.

The overall objective is to develop practical data-driven workflows that support the understanding of offshore environmental loading and its potential implications for asset integrity management.

---

## Case Studies

### Case Study 1: Metocean Exploratory Data Analysis and Feature Engineering

**Objective:** Explore the metocean dataset, understand the distribution and behaviour of environmental variables, identify patterns and develop additional features for subsequent analysis and modelling.

**Key activities:**
- Data loading, inspection and cleaning.
- Handling missing values and checking data consistency.
- Exploratory analysis of significant wave height (Hs), peak wave period (Tp), mean wave direction (MWD), current speed (Uc), wind speed (U10), sea surface temperature (SST) and other available variables.
- Statistical summaries and distribution analysis.
- Time-series visualisation and seasonal pattern investigation.
- Feature engineering, including rolling statistics, lagged variables and other derived features.

**Key output:**
- Enriched metocean dataset containing the original variables and engineered features.

**Deliverable:**
- `Jubilee_TRP3_Metocean_Enriched.csv`

### Case Study 2: Extreme Value Analysis of Significant Wave Height

**Objective:** Apply statistical extreme value analysis techniques to significant wave height data to investigate extreme wave conditions and estimate potential return levels.

**Key activities:**

1. **Generalised Extreme Value (GEV) Analysis**
   - Annual and monthly block maxima extraction.
   - GEV distribution fitting.
   - Examination of block maxima behaviour.

2. **Peaks Over Threshold (POT) Analysis**
   - Mean residual life analysis for threshold selection.
   - Selection of a significant wave height threshold.
   - Event declustering to reduce dependence between exceedances.
   - Generalised Pareto Distribution (GPD) fitting.

3. **Return Level Estimation**
   - Estimation of 1-, 10-, 50- and 100-year return levels.
   - Comparison of GEV and POT approaches.
   - Return period visualisation.

**Selected POT results:**

| Parameter | Result |
|---|---:|
| Selected threshold | 2.05 m |
| Number of independent clusters | 286 |
| GPD shape parameter | -0.3769 |
| GPD scale parameter | 0.2597 m |
| Estimated annual event rate | 286.23 events/year |

**POT return level estimates:**

| Return period | Return level |
|---|---:|
| 1 year | 2.6574 m |
| 10 years | 2.7048 m |
| 50 years | 2.7204 m |
| 100 years | 2.7247 m |

**Important limitation:** The analysis is based on approximately one year of hourly observations. Consequently, long return period estimates are highly uncertain and should not be treated as design values for offshore engineering applications.

**Deliverable:**
- `Jubilee_TRP3_Extreme_Value_Analysis.ipynb`

### Case Study 3: Metocean-Fatigue Correlation and Predictive Modelling

**Objective:** Develop a spectral fatigue calculation workflow using metocean conditions and investigate the ability of polynomial regression models to predict estimated hourly fatigue damage.

**Key activities:**

1. **Wave Spectral Modelling**
   - Implementation of the JONSWAP wave spectrum.
   - Reconstruction and validation of significant wave height from the generated spectrum.

2. **Wave-to-Stress Response**
   - Development of an illustrative frequency-dependent transfer function.
   - Calculation of the stress response spectrum.

3. **Spectral Fatigue Assessment**
   - Calculation of spectral moments.
   - Application of the narrow-band fatigue damage approximation.
   - Estimation of hourly fatigue damage across 8,760 observations.

4. **Predictive Modelling**
   - Development of polynomial regression models of Degrees 1, 2 and 3.
   - Model evaluation using R² and Mean Absolute Error (MAE).
   - Five-fold time-series cross-validation.
   - Residual analysis and model performance comparison.

5. **Fatigue Monitoring Visualisation**
   - Monthly fatigue damage accumulation.
   - Significant wave height versus hourly fatigue damage.
   - Predicted versus actual fatigue damage.
   - Cumulative fatigue damage trajectory.

**Model performance:**

| Model | Test R² | Cross-validation Mean R² |
|---|---:|---:|
| Degree 1 | 0.8102 | 0.8567 |
| Degree 2 | 0.9845 | 0.9735 |
| Degree 3 | 0.9996 | 0.9970 |

Degree 3 achieved the strongest predictive performance among the three models.

**Key output:**
- Hourly fatigue correlation dataset containing 8,760 observations.
- Comparative polynomial regression model performance report.
- Fatigue monitoring visualisations.

**Deliverables:**
- `Jubilee_TRP3_Metocean_Fatigue_Correlation.ipynb`
- `Jubilee_TRP3_Fatigue_Correlation_Dataset.csv`
- `Jubilee_TRP3_Model_Performance_Report.csv`

**Important engineering limitation:** The wave-to-stress transfer function used in this exercise is illustrative and has not been calibrated against OrcaFlex simulations, measured structural response or actual riser properties. The calculated fatigue damage is therefore a computational demonstration, not a validated offshore structural integrity assessment. The S-N curve and stress-unit conventions also require engineering verification.

---

## Tools and Technologies

| Tool / Library | Application |
|---|---|
| Python | Data processing and analysis |
| Jupyter Notebook / Google Colab | Interactive development and documentation |
| Pandas | Data manipulation and analysis |
| NumPy | Numerical computations |
| Matplotlib | Data visualisation |
| Seaborn | Statistical visualisation |
| SciPy | Statistical distributions and numerical methods |
| Scikit-learn | Polynomial regression, preprocessing and model evaluation |
| Git / GitHub | Version control and project documentation |

---

## Repository Structure

```text
Jubilee-TRP3-Metocean-Analysis/
│
├── Case_Study_1/
│   ├── Metocean_EDA_and_Feature_Engineering.ipynb
│   └── Jubilee_TRP3_Metocean_Enriched.csv
│
├── Case_Study_2/
│   └── Jubilee_TRP3_Extreme_Value_Analysis.ipynb
│
├── Case_Study_3/
│   ├── Jubilee_TRP3_Metocean_Fatigue_Correlation.ipynb
│   ├── Jubilee_TRP3_Fatigue_Correlation_Dataset.csv
│   └── Jubilee_TRP3_Model_Performance_Report.csv
│
└── README.md
```

## Overall Learning Outcomes

Through these case studies, the project demonstrates practical application of:

- Python-based metocean data processing and exploratory analysis.
- Time-series analysis and feature engineering.
- Extreme value statistics using GEV and GPD distributions.
- Threshold selection and declustering for POT analysis.
- Wave spectral modelling using the JONSWAP spectrum.
- Spectral fatigue damage estimation using a narrow-band approximation.
- Polynomial regression and time-series cross-validation.
- Model evaluation, residual analysis and data visualisation.

The project also highlights the importance of understanding the physical assumptions behind data-driven models and distinguishing between computational predictions and validated engineering assessments.

---

## Disclaimer

This project is an educational and analytical exercise developed using the supplied Jubilee TRP3 metocean dataset.

The statistical estimates and fatigue calculations are intended for learning, exploratory analysis and demonstration of Python-based workflows. They should not be used directly for offshore design, structural integrity decisions, operational limits or remaining-life assessments without appropriate engineering validation.

---

## Author

**Hassanat Jibril Mohammed**

Geoscience | Python | Data Analytics | Predictive AI/ML | Offshore Asset Integrity

