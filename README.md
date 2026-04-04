# 🏠 Airbnb New York City — Case Study & EDA

![Python](https://img.shields.io/badge/Python-3.8+-blue?style=flat-square&logo=python)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?style=flat-square&logo=jupyter)
![Tableau](https://img.shields.io/badge/Tableau-Dashboard-lightblue?style=flat-square&logo=tableau)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?style=flat-square&logo=pandas)
![License](https://img.shields.io/badge/License-MIT-lightgrey?style=flat-square)

> A comprehensive case study and exploratory data analysis on **Airbnb listings across New York City (2019)** — uncovering pricing dynamics, neighbourhood demand patterns, host behaviour, and availability trends through Python-based EDA and an interactive Tableau dashboard.

---

## 📌 Problem Statement

Airbnb operates in a highly dynamic, location-sensitive market where pricing and availability vary dramatically across neighbourhoods, room types, and host strategies. This case study analyses NYC Airbnb listing data to answer key business questions:

- Which neighbourhoods command the highest prices — and why?
- What room types dominate different boroughs?
- How do host activity levels affect listing performance?
- What patterns exist in availability and minimum nights policies?
- Are there outliers or anomalies that suggest data quality issues or pricing errors?

---

## 🎯 Objective

- Perform thorough EDA on 48,000+ Airbnb listings across New York City
- Clean and preprocess raw listing data (handle nulls, outliers, and inconsistencies)
- Analyse pricing by neighbourhood, room type, borough, and host characteristics
- Visualise geographic distribution of listings and pricing hotspots
- Present findings through an interactive **Tableau dashboard**

---

## 📂 Dataset

| File | Description |
|---|---|
| `AB_NYC_2019.csv` | Raw Airbnb NYC listings dataset (2019) |
| `AB_NYC_2019_Updated.csv` | Cleaned and preprocessed version used for analysis |

### Key Features:
- **Listing Info**: Name, host ID, host name, neighbourhood group (borough), neighbourhood
- **Location**: Latitude, longitude (enables geospatial mapping)
- **Room Type**: Entire home/apt, Private room, Shared room
- **Pricing**: Price per night, minimum nights, service fee
- **Activity**: Number of reviews, reviews per month, last review date
- **Availability**: Availability (days per year), calculated host listings count

---

## 🔬 Analysis Pipeline

```
AB_NYC_2019.csv (Raw)
        │
        ▼
Data Cleaning & Preprocessing
        │   ├── Handle null values (name, host name, reviews)
        │   ├── Remove extreme price outliers (e.g. $0 or >$10,000/night)
        │   ├── Parse and validate date columns
        │   └── Save → AB_NYC_2019_Updated.csv
        │
        ▼
Univariate Analysis
        │   ├── Price distribution (heavily right-skewed)
        │   ├── Room type frequency across NYC
        │   ├── Neighbourhood group (borough) listing counts
        │   └── Availability distribution
        │
        ▼
Bivariate Analysis
        │   ├── Price by room type
        │   ├── Price by neighbourhood group (Manhattan vs others)
        │   ├── Reviews per month vs price
        │   ├── Minimum nights policy patterns
        │   └── Host listing count vs price (multi-listing hosts)
        │
        ▼
Geospatial Analysis
        │   ├── Map of listings by lat/long coloured by price
        │   ├── Heatmap of listing density by borough
        │   └── Neighbourhood-level price hotspot identification
        │
        ▼
Tableau Dashboard
                ├── Interactive borough & neighbourhood price explorer
                ├── Room type breakdown by area
                ├── Availability heatmap
                └── Top hosts by listing count
```

---

## 💡 Key Insights

- **Manhattan dominates pricing**: Median prices in Manhattan are significantly higher than other boroughs, driven by central location and entire-home listings
- **Room type is the strongest price predictor**: Entire home/apt listings cost nearly 2x private rooms across all boroughs
- **Brooklyn is the volume leader**: Brooklyn has the highest number of listings — a competitive market with more mid-range pricing
- **Price distribution is heavily skewed**: Most listings cluster below $200/night, but extreme outliers (>$1,000) exist and require removal for meaningful analysis
- **Multi-listing hosts behave differently**: Hosts with 10+ listings price more competitively and maintain higher availability — suggesting professional property management
- **Reviews correlate inversely with price**: Budget listings tend to have more reviews, suggesting higher booking frequency at lower price points
- **Shared rooms are a tiny market segment**: Despite being the cheapest option, shared rooms represent a very small fraction of total listings

---

## 🛠️ Tech Stack

| Tool | Purpose |
|---|---|
| Python | Core programming language |
| Pandas | Data loading, cleaning, and manipulation |
| NumPy | Numerical operations |
| Matplotlib / Seaborn | Statistical visualisations and heatmaps |
| Tableau | Interactive geographic and business dashboard |
| Jupyter Notebook | Interactive analysis environment |

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
jupyter notebook "AIR BNB CASE STUDY.ipynb"
```

### View the Dashboard

Open `AIR BNB CASE STUDY.twb` in **Tableau Desktop** or upload to **Tableau Public** for the interactive dashboard experience.

---

## 📁 Project Structure

```
📦 Air-BNB-Case-Study
 ┣ 📓 AIR BNB CASE STUDY.ipynb          # Full EDA and analysis notebook
 ┣ 📊 AIR BNB CASE STUDY.twb            # Interactive Tableau dashboard
 ┣ 📄 AB_NYC_2019.csv                   # Raw dataset
 ┣ 📄 AB_NYC_2019_Updated.csv           # Cleaned dataset
 ┗ 📄 README.md                         # Project documentation
```

---

## 🔭 Future Scope

- Build a **price prediction model** using neighbourhood, room type, and availability as features
- Add **sentiment analysis** on listing reviews to correlate guest experience with pricing
- Expand to **multi-year NYC data** to track how Airbnb listings and prices changed post-COVID
- Deploy an interactive **Streamlit pricing estimator** for hosts to benchmark their listing price

---

## 👤 Author

**Praasuk Jain**
- GitHub: [@PJ2001-IND](https://github.com/PJ2001-IND)
- LinkedIn: [praasuk-jain](https://www.linkedin.com/in/praasuk-jain-425b6b1a3/)

---

## 📄 License

This project is licensed under the MIT License.

---

> ⭐ If you found this project useful, consider giving it a star!
