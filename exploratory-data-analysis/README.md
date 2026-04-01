# AAL Apparel — Q4 2020 Sales Analysis

> **Course-End Project | Applied Data Science with Python**
> Analysing fourth-quarter sales data for AAL Apparel across all Australian states to support data-driven investment decisions for the S&M leadership team.

---

## Table of Contents
- [Project Overview](#project-overview)
- [Dataset](#dataset)
- [Project Structure](#project-structure)
- [Methodology](#methodology)
- [Key Findings](#key-findings)
- [Technologies Used](#technologies-used)
- [How to Run](#how-to-run)
- [Results & Report](#results--report)

---

## Project Overview

AAL is a well-established Australian apparel brand (founded 2000) catering to all demographic groups — Kids, Men, Women, and Seniors — across seven states. With business surging, the CEO tasked the Sales & Marketing (S&M) head with two objectives:

1. **Identify** the states generating the highest revenues.
2. **Develop** targeted sales programs for lower-performing states.

This project delivers a full end-to-end data science pipeline — wrangling, statistical analysis, visualisation, and a strategic report — to answer both questions with evidence.

---

## Dataset

| Property | Detail |
|----------|--------|
| **File** | `AusApparalSales4thQrt2020.csv` |
| **Period** | October 1 – December 31, 2020 (Q4) |
| **Rows** | 7,560 transactions |
| **Columns** | 6 (`Date`, `Time`, `State`, `Group`, `Unit`, `Sales`) |
| **States** | WA, NT, SA, VIC, QLD, NSW, TAS |
| **Groups** | Kids, Men, Women, Seniors |
| **Time slots** | Morning, Afternoon, Evening |

---

## Project Structure

```
├── AAL_Sales_Analysis_Clean.ipynb   # Main analysis notebook (Google Colab)
├── AAL_Q4_2020_Sales_Analysis_Report.docx  # Full business report
├── AusApparalSales4thQrt2020.csv    # Source dataset
└── README.md
```

---

## Methodology

### 1. Data Wrangling
- Inspected for missing values using `isna()` / `notna()` — none found
- Converted `Date` column from `object` → `datetime64`
- Detected and stripped leading whitespace from all categorical columns (`Time`, `State`, `Group`)
- Retained high-value outliers (valid bulk transactions, not errors)
- Applied **Min-Max Normalization** to `Sales` and `Unit` columns (preferred over standardization given the non-normal distribution)
- Used `GroupBy` for **data chunking** — segmenting by State, Group, and Time for independent aggregate comparisons

### 2. Data Analysis
- Descriptive statistics: mean, median, mode, std, skewness, kurtosis
- Shapiro-Wilk normality test — confirmed right-skewed, non-normal distribution
- Group-level and state-level sales aggregation
- Time-of-day peak analysis
- Weekly, monthly, quarterly, and daily resampling using Pandas `resample()`
- Units–Sales regression (near-perfect linear correlation, R² ≈ 1.0)

### 3. Data Visualisation
- Box plots — outlier detection
- KDE histograms — distribution analysis
- Bar charts — group, state, and time-of-day comparisons
- Heatmap — Group × State cross-tabulation
- Regression scatter plot — Units vs. Sales relationship
- Time-series line charts — daily, weekly, monthly, quarterly trends
- **Interactive Plotly dashboard** — 6-panel strategic summary for S&M leadership

### 4. Report Generation
- Full narrative report with findings, insights, and strategic recommendations
- Markdown-integrated throughout the notebook

---

## Key Findings

| # | Finding |
|---|---------|
| 1 | **VIC dominates** — $105.6M in Q4, nearly 4.8× the lowest state (WA at $22.2M) |
| 2 | **Balanced demographics** — all four groups contribute ~25% each; universal brand appeal confirmed |
| 3 | **November trough** — revenue dipped 20.7% in November before a 49.2% December surge |
| 4 | **Flat time-of-day split** — Morning/Afternoon/Evening within 2% of each other; Evening is the only underperformer |
| 5 | **Constant price per unit** — R² ≈ 1.0; revenue growth is entirely volume-driven at current pricing |
| 6 | **Right-skewed distribution** — median ($35K) is a far better benchmark than the mean ($45K) for target-setting |

---

## Technologies Used

| Library | Purpose |
|---------|---------|
| `pandas` | Data manipulation, cleaning, resampling |
| `numpy` | Numerical operations |
| `scipy` | Shapiro-Wilk normality test |
| `matplotlib` | Base plotting, multi-panel charts |
| `seaborn` | Statistical visualisation (box plots, heatmaps, KDE, regression) |
| `plotly` | Interactive executive dashboard |
| `sklearn` | Min-Max normalization |

---

## How to Run

### Option 1 — Google Colab (recommended)
1. Open `AAL_Sales_Analysis_Clean.ipynb` in [Google Colab](https://colab.research.google.com/)
2. Run all cells — the notebook automatically clones the dataset from this repository
3. No additional setup required

### Option 2 — Local Jupyter
```bash
# 1. Clone this repository
git clone https://github.com/MM33NA/AI-machine-learning-projects.git
cd AI-machine-learning-projects/exploratory-data-analysis

# 2. Install dependencies
pip install pandas numpy scipy matplotlib seaborn plotly scikit-learn

# 3. Launch Jupyter
jupyter notebook AAL_Sales_Analysis_Clean.ipynb
```

---

## Results & Report

The full business report (`AAL_Q4_2020_Sales_Analysis_Report.docx`) includes:
- Executive summary with Q4 KPIs
- State-by-state and demographic-group breakdowns
- Time-of-day and time-series analysis
- 5 prioritised strategic recommendations for the S&M team

**Top recommendation:** A dedicated **November Activation Campaign** (Black Friday / Cyber Week / pre-Christmas) targeting the ~$24M November revenue gap is the single highest-impact, lowest-risk action available for Q4 2021 planning.

---

*Applied Data Science with Python — Course-End Project*
