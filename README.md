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
- Reusable helpers and consistent folder structure

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

## 🚀 Getting Started
1. **Clone** the repo
   ```bash
   git clone https://github.com/AlanYu0321/R.git
   cd R
   ```
2. **Open** the project in R / RStudio.
3. **Run** a lab (e.g., an EDA script in `labs/`). If a lab uses local data, place it under `data/` and adjust the path with `here::here("data", "yourfile.csv")`.

### Example: Minimal EDA Template
```r
library(tidyverse)
library(janitor)
library(here)

# 1) Load data
path <- here("data", "mydata.csv")
df <- readr::read_csv(path) |> janitor::clean_names()

# 2) Quick structure & summary
glimpse(df)
skimr::skim(df)

# 3) Transform
summary_tbl <- df |> 
  filter(!is.na(target_var)) |> 
  group_by(category) |> 
  summarise(n = n(), mean_val = mean(numeric_col, na.rm = TRUE), .groups = "drop")

# 4) Visualize
p <- df |> 
  ggplot(aes(x = numeric_col)) +
  geom_histogram(bins = 30) +
  labs(title = "Distribution of numeric_col", x = "numeric_col", y = "Count")
print(p)

# 5) Save outputs
readr::write_csv(summary_tbl, here("outputs", "summary.csv"))
ggplot2::ggsave(here("outputs", "numeric_col_histogram.png"), p, width = 8, height = 5, dpi = 300)
```

## 🗂️ Suggested Project Layout
```
R/
├─ data/               # Raw input data (not tracked by git if large/sensitive)
├─ outputs/            # Exported figures / tables
├─ labs/               # R scripts or .Rmd notebooks
│  ├─ 01_eda_basics.R
│  ├─ 02_tidy_transformations.R
│  ├─ 03_visualization_ggplot.R
│  └─ 04_simple_stats.R
├─ R/                  # Optional reusable functions (source with devtools::load_all or source())
│  └─ utils.R
└─ README.md
```
> Add a `.gitignore` rule for `data/` and `outputs/` if files are large or private.

## 📊 Common Plot Recipes
```r
# Boxplot by group
mtcars |> ggplot(aes(x = factor(cyl), y = mpg)) +
  geom_boxplot() +
  labs(x = "Cylinders", y = "MPG")

# Scatter with smoother
mtcars |> ggplot(aes(wt, mpg)) +
  geom_point(alpha = 0.6) +
  geom_smooth(method = "loess", se = FALSE)
```

## 🧪 Reproducibility (optional)
Use **renv** to lock package versions for stable results:
```r
install.packages("renv")
renv::init()      # creates renv.lock
renv::snapshot()  # update lockfile after installing packages
```

## 🗺️ Roadmap
- [ ] Add sample datasets under `data/` with a small README per dataset
- [ ] Convert some labs to `.Rmd` for HTML reports
- [ ] Add `renv` lockfile and `DESCRIPTION` for reproducibility
- [ ] Create `R/utils.R` for helper functions (e.g., theme, scales)

## 🤝 Contributing
1. Fork → create a feature branch → commit → open a PR
2. For new labs, follow the naming convention `NN_topic.R` and include a short header with purpose, inputs, and outputs.

## 📄 License
Add a license (e.g., MIT) at the repo root so others know how they can use the code.

## 👤 Author
- Maintainer: Alan Yu (GitHub: `AlanYu0321`)

---
**How to use this README**: Save this file as `README.md` in the repo root. Update examples and package lists as your labs evolve. Add badges, screenshots, or rendered HTML reports as you go.
