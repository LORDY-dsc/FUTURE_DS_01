# Superstore Sales Analysis

Exploratory data analysis of Superstore sales data in R — uncovering revenue drivers, sales trends, and profitability gaps across categories and regions, with actionable recommendations for business growth.

## Overview

This project analyzes a 10,000-row retail sales dataset to answer four core business questions:

1. Which products generate the most revenue?
2. How do sales change over time?
3. Which categories or regions are most profitable?
4. Where should the business focus to grow faster?

The goal isn't just to produce charts — it's to turn raw transaction data into concrete, defensible business recommendations.

## Tech Stack

- **R**
- [`dplyr`](https://dplyr.tidyverse.org/) — data wrangling and aggregation
- [`ggplot2`](https://ggplot2.tidyverse.org/) — visualization
- [`scales`](https://scales.r-lib.org/) — axis formatting (currency, percentages)

## Setup

```r
install.packages(c("dplyr", "ggplot2", "scales"))

library(dplyr)
library(ggplot2)
library(scales)

superStore <- read.csv("data/superstore.csv", encoding = "latin1", stringsAsFactors = FALSE)
superStore$Order.Date <- as.Date(superStore$Order.Date, format = "%m/%d/%Y")
superStore$Ship.Date  <- as.Date(superStore$Ship.Date, format = "%m/%d/%Y")
```

## Data

The dataset is a classic "Superstore" retail sales export (~10,000 rows, 21 columns), including order details, customer info, product category/sub-category, sales, quantity, discount, and profit. Dates are stored as `MM/DD/YYYY` strings and were converted to `Date` type before analysis. Some character columns contained invalid UTF-8 encoding (e.g. accented customer names) and were re-imported using `latin1` encoding.

## Analysis & Findings

### 1. Which products generate the most revenue?

![Top Products by Revenue](images/top_products_revenue.png)

A single product — a Canon copier — generated roughly 3x the revenue of the next-best seller, indicating meaningful revenue concentration risk. The top 15 is dominated by big-ticket equipment (copiers, binding systems, printers) rather than everyday supplies, pointing toward account-based, business-to-business sales as a growth lever.

### 2. How do sales change over time?

![Monthly Revenue Trend](images/monthly_revenue_trend.png)

Monthly revenue roughly doubled over the period analyzed, with a clear upward trend. Volatility between months increased alongside growth, suggesting revenue is still driven by large, infrequent deals rather than steady repeat business. Recurring year-end spikes point to predictable seasonality that can be planned for.

### 3. Which categories or regions are most profitable?

![Profit by Category and Region](images/profit_by_category_region.png)

Furniture is barely profitable anywhere and turns negative in the Central region. Technology and Office Supplies consistently outperform on margin across all regions. West is the strongest-performing region overall; Central is the weakest.

### 4. Where should the business focus to grow faster?

![Discount vs Margin by Sub-Category](images/discount_vs_margin.png)

High discount rates are the main driver of Furniture's poor margins — Tables and Bookcases both carry heavy discounting and negative profit. Low-discount categories like Labels, Paper, and Envelopes quietly deliver 40%+ margins. Capping discounts on underperforming sub-categories, doubling down on Technology and Office Supplies in top-performing regions, and reducing reliance on a single hero product are the clearest paths to sustainable growth.

## Key Takeaway

The biggest revenue driver isn't always the biggest profit driver. Pairing revenue analysis with margin and discount data is what actually reveals where a business should focus to grow.

## License

MIT
