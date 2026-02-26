# March Machine Learning Mania 2026

Kaggle competition: predict the outcomes of every possible matchup in the
NCAA Men's and Women's Basketball Tournaments.

**Competition:** https://www.kaggle.com/competitions/march-machine-learning-mania-2026/overview/description

---

## Overview

Submissions are evaluated on **log-loss** against the actual 2026 NCAA
tournament results. For every possible game between any two teams that
could meet in the bracket, contestants predict the probability that the
**lower-ID team wins**.

```
ID,Pred
2026_1101_1102,0.5
2026_1101_1103,0.7
```

---

## Notebook

[`march_mania_2026.ipynb`](march_mania_2026.ipynb) – end-to-end research notebook covering:

| Section | Description |
|---------|-------------|
| 0. Kaggle Setup | Install `kaggle` package, download & extract competition CSV files |
| 1. Configuration | `DATA_DIR`, season constants, library imports |
| 2. Data Loading | All competition CSV files with schema overview |
| 3. EDA | Score distributions, seeding upset analysis |
| 4. Feature Engineering | Win %, point differential, Elo ratings, seeds, Massey rankings |
| 5. Model Training | Logistic Regression, XGBoost, LightGBM with 5-fold CV log-loss |
| 6. Ensemble | Weighted average of models with prediction calibration |
| 7. Submission | Clipped predictions saved to `submission.csv` |
| Appendix A | Advanced feature ideas (box-score efficiency, SOS, momentum) |
| Appendix B | Alternative models (Bradley-Terry, Neural Network, Bayesian Elo) |

---

## Quick Start

### Option A – Automatic download via Kaggle API (recommended)

1. Install dependencies:
   ```bash
   pip install kaggle numpy pandas matplotlib seaborn scikit-learn xgboost lightgbm
   ```
2. Set up Kaggle credentials:
   - Go to https://www.kaggle.com/settings → Account → API → **Create New Token**
   - Save the downloaded `kaggle.json` to `~/.kaggle/kaggle.json` (Linux/Mac) or `%USERPROFILE%\.kaggle\kaggle.json` (Windows)
   - Accept the competition rules at https://www.kaggle.com/competitions/march-machine-learning-mania-2026
3. Open and run the notebook – **Section 0** will install `kaggle` and download all CSVs automatically:
   ```bash
   jupyter notebook march_mania_2026.ipynb
   ```

### Option B – Manual download

Download the data manually from the competition page and set `DATA_DIR` in Section 1:

```python
DATA_DIR = '/path/to/march-machine-learning-mania-2026'
```

---

## Key Files (Competition Data)

| File | Description |
|------|-------------|
| `{M/W}Teams.csv` | Team ID ↔ name mapping |
| `{M/W}Seasons.csv` | Season metadata |
| `{M/W}RegularSeasonCompactResults.csv` | Regular season outcomes |
| `{M/W}RegularSeasonDetailedResults.csv` | Regular season with box-score |
| `{M/W}NCAATourneyCompactResults.csv` | Historical tournament outcomes |
| `{M/W}NCAATourneyDetailedResults.csv` | Tournament with box-score |
| `{M/W}NCAATourneySeeds.csv` | Tournament seeds |
| `MMasseyOrdinals.csv` | Massey ordinal rankings (Men's) |
| `{M/W}SampleSubmission.csv` | All 2026 matchup IDs to predict |
