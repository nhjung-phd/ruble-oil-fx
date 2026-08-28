# Replication Materials: Russian Ruble Oil–Exchange Rate Linkage

This repository provides replication materials for the study:

**Changes in the Russian Ruble’s Oil–Exchange Rate Linkage after the Russia–Ukraine War: An Analysis of Structural Change and Predictive Information**

## Repository status

This repository is intended as a reproducibility package for academic review and publication. The code downloads public financial time-series data from Yahoo Finance using `yfinance`; raw Yahoo Finance data are **not redistributed** in this repository.

The final source notebook is designed to be run directly. Tables and figures are displayed **inline inside the notebook**. No `outputs/` folder is included, and no files are written by default.

## Recommended citation

Pae, Y. H., Ahn, T. B., & Jung, N. H. (2026). *Changes in the Russian Ruble’s Oil–Exchange Rate Linkage after the Russia–Ukraine War: An Analysis of Structural Change and Predictive Information*. Replication materials.

## Data source

- Source: Yahoo Finance via `yfinance`
- Frequency: weekly (`interval="1wk"`)
- Sample period: January 2019 to April 2026
- Raw-data download endpoint: May 1, 2026
- Structural break date: February 24, 2022

## Exchange-rate convention

The exchange-rate variables are measured as **local-currency units per U.S. dollar**.

| Variable | Yahoo Finance ticker | Interpretation |
|---|---:|---|
| RUB | `RUB=X` | Rubles per U.S. dollar |
| UAH | `UAH=X` | Hryvnias per U.S. dollar |
| KRW | `KRW=X` | Korean won per U.S. dollar |
| JPY | `JPY=X` | Japanese yen per U.S. dollar |
| CAD | `CAD=X` | Canadian dollars per U.S. dollar |
| NOK | `NOK=X` | Norwegian kroner per U.S. dollar |
| KZT | `KZT=X` | Kazakhstani tenge per U.S. dollar |
| EUR | `EURUSD=X` | Reported as U.S. dollars per euro; inverted to euros per U.S. dollar before analysis |

Therefore, an increase in an exchange-rate variable indicates depreciation of the local currency against the U.S. dollar.

## Main methods

The analysis includes:

1. OLS regressions by country and period
2. Granger predictive-power tests
3. GARCH(1,1) volatility models
4. Chow structural-break tests
5. Newey–West HAC auxiliary interaction analysis
6. Robustness check excluding the March–May 2020 COVID-19 oil-price collapse period
7. Student-t GARCH sensitivity analysis
8. Supplementary comparison-group analysis

## Repository structure

```text
russia-ukraine-ruble-oil-fx-linkage/
├── README.md
├── requirements.txt
├── environment.yml
├── .gitignore
├── LICENSE
├── CITATION.cff
├── notebooks/
│   └── 01_full_replication.ipynb
├── data/
│   ├── raw/
│   └── processed/
├── docs/
│   └── paper_title.txt
└── scripts/
    └── README.md
```

## How to run

### Option 1: Google Colab

Open `notebooks/01_full_replication.ipynb` in Google Colab and run all cells.

### Option 2: Local Python environment

```bash
git clone https://github.com/<YOUR_GITHUB_ID>/russia-ukraine-ruble-oil-fx-linkage.git
cd russia-ukraine-ruble-oil-fx-linkage
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter lab
```

Then open and run:

```text
notebooks/01_full_replication.ipynb
```

## Output behavior

The notebook displays tables and figures inline. It does **not** create an `outputs/` folder and does **not** export CSV, Excel, PNG, or PDF files by default.

If users want to save tables or figures, they may add their own export commands locally.

## Reproducibility notes

- Missing observations are forward- and backward-filled before remaining missing rows are dropped.
- Variables are transformed into weekly log differences or rates of change.
- The war date is fixed at February 24, 2022.
- The maximum lag in the Granger predictive-power tests is one week.
- The Newey–West HAC maximum lag is five weeks.
- GARCH estimates can be sensitive to distributional assumptions and boundary solutions; Student-t GARCH sensitivity checks are included.
- Some results may vary slightly if Yahoo Finance revises historical data or if package versions change.

## License

- Code: MIT License
- Data: downloaded by users from Yahoo Finance; not redistributed
