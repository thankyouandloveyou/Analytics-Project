# Shopify Sales Analysis: Investigating a Major Sales Shift

## Project Overview

A product analytics case study investigating a significant and persistent shift in Shopify sales.

The goal was not simply to identify that sales increased, but to understand **when the change occurred, whether it was statistically meaningful, whether it persisted, which customer segment was associated with the change, and what additional analysis would be needed to identify the underlying business driver.**

This project demonstrates an end-to-end **Product Analytics workflow** using transaction-level sales data.

---

## Business Question

**Sales increased substantially during the year. What changed, when did it happen, which segment was associated with the increase, and what should we investigate next?**

From a Product Analytics perspective, the analysis follows:

> **Detect → Quantify → Segment → Investigate → Recommend**

---

## Dataset

The dataset contains approximately **204K sales transactions** from October 2012 through September 2013.

Available fields:

* `sale_time` — timestamp of each transaction
* `purchaser_gender` — purchaser gender

Because the dataset does not contain customer IDs or additional product/business variables, the analysis focuses on **daily sales behavior and purchaser-segment trends**.

---

# Product Analytics Approach

## 1. Establish the Sales Baseline

I aggregated transaction-level data into daily sales and visualized the time series to understand the overall sales trajectory and identify unusual changes.

**Product Analytics skills:**
`Data aggregation` · `Time-series analysis` · `Exploratory data analysis` · `Data visualization`

---

## 2. Detect the Sales Shift

Rather than selecting an arbitrary period for comparison, I calculated the **day-over-day change in sales** to identify the date associated with the largest increase.

**Detected change point: April 29, 2013**

This date was then used as the breakpoint for subsequent analysis.

**Product Analytics skills:**
`Change detection` · `Trend analysis` · `Metric monitoring`

---

## 3. Test Whether the Change Was Statistically Significant

I compared average daily sales before and after the detected change point using a **Welch's t-test**.

Results:

* t-statistic: **-45.94**
* p-value: **3.49 × 10⁻¹³⁸**

The results provide strong statistical evidence that average daily sales differed between the two periods.

**Product Analytics skills:**
`Hypothesis testing` · `Statistical inference` · `Significance testing`

---

## 4. Quantify the Business Impact

I calculated the change in average daily sales before and after April 29 to translate the statistical finding into a business metric.

This helps answer:

> **"How large was the change?"**

rather than simply:

> **"Was the change statistically significant?"**

**Product Analytics skills:**
`Metric definition` · `Business impact quantification` · `Effect interpretation`

---

## 5. Determine Whether the Increase Persisted

A single-day spike could represent an anomaly rather than a meaningful business change.

I therefore used a **7-day rolling average** to evaluate whether the higher sales level persisted after April 29.

The elevated sales level continued for multiple weeks, suggesting that the change was **persistent rather than a temporary one-day spike**.

**Product Analytics skills:**
`Trend analysis` · `Signal vs. noise` · `Metric monitoring`

---

## 6. Segment the Change by Purchaser Gender

I analyzed sales trends separately by purchaser gender to understand whether the overall sales increase was distributed across segments or concentrated in a particular group.

The analysis showed:

* Male sales increased substantially after the detected change point.
* Female sales declined overall, although the decline became less pronounced after April 29.
* The overall sales increase was therefore primarily associated with the male purchaser segment.

Average daily sales:

| Segment | Before Apr 29 | After Apr 29 |
| ------- | ------------: | -----------: |
| Female  |           326 |          279 |
| Male    |           178 |          422 |

This demonstrates the importance of **segment-level analysis**: the aggregate metric alone would not reveal where the change was concentrated.

**Product Analytics skills:**
`Segmentation` · `Cohort/segment analysis` · `Metric decomposition` · `Behavioral analysis`

---

## 7. Model the Change Using Interrupted Time Series

To better characterize the change around April 29, I used an **Interrupted Time-Series (ITS) regression estimated with OLS**.

The model separates:

* the underlying pre-change sales trend,
* the immediate level shift at the change point, and
* the change in slope after the intervention.

### Results

The model estimated an immediate increase of approximately:

**+194 daily sales**
95% CI: **177–211**
p < **0.001**

The estimated change in slope after April 29 was not statistically significant:

**p = 0.977**

This indicates that the sales shift was primarily an **immediate level increase**, rather than a statistically significant acceleration in the underlying sales trend.

The model explained approximately **85.8% of the variation in daily sales**.

**Product Analytics skills:**
`Time-series regression` · `Interrupted Time Series` · `Regression modeling` · `Trend decomposition` · `Statistical interpretation`

---

# Key Product Insights

### 1. Sales experienced a substantial structural shift

Daily sales moved to a significantly higher level around **April 29, 2013**, and the increase persisted beyond the initial change point.

### 2. The shift was primarily a level change

The ITS model estimates an immediate increase of approximately **194 sales per day**, while finding no statistically significant change in the underlying slope.

### 3. The aggregate increase was concentrated in one segment

Male purchaser sales increased substantially around the change point, while female sales declined.

This highlights why product metrics should be **decomposed by relevant user segments rather than analyzed only at the aggregate level**.

### 4. The analysis identifies a business question, not a causal conclusion

The data shows a strong association between the April 29 change point and the sales increase, but it does not identify what caused the shift.

---

# Business Recommendation / Next Investigation

The next Product Analytics question is:

> **What changed around April 29 that could explain the sustained increase in sales?**

With additional product and business data, I would investigate:

* Marketing campaigns
* Product launches
* Pricing changes
* Website or checkout changes
* Acquisition channels
* Changes in customer composition
* Other simultaneous product or business interventions

The male segment would be a particularly useful area for further investigation because its sales trajectory changed substantially around the same period.

If an intervention is identified, the appropriate **causal inference design** would depend on how the intervention was implemented.

For example:

* **Randomized rollout → A/B test**
* **Treated vs. untreated groups over time → Difference-in-Differences**
* **Known intervention date with longitudinal data → Interrupted Time Series**

The objective would be to move from:

> **"Sales changed around the launch."**

to:

> **"This intervention caused an estimated X incremental sales/conversions."**

---

# Limitations

This is an observational analysis and therefore does not establish that a specific business intervention caused the sales increase.

The dataset does not include:

* Customer identifiers
* Product information
* Pricing
* Marketing campaigns
* Acquisition channels
* Geography
* Website/product events

These limitations prevent direct identification of the underlying business driver.

The ITS analysis strengthens the characterization of the timing and magnitude of the shift, but **statistical significance should not be interpreted as proof of causality**.

---

# Product Analytics Skills Demonstrated

### Product & Business Analytics

* Business question framing
* Metric definition
* Metric decomposition
* Trend and change detection
* Segment analysis
* Business impact quantification
* Insight generation
* Translating analysis into product/business questions
* Identifying data gaps and next analytical steps

### Statistics & Experimentation

* Hypothesis testing
* Welch's t-test
* Statistical significance
* Confidence intervals
* Effect size interpretation
* Regression
* Interrupted Time-Series analysis
* Causal inference concepts

### Technical

* Python
* Pandas
* NumPy
* SciPy
* Statsmodels
* Matplotlib

---

# Project Takeaway

This project demonstrates an end-to-end Product Analytics workflow:

**Observe → Detect → Test → Quantify → Segment → Model → Investigate → Recommend**

Rather than stopping at **"sales increased,"** the analysis investigates **when the metric changed, how large the change was, whether it persisted, where the change was concentrated, and what additional data or causal design would be required to determine why it happened.**
