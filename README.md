# ✈️ Airline Route Profitability & Cost Analysis

A comprehensive Exploratory Data Analysis (EDA) and Feature Engineering project examining airline route performance, cost structure, fleet efficiency, and seasonal demand patterns — aimed at uncovering data-driven insights for strategic airline operations.

---

## 📌 Project Overview

This project analyzes a rich airline operations dataset to answer core business questions:

- Which routes are the most and least profitable?
- What cost components drive airline operating expenses?
- How do aircraft type and route category interact with profitability?
- How does demand and profitability shift across seasons?
- What do unit economics (CASK/RASK) reveal about network efficiency?

The technical foundation for data processing and initial visualizations is adapted from the work by *Emanuel Lázaro* on [Kaggle](https://www.kaggle.com/code/emanuellcs/airline-route-profitability-cost-analysis).

---

## 📁 Repository Structure

```
airline-route-profitability/
│
├── Airline_Route_Profitability_and_Cost_Analysis.ipynb   # Main analysis notebook
├── README.md                                              # Project documentation
└── requirements.txt                                       # Python dependencies (optional)
```

---

## 📊 Dataset

**Source**: [Kaggle — Airline Route Profitability and Cost Analysis](https://www.kaggle.com/datasets/waleedfaheem/airline-route-profitability-and-cost-analysis)

**File**: `airline_route_profitability.csv`

The dataset includes flight-level records with:
- Flight metadata: date, origin, destination, aircraft type, route category
- Passenger and capacity data: passengers, aircraft capacity, load factor
- Financial metrics: total revenue, total cost, profit, profit margin
- Cost breakdown across 14 components (fuel, crew, maintenance, catering, marketing, etc.)
- Operational data: flight hours, season labels

---

## 🔬 Analysis Sections

### 1. Data Quality Assessment
- Column types, missing value audit, duplicate detection
- Consistency checks: recomputed load factor, profit, and profit margin against provided values — all passed ✅

### 2. Feature Engineering
Seven new features were derived to enrich the analysis:

| Feature | Description |
|---|---|
| `Revenue_Per_Passenger` | Total revenue per passenger |
| `Cost_Per_Passenger` | Total cost per passenger |
| `Fuel_Percentage` | Fuel cost as % of total cost |
| `Is_Profitable` | Binary flag for profitable flights |
| `Estimated_Distance` | Proxy: flight hours × 850 km/h |
| `CASK` | Cost per Available Seat Kilometer |
| `RASK` | Revenue per Available Seat Kilometer |

### 3. Exploratory Data Analysis

**Fleet & Route Network**
- Aircraft type distribution and route category breakdown
- Top 15 destinations by flight volume

**Financial Metrics**
- Distribution analysis of revenue, cost, profit, profit margin, and load factor
- Median benchmarking across all key financial indicators

**Route Profitability**
- Top 15 and bottom 15 destinations ranked by average profit margin
- Monthly load factor trends for best and worst performing routes
- Notable finding: BKK achieves high profitability despite low load factor (pricing effect); BAH shows high load factor yet negative margins (cost or pricing problem)

**Aircraft & Segment Analysis**
- Profit margin boxplots by route category and aircraft type
- Heatmap: median profit margin by aircraft type × route category

**Load Factor vs. Profit Margin**
- Scatter plot with Pearson correlation coefficient
- Average load factor by destination, color-coded by route category

**Correlation Analysis**
- Full lower-triangle correlation heatmap across all numeric features
- Targeted bar chart: feature correlations with profit margin

**Cost Structure Decomposition**
- 14 cost components ranked as % of total cost
- Stacked bar chart: cost distribution by route category (Short / Medium / Long Haul)
- Deep-dive fuel analysis: fuel % by route category and aircraft type

**CASK & RASK Analysis**
- Scatter plot of CASK vs. RASK per destination with breakeven line
- RASK–CASK spread ranked by destination, color-coded by route category

**Seasonality Analysis**
- Monthly load factor and profit margin trends by route category
- Monthly total revenue bar chart
- Seasonal performance comparison (Peak / Shoulder / Normal / Low)
- Heatmap: profit margin by destination × season

---

## 💡 Key Findings

- **Long-haul routes** consistently outperform short and medium-haul on profit margins and unit economics (RASK–CASK spread).
- **Fuel cost** is the dominant cost driver across all segments, with its share rising on long-haul routes.
- **Load factor and profitability are positively correlated**, but pricing strategy can override this — BKK proves that low passenger fill rates don't preclude strong profitability.
- **BAH is a strategic outlier**: high load factor paired with poor profitability points to either elevated route-specific costs or systematic underpricing.
- **Seasonality materially compresses margins** — even top-performing destinations can slip into unprofitability during low season, reinforcing the need for dynamic pricing and capacity management.

---

## 🛠️ Technologies Used

- **Python 3**
- `pandas` — data manipulation and aggregation
- `numpy` — numerical operations
- `matplotlib` — custom visualizations
- `seaborn` — statistical plotting
- `kagglehub` — dataset loading from Kaggle

---

## 🚀 Getting Started

### Run in Google Colab
Click the badge to open the notebook directly:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1LPr6-4DQmYv5j8sbvmXc6c2RUsW8Oxdf)

### Run Locally

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/airline-route-profitability.git
   cd airline-route-profitability
   ```

2. Install dependencies:
   ```bash
   pip install pandas numpy matplotlib seaborn kagglehub
   ```

3. Set up Kaggle API credentials (required for `kagglehub`):
   - Go to [kaggle.com](https://www.kaggle.com) → Account → API → Create New Token
   - Place `kaggle.json` in `~/.kaggle/`

4. Launch the notebook:
   ```bash
   jupyter notebook Airline_Route_Profitability_and_Cost_Analysis.ipynb
   ```

---

## 🔮 Future Work

- **Predictive Modeling**: Train regression and classification models to forecast flight profitability using engineered features
- **Route Optimization**: Recommend route discontinuation or frequency changes based on CASK/RASK spread
- **Dynamic Pricing Analysis**: Model seasonal pricing elasticity to maximize yield on underperforming routes
- **Fleet Deployment Optimization**: Match aircraft type to route category using fuel efficiency and margin data

---

## 🙏 Acknowledgements

- Dataset by [Waleed Faheem](https://www.kaggle.com/waleedfaheem) on Kaggle
- Original analysis reference by [Emanuel Lázaro](https://www.kaggle.com/code/emanuellcs/airline-route-profitability-cost-analysis)

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
