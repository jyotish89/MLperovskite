# MLperovskite
# Hardened Perovskite Band-Gap Uncertainty Quantification Pipeline

An end-to-end, reproducible Python pipeline for evaluating prediction intervals and uncertainty quantification (UQ) models on perovskite band-gap datasets (`master_composition_bandgap.csv`).

---

## Key Pipeline Features

* **Strict Grouping Discipline**: Grouped by chemical `formula` across low- and high-fidelity pools to prevent data leakage.
* **Tuned Machine Learning Models**: Single-pass parameter tuning on low-fidelity data using `GroupKFold` for base, lower-quantile, and upper-quantile `HistGradientBoostingRegressor` models.
* **Four-Method UQ Benchmark**: Repeated 20-seed evaluations comparing:
  1. Global Split Conformal Prediction
  2. Mondrian Conformal Prediction (B-site stratification with threshold $N=10$)
  3. Quantile Gradient Boosting
  4. Gaussian Process Regression (GPR sensitivity ladder up to 4,000 samples)
* **Extrapolation Analysis**: Comprehensive B-site, A-site, and X-site Leave-One-Group-Out (LOBO) evaluation across 5 fixed seeds.
* **Statistically Rigorous Metrics**: Wilson score confidence intervals for individual empirical coverage calculations and percentile bootstrap intervals across seed repetitions.

---

## Directory Structure

```text
project/
├── data/
│   └── cleaned_perovskite.csv
├── src/
│   ├── config.py
│   ├── data_validation.py
│   ├── preprocessing.py
│   ├── tuning.py
│   ├── models.py
│   ├── conformal.py
│   ├── repeated_evaluation.py
│   └── metrics_ci.py
├── scripts/
│   ├── run_validation.py
│   ├── run_tuning.py
│   ├── run_repeated_benchmark.py
│   ├── run_lobo.py
│   └── build_report.py
├── results/
│   ├── figures/
│   ├── tables/
│   ├── markdown/
│   └── latex/
├── requirements.txt
└── README.md
