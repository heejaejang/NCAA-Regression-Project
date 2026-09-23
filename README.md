# Predicting College Basketball Scoring Through NCAA Data

## Overview

This project examines which player-level factors are associated with points per game among NCAA men's basketball players with meaningful playing time.

The analysis uses 2022 NCAA basketball statistics and multiple linear regression to investigate the relationship between scoring and factors including shooting efficiency, playmaking, possession control, rebounding, defense, and player experience.

## Research Question

> How do shooting efficiency, playmaking, possession control, rebounding, defense, and player experience influence points per game?

## Dataset

- 2022 NCAA men's basketball player statistics
- ~4,000 players
- ~179 variables
- Source: Kaggle

## Methods

- Data cleaning and variable selection
- Exploratory data analysis
- Multiple linear regression
- AIC-based model selection
- Outlier and influence diagnostics
- Multicollinearity assessment using GVIF
- Box-Cox transformation
- Regression diagnostics

## Key Results

The analysis found significant associations between scoring and several player-level performance measures, particularly playing time and offensive statistics.

## Limitations

- Data represents the 2022 NCAA season only.
- Results primarily apply to players receiving meaningful playing time.
- The observational data cannot establish causal relationships.
- Basketball statistics can be inherently correlated with one another.

## Tools

**R · R Markdown · ggplot2 · dplyr · Statistical Regression**

## Repository Structure

```text
├── data/
├── svg/
├── NCAA_Regression_Analysis.Rmd
├── README.md
└── .gitignore
