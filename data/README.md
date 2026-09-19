# Data

This project uses the **Shopify Sales Analysis** dataset from StrataScratch.

The raw dataset is not included in this repository. To reproduce the analysis, obtain the dataset from the original source and place the CSV files in:

```text
sales_data_analysis_datasets/
```

## Dataset Description

The dataset contains individual Shopify sales transactions from **October 2012 to September 2013**.

| Column             | Description                                      | Data Type   |
| ------------------ | ------------------------------------------------ | ----------- |
| `sale_time`        | Timestamp when the sale occurred                 | Datetime    |
| `purchaser_gender` | Gender of the purchaser associated with the sale | Categorical |

### Derived Variables

The analysis also creates several variables from the original data, including:

| Variable              | Description                                                                |
| --------------------- | -------------------------------------------------------------------------- |
| `sale_date`           | Calendar date extracted from `sale_time`                                   |
| `daily_sales`         | Number of sales transactions recorded each day                             |
| `prev_day_sales`      | Previous day's sales count                                                 |
| `sales_change`        | Day-over-day change in sales                                               |
| `rolling_7_day_sales` | 7-day rolling average of daily sales                                       |
| `post_change`         | Indicator for observations on or after April 29, 2013                      |
| `time`                | Time index centered on the detected change date                            |
| `time_after_change`   | Interaction term used to estimate a change in slope after the change point |

The original dataset contains approximately **204K transactions**.
