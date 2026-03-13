[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1BM2zjhrppD7yUs8Zt0h1XAtnuC8oDOcM?usp=sharing)

# Customer Sales Dashboard — Superstore Sales Analysis

Data analysis project built using Python in Google Colab. This project explores 4 years of retail sales data (2015–2018) from a global superstore to uncover business insights through data cleaning, analysis, and visualization.

---

## Key Findings

- **Technology** is the top-selling category at ~$830,000 in total sales
- **Sales grew consistently** year over year from 2015 to 2018
- **West region** leads with 31.4% of total sales; South (17.2%) is the biggest growth opportunity
- **Canon imageCLASS 2200 Copier** is the #1 best-selling product at ~$60,000
- Average monthly sales peaked at ~$120,000 in late 2018

---

## Dataset

- **Source:** [Superstore Sales Dataset by Rohit Sahoo](https://www.kaggle.com/datasets/rohitsahoo/sales-forecasting) — Kaggle
- **Size:** 9,800 rows × 18 columns
- **Period:** January 2015 – December 2018
- **Fields include:** Order Date, Ship Date, Customer Segment, Region, Category, Product Name, Sales, Profit, Quantity

---

## 🛠️ Tools & Libraries

| Tool | Purpose |
|------|---------|
| Python 3 | Core language |
| Pandas | Data loading, cleaning, analysis |
| NumPy | Numerical operations |
| Matplotlib | Chart creation |
| Seaborn | Styled visualizations |
| Google Colab | Cloud notebook environment |

---


## How to Run

**[Open directly in Google Colab](https://colab.research.google.com/drive/1BM2zjhrppD7yUs8Zt0h1XAtnuC8oDOcM?usp=sharing)**

Or run locally:
1. Open [Google Colab](https://colab.research.google.com)
2. Upload `Customer_Sales_Dashboard.ipynb`
3. Download the dataset from [Kaggle](https://www.kaggle.com/datasets/rohitsahoo/sales-forecasting)
4. Upload the CSV file to your Colab session
5. Run all cells: **Runtime → Run All**

---

## Charts Built

1. **Total Sales by Category** — Bar chart comparing Technology, Furniture, Office Supplies
2. **Monthly Sales Trend** — Line chart showing growth from 2015 to 2018
3. **Sales Distribution by Region** — Pie chart across West, East, Central, South
4. **Top 10 Best Selling Products** — Horizontal bar chart by total revenue

---

## Errors Faced & How They Were Fixed

### ValueError: Date Format Mismatch

**Error:**
```
ValueError: time data "15/04/2018" doesn't match format "%m/%d/%Y"
```

**Why it happened:**

Pandas assumed dates were in American format `MM/DD/YYYY`, but the Superstore dataset uses European format `DD/MM/YYYY`. So when it encountered `15/04/2018`, it tried to read `15` as a month — which doesn't exist — and crashed.

**Fix:**
```python
# Before (causes error)
df['Order Date'] = pd.to_datetime(df['Order Date'])

# After (fixed with dayfirst=True)
df['Order Date'] = pd.to_datetime(df['Order Date'], dayfirst=True)
df['Ship Date'] = pd.to_datetime(df['Ship Date'], dayfirst=True)
```

Adding `dayfirst=True` tells Pandas to read the first number as the **day** instead of the month, which matches the dataset's format correctly.

**Lesson learned:** Always check your date format before converting. Print a few raw values with `df['Order Date'].head()` first to see what format they're in.

---

## What I Learned

- How to load, explore and clean a real-world dataset using Pandas
- How to handle date parsing issues and format mismatches
- How to group and aggregate data to answer business questions
- How to build bar charts, line charts, pie charts and heatmaps
- How to structure and share a data analysis project professionally

---

## Future Improvements

- Add profit analysis — which category is most *profitable* vs just highest sales?
- Build an interactive dashboard using Plotly
- Add a machine learning model to forecast future sales
- Analyze shipping performance — which ship mode is fastest?

---