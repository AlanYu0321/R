# R — Data Analysis & Visualization Labs

> A collection of small, focused R labs for data loading, wrangling, visualization, and introductory statistics.

## 🌟 Overview
This repository contains hands‑on labs written in R to explore real datasets, build tidy data workflows, and create publication‑quality graphics. It’s designed to be simple to run locally and easy to extend.

## 📁 Repository Structure
```
R/
├─ labs/               # Self‑contained lab scripts / notebooks
├─ README.md           # You are here
└─ .gitignore
```
> Tip: keep each lab independent with its own input/output paths so it’s easy to run labs in any order.

## ✨ Key Features
- Data loading from CSV/TSV and other common formats
- Tidy transformations (filter/select/mutate/group_by/summarise)
- Exploratory Data Analysis (EDA): summary tables & quick checks
- Visualizations with **ggplot2** (histogram, boxplot, bar/line/scatter)

## 🧰 Requirements
- **R** ≥ 4.2
- Recommended IDE: **RStudio** (optional)
- Core packages (install on first run):
  - `tidyverse` (ggplot2, dplyr, readr, tidyr, purrr, stringr, forcats)
  - `janitor` (clean column names & quick crosstabs)
  - `skimr` or `summarytools` (fast EDA)
  - `here` (reliable project paths)

Install once in R:
```r
install.packages(c("tidyverse", "janitor", "skimr", "here"))
```