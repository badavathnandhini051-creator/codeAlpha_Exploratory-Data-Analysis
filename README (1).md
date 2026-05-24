# 📊 Superstore Sales — Exploratory Data Analysis (EDA)

A complete, end-to-end EDA of the Superstore Sales dataset covering data structure exploration, trend identification, statistical hypothesis testing, and data quality auditing.

---

## 📁 Project Structure

```
superstore-eda/
├── Superstore_EDA.ipynb        # Main notebook
├── superstore.csv              # Dataset (1,000 orders × 12 columns)
├── requirements.txt            # Python dependencies
├── README.md                   # This file
└── eda_outputs/                # Generated charts & visualizations
    ├── 01_sales_profit_distribution.png
    ├── 02_category_performance.png
    ├── 03_subcategory_profit.png
    ├── 04_regional_performance.png
    ├── 05_monthly_sales_trend.png
    ├── 06_segment_analysis.png
    ├── 07_shipping_mode.png
    ├── 08_discount_vs_profit.png
    ├── 09_profit_by_region_anova.png
    ├── 10_profit_by_category_violin.png
    ├── 11_correlation_heatmap.png
    ├── 12_outlier_detection.png
    └── 13_loss_by_category.png
```

---

## 🎯 Business Questions Answered

| # | Question |
|---|----------|
| Q1 | Which **region** generates the highest sales and profit? |
| Q2 | Which **category/sub-category** is most and least profitable? |
| Q3 | Does a **higher discount** always lead to lower profit? |
| Q4 | Which **customer segment** contributes most to revenue? |
| Q5 | Is there a **seasonal trend** in sales across months/years? |
| Q6 | Which **states** are top performers vs underperformers? |
| Q7 | Does **shipping mode** affect profitability? |
| Q8 | Are there **outliers** in sales or profit that skew the data? |

---

## 📌 EDA Coverage (5 Core Points)

### Point 1 — Meaningful Questions
Defined 8 business-driven questions before touching the data, ensuring analysis stays goal-oriented.

### Point 2 — Data Structure Exploration
- Dataset: **1,000 rows × 12 columns**
- Columns: Order ID, Order Date, Ship Mode, Segment, State, Region, Category, Sub-Category, Sales, Quantity, Discount, Profit
- Feature engineering: Year, Month, Quarter extracted from Order Date
- 3 categories, 4 regions, 3 customer segments, 4 shipping modes

### Point 3 — Trends, Patterns & Anomalies
- Sales is heavily **right-skewed** — a few very large orders dominate
- **Technology** leads in total sales; some sub-categories consistently lose money
- **Q4 (Oct–Dec)** shows consistent seasonal sales spikes across all years
- **West and East** regions tend to outperform Central and South

### Point 4 — Hypothesis Testing
| Hypothesis | Test | Result |
|-----------|------|--------|
| Higher discount → lower profit | Pearson correlation + regression | ✅ Significant negative correlation |
| Region affects profit | One-way ANOVA | ✅ Significant difference across regions |
| Category affects profit | Kruskal-Wallis (non-parametric) | ✅ Significant difference across categories |

### Point 5 — Data Quality Issues
- ~1.5% missing values in Sales and Profit columns
- No duplicate rows detected
- Significant outliers in Sales and Profit (right-tail heavy)
- ~30% of orders are **loss-making**, primarily driven by high discounts (40–70%)

---

## 📊 Output Visualizations

| File | Description |
|------|-------------|
| `01_sales_profit_distribution.png` | Histogram distributions for Sales & Profit |
| `02_category_performance.png` | Total Sales & Profit by Category |
| `03_subcategory_profit.png` | Horizontal bar chart — profit by sub-category (red = loss) |
| `04_regional_performance.png` | Grouped bar — Sales & Profit by Region |
| `05_monthly_sales_trend.png` | Multi-year monthly sales line chart |
| `06_segment_analysis.png` | Customer segment sales & profit breakdown |
| `07_shipping_mode.png` | Avg Sales & Profit by Ship Mode |
| `08_discount_vs_profit.png` | Scatter plot with regression line (Discount vs Profit) |
| `09_profit_by_region_anova.png` | Box plot — Profit distribution by Region |
| `10_profit_by_category_violin.png` | Violin plot — Profit distribution by Category |
| `11_correlation_heatmap.png` | Correlation matrix heatmap |
| `12_outlier_detection.png` | IQR box plots for Sales, Profit, Quantity |
| `13_loss_by_category.png` | Total loss by category from negative-profit orders |

---

## 🚀 How to Run

### 1. Clone / download the project

```bash
git clone https://github.com/your-username/superstore-eda.git
cd superstore-eda
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Launch the notebook

```bash
jupyter notebook Superstore_EDA.ipynb
```

Or run as a script (outputs will be saved to `eda_outputs/`):

```bash
jupyter nbconvert --to script Superstore_EDA.ipynb
python Superstore_EDA.py
```

---

## 🛠️ Tech Stack

| Library | Purpose |
|---------|---------|
| `pandas` | Data loading, cleaning, aggregation |
| `numpy` | Numerical computation |
| `matplotlib` | Base plotting |
| `seaborn` | Statistical visualizations |
| `scipy` | Hypothesis testing (ANOVA, Kruskal-Wallis, Pearson) |
| `jupyter` | Interactive notebook environment |

---

## ✅ Key Findings Summary

| Area | Finding |
|------|---------|
| **Data Quality** | ~1.5% missing values; no duplicates; heavy outliers in Sales |
| **Profitability** | Some sub-categories (e.g., Tables, Bookcases) are net loss-makers |
| **Discount Effect** | Strong negative correlation — discounts above 30% often destroy margins |
| **Seasonality** | Consistent Q4 sales spike every year |
| **Region** | West & East outperform; South underperforms |
| **Segments** | Consumer drives volume; Corporate tends to have better margins |

---

## 📋 Recommended Next Steps

1. **Impute missing values** using median or model-based strategies
2. **Winsorize outliers** before building predictive models
3. **Review discount policy** — cap at 20% to protect margins
4. **Focus marketing** on high-profit regions, segments, and sub-categories
5. **Build predictive models** — profit regression, customer segmentation (clustering)
