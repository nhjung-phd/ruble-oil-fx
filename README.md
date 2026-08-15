# ruble-oil-fx

Replication package for the study **"Changes in the Russian Ruble’s Oil–Exchange Rate Linkage after the Russia–Ukraine War: An Analysis of Structural Change and Predictive Information."**

This repository provides Python notebooks and scripts for reproducing the empirical analyses reported in the main text, appendix, and supplementary materials.

## 1. Study Overview

The study examines whether the Russian ruble’s oil–exchange rate linkage changed after the Russia–Ukraine war. The analysis compares the Russian ruble, Ukrainian hryvnia, and Korean won before and after February 24, 2022, and uses additional comparison currencies to assess whether the Russian pattern is distinct from general oil-importer or resource-exporter currency behavior.

Main empirical methods include:

- OLS regressions by country and period
- Granger predictive-power tests
- GARCH(1,1) volatility models
- Chow structural-break tests
- Newey–West HAC auxiliary interaction analysis
- Robustness check excluding the March–May 2020 COVID-19 oil-price collapse period
- Student-t GARCH sensitivity analysis
- Supplementary comparison-group analysis

## 2. Data Source

All data are collected from Yahoo Finance through the `yfinance` Python package.

- Data source: Yahoo Finance via `yfinance`
- Frequency: weekly (`interval="1wk"`)
- Sample period: January 2019 to April 2026
- Raw-data download endpoint: May 1, 2026
- Structural break date: February 24, 2022

Raw Yahoo Finance data are not redistributed in this repository. Users can reproduce the data download by running the notebooks.

## 3. Exchange-Rate Convention

The exchange-rate variables are measured as **local-currency units per U.S. dollar**.

Therefore, an increase in an exchange-rate variable indicates depreciation of the local currency against the U.S. dollar.

| Variable | Yahoo Finance ticker | Interpretation |
|---|---|---|
| RUB | `RUB=X` | Rubles per U.S. dollar |
| UAH | `UAH=X` | Hryvnias per U.S. dollar |
| KRW | `KRW=X` | Korean won per U.S. dollar |
| JPY | `JPY=X` | Japanese yen per U.S. dollar |
| CAD | `CAD=X` | Canadian dollars per U.S. dollar |
| NOK | `NOK=X` | Norwegian kroner per U.S. dollar |
| KZT | `KZT=X` | Kazakhstani tenge per U.S. dollar |
| EUR | `EURUSD=X` | Reported as U.S. dollars per euro; inverted to euros per U.S. dollar before analysis |

This convention is important for interpreting coefficients. For example, if the RUB variable increases, more rubles are required to purchase one U.S. dollar, which indicates ruble depreciation. If the RUB variable decreases, the ruble appreciates against the U.S. dollar.

## 4. Repository Structure

```text
ruble-oil-fx/
├── README.md
├── README_KR.md
├── requirements.txt
├── environment.yml
├── LICENSE
├── CITATION.cff
├── notebooks/
│   ├── 01_full_replication.ipynb
│   └── 02_appendix_robustness_checks.ipynb
├── outputs/
│   ├── tables/
│   └── figures/
├── data/
│   ├── raw/
│   └── processed/
└── scripts/
```

## 5. Notebooks

### `notebooks/01_full_replication.ipynb`

This notebook reproduces the main empirical analyses:

- data collection through `yfinance`
- data preprocessing and exchange-rate transformation
- descriptive statistics and stationarity tests
- OLS regressions
- Granger predictive-power tests
- GARCH(1,1) models
- Chow structural-break tests
- Newey–West auxiliary interaction analysis
- additional comparison-group analysis

### `notebooks/02_appendix_robustness_checks.ipynb`

This notebook reproduces reviewer-requested robustness checks:

- OLS robustness check excluding the March–May 2020 COVID-19 oil-price collapse period
- Student-t GARCH sensitivity analysis
- appendix-style output tables

## 6. How to Run

### Option A. Google Colab

1. Upload the notebooks to Google Colab.
2. Install required packages if needed.
3. Run all cells from top to bottom.

### Option B. Local Python Environment

```bash
git clone https://github.com/<YOUR_GITHUB_ID>/ruble-oil-fx.git
cd ruble-oil-fx
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter lab
```

Then open:

```text
notebooks/01_full_replication.ipynb
```

For robustness checks only, open:

```text
notebooks/02_appendix_robustness_checks.ipynb
```

## 7. Required Python Packages

The main packages are listed in `requirements.txt` and `environment.yml`.

Core packages include:

- `yfinance`
- `pandas`
- `numpy`
- `statsmodels`
- `arch`
- `scipy`
- `matplotlib`
- `jupyter`

## 8. Outputs

The notebooks generate tables and figures under:

```text
outputs/tables/
outputs/figures/
```

Output values may vary slightly depending on Yahoo Finance data revisions and package versions.

## 9. Reproducibility Notes

- Missing observations are forward- and backward-filled before remaining missing rows are dropped.
- Variables are transformed into weekly log differences or rates of change.
- The war date is fixed at February 24, 2022.
- The maximum lag in the Granger predictive-power tests is one week.
- The Newey–West HAC maximum lag is five weeks.
- GARCH estimates can be sensitive to convergence and distributional assumptions; Student-t GARCH sensitivity checks are included.

## 10. Data and Code Availability Statement

The data used in this study were collected from Yahoo Finance through the `yfinance` package. The replication code and analysis scripts are provided in this repository for reproducibility. Raw Yahoo Finance data are not redistributed.

## 11. Citation

Please cite the related article and this repository if you use the materials.

```text
Jung, N. H. (2026). Changes in the Russian Ruble’s Oil–Exchange Rate Linkage after the Russia–Ukraine War: An Analysis of Structural Change and Predictive Information. Replication materials.
```

## 12. License

- Code: MIT License
- Data: downloaded by users from Yahoo Finance; not redistributed
