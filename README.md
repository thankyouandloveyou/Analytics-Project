# Shopify Sales Analysis

## Project Overview

This project analyzes Shopify sales data to identify sales trends, patterns, and significant changes in purchasing behavior over time.

The analysis combines **exploratory data analysis, time-series analysis, statistical testing, and data visualization** to uncover meaningful changes in daily sales performance.

## Business Questions

* Identify the driver(s) behind the sales increase, so the business can determine whether the underlying strategy can be replicated or scaled.

## Dataset

The dataset contains Shopify purchase-level transaction data, including:

* Sale time
* Purchaser gender
* Other transaction-level attributes

Each row represents an individual purchase.

## Tools & Technologies

* **Python**
* **Pandas** — data cleaning and analysis
* **SciPy** — statistical testing
* **Matplotlib** — data visualization
* **Jupyter Notebook / Anaconda**

## Analysis

### 1. Data Preparation

* Converted transaction timestamps to datetime format
* Extracted the sale date from transaction timestamps
* Aggregated transaction-level data into daily sales
* Grouped sales by purchaser gender for trend analysis

### 2. Exploratory Data Analysis

The initial EDA examined:

* Dataset structure and dimensions
* Missing values
* Duplicate records
* Descriptive statistics
* Daily sales distributions
* Sales trends over time
* Purchasing trends by gender

### 3. Time-Series Analysis

Daily sales were analyzed as a time series to identify:

* Overall sales trends
* Peaks and declines
* Unusual fluctuations
* Potential changes in sales behavior over time

### 4. Statistical Analysis

Statistical tests were used to determine whether observed changes in sales represented statistically significant differences rather than normal variation.

### 5. Visualization

Key findings were visualized using time-series plots and comparative sales charts.

## Key Findings

> Add your actual findings here after completing the analysis.

* **Finding 1:** 
* **Finding 2:** 
* **Finding 3:** 
* **Finding 4:** 

## Visualizations

### Daily Sales Over Time

![Daily Sales](images/daily_sales.png)

### Daily Sales by Gender

![Daily Sales by Gender](images/daily_sales_by_gender.png)

## Conclusion

The analysis identified key patterns and changes in Shopify sales performance over time. Time-series analysis and statistical testing were used to distinguish meaningful changes from normal fluctuations.

The results provide insights into sales trends and customer purchasing behavior that could support further investigation into the underlying business drivers.

## Project Structure

```text
Shopify-Sales-Analysis/
│
├── data/
│   └── shopify_sales.csv
│
├── images/
│   ├── daily_sales.png
│   └── daily_sales_by_gender.png
│
├── Shopify_Analysis.ipynb
│
└── README.md
```

## Skills Demonstrated

**Python · Pandas · SciPy · Matplotlib · Exploratory Data Analysis · Time-Series Analysis · Statistical Testing · Data Visualization · Business Analysis**
