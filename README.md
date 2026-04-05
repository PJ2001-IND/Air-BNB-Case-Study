# 🏠 Airbnb NYC 2019 — Case Study (EDA + Tableau Dashboard)

![Python](https://img.shields.io/badge/Python-3.8+-blue?style=flat-square&logo=python)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?style=flat-square&logo=jupyter)
![Tableau](https://img.shields.io/badge/Tableau-Dashboard-E97627?style=flat-square&logo=tableau)
![Pandas](https://img.shields.io/badge/Pandas-EDA-150458?style=flat-square&logo=pandas)
![Seaborn](https://img.shields.io/badge/Seaborn-Visualisation-4C72B0?style=flat-square)

> An end-to-end **Exploratory Data Analysis (EDA) and Tableau dashboard case study** on the New York City Airbnb 2019 dataset — covering 48,895 listings across all 5 NYC boroughs. The study uncovers pricing patterns, host behaviour, room type distributions, neighbourhood demand, and review trends, with the cleaned data exported to power an 11-sheet interactive Tableau workbook.

---

## 📌 Problem Statement

The short-term rental market in New York City is one of the most competitive in the world. With nearly 49,000 listings in 2019 spanning Manhattan, Brooklyn, Queens, the Bronx, and Staten Island, understanding what drives pricing, availability, and demand is critical for hosts, guests, and business analysts alike. This case study performs a structured EDA on the NYC Airbnb 2019 dataset to uncover:

- **Which neighbourhoods and room types command the highest prices?**
- **How do host listing counts, availability, and reviews vary across boroughs?**
- **What are the outlier patterns in price and minimum nights, and how should they be treated?**

---

## 🎯 Objectives

- Perform end-to-end data cleaning and exploratory analysis on the NYC Airbnb 2019 dataset
- Identify and treat outliers in `price` and `minimum_nights` using quantile-based capping (99.7th percentile)
- Analyse pricing, availability, reviews, and host behaviour across all 5 NYC neighbourhood groups
- Export the cleaned dataset (`AB_NYC_2019_Updated.csv`) for Tableau visualisation
- Build an **11-sheet Tableau dashboard** covering price, reviews, availability, room type, and host analytics

---

## 📂 Dataset

| Property | Detail |
|---|---|
| File | `AB_NYC_2019.csv` |
| Source | Airbnb NYC — publicly available 2019 listings data |
| Records | 48,895 listings |
| Features | 16 columns |
| Coverage | All 5 NYC boroughs — Manhattan, Brooklyn, Queens, Bronx, Staten Island |
| Unique Neighbourhoods | 221 |
| Unique Hosts | 37,457 |
| Price Range | \$0 — \$10,000/night (mean: \$152.72, median: \$106) |
| Avg. Availability | 112.78 days/year |

### Dataset Columns

| Column | Description |
|---|---|
| `id` | Unique listing ID — dropped before analysis |
| `name` | Listing name — dropped before analysis |
| `host_id` | Unique host identifier |
| `host_name` | Host name |
| `neighbourhood_group` | NYC borough (Manhattan: 21,661 / Brooklyn: 20,104 / Queens: 5,666 / Bronx: 1,091 / Staten Island: 373) |
| `neighbourhood` | Specific neighbourhood (221 unique) |
| `latitude` / `longitude` | Geolocation coordinates |
| `room_type` | Entire home/apt (25,409) / Private room (22,326) / Shared room (1,160) |
| `price` | Nightly price in USD |
| `minimum_nights` | Minimum booking duration (max: 1,250 nights) |
| `number_of_reviews` | Total number of guest reviews |
| `last_review` | Date of last review — dropped (10,052 nulls) |
| `reviews_per_month` | Average monthly reviews (10,052 nulls → filled with 0) |
| `calculated_host_listings_count` | Number of listings per host |
| `availability_365` | Days available per year (0–365) |

---

## 🔬 Methodology

```
AB_NYC_2019.csv (48,895 records, 16 columns)
   │
   ▼
Data Understanding & Initial Inspection
   │   ├── Shape, dtypes, null counts, duplicate check
   │   ├── Unique value counts per column
   │   └── Null percentage audit — last_review (20.56%), reviews_per_month (20.56%)
   │
   ▼
Data Cleaning
   │   ├── Drop redundant columns: id, name, last_review
   │   └── Fill reviews_per_month nulls with 0
   │       (listings with 0 reviews have no monthly review rate)
   │
   ▼
Exploratory Data Analysis (EDA)
   │   ├── Numerical Variables Analysis
   │   │     ├── Descriptive stats — price, minimum_nights, reviews, availability
   │   │     ├── Pairplot — numeric features cross-correlation
   │   │     └── Correlation heatmap (upper triangle, YlGnBu palette)
   │   │
   │   ├── Outlier Detection & Treatment
   │   │     ├── Price: boxplot → quantile binning → drop above 99.7th percentile
   │   │     │     (price capped at $1,500 — 273 extreme rows removed)
   │   │     ├── Minimum Nights: boxplot → quantile binning → drop above 99.7th percentile
   │   │     └── Replot boxplots + distplots after treatment
   │   │
   │   └── Categorical Variables Analysis
   │         ├── Countplots — room_type vs neighbourhood_group
   │         ├── Unique value inspection — neighbourhood (221), room_type (3), group (5)
   │         └── Value counts — neighbourhood_group, neighbourhood, room_type
   │
   ▼
Export Cleaned Data
   │   └── df.to_csv("AB_NYC_2019_Updated.csv")
   │       → 48,622 records, 14 columns (273 outlier rows removed)
   │
   ▼
Tableau Dashboard (AIR_BNB_CASE_STUDY.twb — 11 sheets)
       ├── Price Analyses Per Night
       ├── Avg. Price Neighbourhood Distribution
       ├── Average Price Vs Neighbourhood Group
       ├── Room Type Price Analysis
       ├── Minimum Nights Vs Host Listing
       ├── Host Vs Availability 365
       ├── Max. Reviews Vs Host
       ├── Number Of Host Listing Per Housing Type
       ├── Number Of Reviews Per Listing
       ├── No. Of Listing Per Neighbourhood Group And Avg. Review Per Month
       └── By Neighbourhood Group
```

---

## 📊 Results

| Metric | Value |
|---|---|
| Raw Records | 48,895 listings |
| Cleaned Records | 48,622 listings (273 outlier rows removed) |
| Price after cleaning | Max capped at \$1,500 (mean: \$143.60) |
| Minimum Nights after cleaning | Capped at 99.7th percentile |
| Null values after cleaning | 0 (except host_name: 21) |
| Tableau Sheets | 11 interactive visualisations |

> 📝 *Refer to `AIR_BNB_CASE_STUDY.ipynb` for full EDA code, boxplots, distribution plots, pairplots, and correlation heatmaps. Open `AIR_BNB_CASE_STUDY.twb` in Tableau Desktop to explore the interactive 11-sheet dashboard.*

---

## 💡 Key Insights

- **Manhattan commands the highest prices** — significantly above all other boroughs, driven by Entire home/apt listings in premium neighbourhoods
- **Brooklyn is the most active borough** after Manhattan with 20,104 listings, offering more affordable pricing
- **Entire home/apt is the dominant room type** (25,409 listings — 51.97%), followed closely by Private room (22,326 — 45.66%)
- **Price outliers are extreme** — before cleaning, prices ranged from \$0 to \$10,000/night; after 99.7th percentile capping they are capped at \$1,500
- **Minimum nights also has extreme outliers** — some listings require up to 1,250 nights; treated with same 99.7th percentile approach
- **10,052 listings (20.56%)** have never received a review — reflected by null `last_review` and `reviews_per_month`, correctly filled with 0
- **High host listing count** does not correlate strongly with higher prices — indicates professional hosts operate across price ranges
- The Tableau dashboard reveals **geographical clustering** of high-price listings in lower Manhattan, with availability and review patterns varying significantly by borough

---

## 🛠️ Tech Stack

| Tool | Purpose |
|---|---|
| Python 3.8+ | Core programming language |
| Pandas | Data loading, cleaning, null handling, outlier treatment, CSV export |
| NumPy | Numerical operations and array masking |
| Matplotlib / Seaborn | EDA visualisations — boxplots, distplots, pairplots, countplots, heatmaps |
| Jupyter Notebook | Interactive EDA development environment |
| Tableau Desktop | 11-sheet interactive dashboard on cleaned dataset |

---

## 🚀 Getting Started

### Prerequisites

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

### Run the Notebook

```bash
# Clone the repository
git clone https://github.com/PJ2001-IND/Air-BNB-Case-Study.git

# Navigate to the project directory
cd Air-BNB-Case-Study

# Launch Jupyter Notebook
jupyter notebook AIR_BNB_CASE_STUDY.ipynb
```

### Open the Tableau Dashboard

```
1. Open Tableau Desktop
2. Open AIR_BNB_CASE_STUDY.twb
3. Ensure AB_NYC_2019_Updated.csv is in the same directory as the .twb file
4. Explore all 11 dashboard sheets
```

---

## 📁 Project Structure

```
📦 Air-BNB-Case-Study
 ┣ 📓 AIR_BNB_CASE_STUDY.ipynb          # Full EDA pipeline and data cleaning notebook
 ┣ 📊 AIR_BNB_CASE_STUDY.twb            # Tableau workbook — 11-sheet interactive dashboard
 ┣ 📄 AB_NYC_2019.csv                   # Raw Airbnb NYC 2019 dataset (48,895 records, 16 features)
 ┣ 📄 AB_NYC_2019_Updated.csv           # Cleaned dataset exported from notebook (48,622 records, 14 features)
 ┣ 📄 requirements.txt                  # Python dependencies
 ┗ 📄 README.md                         # Project documentation
```

---

## 🔭 Future Scope

- Build a **price prediction model** using the cleaned dataset — Linear Regression or XGBoost on neighbourhood, room type, and availability features
- Extend the Tableau dashboard with **geospatial mapping** of listing density and price heatmaps across NYC zip codes
- Incorporate **time-series analysis** using review dates to track demand seasonality across months
- Apply **clustering (K-Means)** to segment listings into tiers — budget, mid-range, premium — for targeted host and guest recommendations
- Integrate **live Airbnb data** via the Inside Airbnb API for real-time market tracking
- Deploy insights as a **Streamlit web app** for interactive neighbourhood and price exploration

---

## 👤 Author

**Praasuk Jain**
- GitHub: [@PJ2001-IND](https://github.com/PJ2001-IND)
- LinkedIn: [praasuk-jain](https://www.linkedin.com/in/praasuk-jain-425b6b1a3/)

---

> ⭐ If you found this project useful, consider giving it a star!
