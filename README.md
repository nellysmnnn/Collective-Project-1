# Video Game Sales Analysis: Finding Successful Strategies for 2017

## Overview

The gaming industry releases hundreds of titles every year, but not all of them become profitable. This project analyzes historical video game sales data (through 2016) to identify which platforms, genres, and factors drive commercial success, and uses those insights to build recommendations for planning game releases in 2017.

## Dataset

The analysis uses `games.csv`, containing per-game records with the following fields:

- `Name`, `Platform`, `Year_of_Release`, `Genre`
- Regional sales figures: `NA_sales`, `EU_sales`, `JP_sales`, `Other_sales`
- `Critic_Score`, `User_Score`, `Rating` (ESRB)

## Project Workflow

**1. Data Loading & Inspection**
Initial review of the dataset to identify missing values, incorrect column names, and data type issues.

**2. Data Preparation**
- Standardized column names to lowercase
- Dropped rows missing `name`, `genre`, or `year_of_release` (critical fields)
- Left `user_score` and `critic_score` missing values untouched to avoid biasing later analysis; converted `'tbd'` entries in `user_score` to `NaN` so the column could be treated numerically
- Filled missing `rating` values with `'unknown'`
- Corrected data types (e.g., `year_of_release` to integer, `user_score` to numeric)
- Added a `total_sales` column (sum of all regional sales)
- Identified and removed duplicate records

**3. Exploratory Data Analysis**
- Examined game release volume by year
- Analyzed total sales by platform and modeled platform lifecycles (finding a typical ~10-year cycle: launch, growth, decline)
- Narrowed analysis to a "current" period (2013–2016) to reflect up-to-date market trends
- Compared sales distributions across top platforms via box plots
- Investigated correlation between critic/user scores and sales (both for a single platform and across multiple platforms)
- Analyzed sales distribution by genre

**4. Regional User Profiles**
For North America, Europe, and Japan, identified the top platforms, top genres, and ESRB rating patterns driving regional sales.

**5. Hypothesis Testing**
Two independent-samples t-tests (α = 0.05):
- H₀: Average user ratings are equal between Xbox One and PC → **not rejected** (no significant difference)
- H₀: Average user ratings are equal between Action and Sports genres → **rejected** (significant difference found)

## Key Findings

- **Platform lifecycle:** Platforms typically follow a ~10-year cycle — a sharp 2–3 year growth phase, a mid-cycle sales peak, then decline.
- **Top platforms:** PS4 and Xbox 360 show the strongest and most consistent sales in the recent period.
- **Genres:** Shooter, Sports, and Action are the most commercially successful genres; Adventure, Puzzle, Simulation, and Strategy are lower-performing/niche.
- **Reviews:** Critic scores show a moderate positive correlation with sales; user scores show little to no correlation, suggesting professional reviews carry more weight in purchase decisions.
- **Regional differences:**
  - *North America:* Favors Microsoft/Sony consoles; Action, Shooter, and Sports genres lead.
  - *Europe:* Similar to NA, but with stronger Racing sales; Sony leads over Microsoft.
  - *Japan:* Strongly favors handheld consoles (3DS, PSV) and Nintendo hardware; RPG dominates, while Western genres like Shooter and Sports are minor.
- **ESRB ratings:** Meaningful influence on sales in NA/EU (favoring "E" and "M" ratings); negligible effect in Japan.

## Recommendations for 2017

- Prioritize game development and marketing for **PS4** and **Xbox 360**.
- Focus on **Action, Shooter, and Sports** genres for maximum reach and revenue.
- Leverage strong critic reviews in marketing materials.
- Tailor Western marketing campaigns around ESRB age ratings.
- For the Japanese market, prioritize handheld platforms and RPG titles.
- Base planning decisions on the 2013–2016 data window, as it best reflects current market trends.

## Tools & Libraries

- `pandas`, `numpy` — data manipulation
- `matplotlib`, `seaborn` — visualization
- `scipy.stats` — hypothesis testing (t-tests)

## How to Run

1. Place `games.csv` in the project directory.
2. Open `collective_project_1.ipynb` in Jupyter Notebook/JupyterLab.
3. Run all cells in order — the notebook proceeds sequentially from data loading through analysis, regional profiling, and hypothesis testing.

## Requirements

```
pandas
numpy
matplotlib
seaborn
scipy
```
