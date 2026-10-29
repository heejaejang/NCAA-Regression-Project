# Predicting College Basketball Scoring Through NCAA Data

## Overview

A two-part analysis of scoring among NCAA Division I men's basketball players:

- **Part 1: What explains scoring?** Which player-level factors are associated with points per game within the 2022 season.
- **Part 2: Can next season be forecast?** Once a player's 2022 performance is known, does his high-school recruiting ranking still help predict his 2023 scoring?

**About the code:** the analysis was originally written in R (`NCAA_Regression_Analysis.Rmd`), which is kept in the repository as the original code. The Python notebooks are the updated, improved version: rewritten with reusable functions, corrected validation, cross-validation, and an extended forecasting analysis (Part 2).

## Files

| File | Description |
|---|---|
| `NCAA_Regression_Analysis.ipynb` | **Part 1 (Python, current version):** what explains points per game in 2022 |
| `NCAA_Next_Season_Forecast.ipynb` | **Part 2 (Python):** forecasting 2023 scoring from 2022 statistics and recruiting rank |
| `NCAA_Regression_Analysis.Rmd` | Original Part 1 analysis in R |
| `data/CollegeBasketballPlayers2022.csv` | 2022 player statistics (Kaggle, compiled from Bart Torvik) |
| `data/CollegeBasketballPlayers2023.csv` | 2023 player statistics (Bart Torvik export, no header row) |

## Research Questions

1. **Part 1:** How do shooting efficiency, playmaking, possession control, rebounding, defense, and player experience relate to points per game?
2. **Part 2:** Once a player's current-season performance is known, does his recruiting ranking still help predict how he performs next season?

## What Changed From the R Version

- Rewritten in Python (pandas, statsmodels, scikit-learn) with reusable functions in place of repeated code
- Train/test validation corrected: the Box-Cox λ is estimated on training data only, and accuracy is reported in points per game
- An invalid AIC comparison between models with different responses and samples replaced with a like-for-like comparison
- Added 5-fold cross-validation, HC3 robust standard errors, and a Lasso comparison
- Influence diagnostics summarized in readable tables, with the most influential players named
- Redundant tests removed, so each question is answered once with the most appropriate test
- Added Part 2: a new forecasting question using a second season of data

## Dataset

- 2022 and 2023 NCAA Division I men's basketball player statistics (about 4,000 and 5,000 players)
- Seasons linked by player ID: 2,280 players appear in both
- Sources: Kaggle (2022) and Bart Torvik (2023)

## Methods

**Part 1:** data cleaning, exploratory analysis, multiple linear regression, Box-Cox transformation, regression diagnostics, partial F tests, influence diagnostics, VIF, stepwise selection by AIC, held-out test set, 5-fold cross-validation, HC3 robust standard errors, Lasso.

**Part 2:** linking seasons by player ID, survivorship analysis, nested OLS models with and without recruiting rank, partial F tests, HC3 robust standard errors, effect sizes in points per game, 5-fold cross-validation against a naive baseline, a points-per-40-minutes efficiency model, gradient boosting with permutation importance.

## Key Results

**Part 1:**
- A Box-Cox-transformed OLS model (λ ≈ 0.44) predicts points per game with a cross-validated RMSE of about **2.0 points** for players with more than 5% of team minutes, beating the untransformed model (2.08).
- Playing time is the strongest predictor, followed by rebounding, assist rate, and true shooting %; turnover rate and defensive BPM are associated with fewer points.
- The class year × minutes interaction is statistically significant (p = 0.019) but practically negligible for prediction.

**Part 2:**
- Scoring carries over only partly (r = 0.50), so a "same as last season" forecast does worse than predicting the average.
- A model using last season's statistics cuts forecast error from 4.98 to **4.18 points per game**.
- Recruiting rank adds statistically significant information (p = 0.00002; about +1 point per game from rank 25 to rank 75), but barely improves overall accuracy (4.18 → 4.16), since only 39% of players are ranked.
- **Rank predicts role, not efficiency:** it does not predict points per 40 minutes (p = 0.23). Highly ranked recruits score more mainly because they play bigger roles.
- Transfers score less than their statistics predict (p = 0.013), and OLS outperformed gradient boosting.

## Limitations

- One season (Part 1) and one pair of seasons (Part 2); results may not hold in other years.
- Part 1 applies to players with meaningful playing time; Part 2 applies only to players who return the next season (57% of 2022 players).
- The 2022 file appears to be a mid-season snapshot, and its class-year labels are inconsistent with 2023.
- Recruiting ranks are available for only part of the sample.
- Observational data: the results are associations, not causal effects.

## How to Run

Open either notebook in Google Colab. The data files load automatically from this repository, so nothing needs to be uploaded. Required packages: pandas, numpy, matplotlib, seaborn, scipy, statsmodels, scikit-learn.

## Tools

Python · pandas · statsmodels · scikit-learn · matplotlib · seaborn · R (original version)

## Repository Structure

```
├── data/
│   ├── CollegeBasketballPlayers2022.csv
│   └── CollegeBasketballPlayers2023.csv
├── NCAA_Regression_Analysis.ipynb
├── NCAA_Next_Season_Forecast.ipynb
├── NCAA_Regression_Analysis.Rmd
├── README.md
└── .gitignore
```
 
