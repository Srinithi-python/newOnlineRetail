# Online Retail Dataset Analysis

## Overview
This repository contains an end-to-end Data Science project analyzing an Online Retail dataset using Python and Pandas. The project covers the full pipeline from raw data ingestion and cleaning to feature engineering, exploratory data analysis (EDA), data wrangling, and descriptive statistical summary.

## Executive Summary of Results
- **Dataset Size:** ~401,604 rows across 16 engineered features.
- **Total Revenue:** ~$8,935,447.60
- **Total Orders:** ~22,190 distinct invoices.
- **Top Generating Market:** United Kingdom (~$7,329,261 total revenue across ~19,857 orders).
- **Top Product by Revenue:** StockCode `23843` (~$168,469.60).

---

## Project Structure & Tasks

### Task 1 – Data Import & Setup
- Loaded the Online Retail dataset directly from a remote GitHub repository using Pandas (`pd.read_excel`).
- Displayed initial dataset metadata, including head, tail, array shape `(541909, 8)`, and column names.
- Converted `InvoiceDate` to standard `datetime64[ns]` format.

### Task 2 – Data Cleaning
- **Missing Values:** Handled missing customer identifiers by dropping records without a `CustomerID` (reduced to 406,829 rows).
- **Duplicates:** Identified and removed 5,225 duplicate transaction records.
- **Data Validation:**
  - Handled negative order quantities by clipping them or resetting invalid values.
  - Imputed non-positive unit prices using the global mean unit price for valid items.
  - Cleaned invalid `UnitPrice` records.

### Task 3 – Feature Engineering
- **Revenue Calculation:** Derived `TotalPrice` = `Quantity` × `UnitPrice`.
- **Temporal Features:** Extracted `Year`, `Month` (period format), `Day`, `Hour`, and `Day Type` (`Weekday` vs `Weekend`).
- **Customer & Order Segmentation:**
  - `Customer Segment`: Binned customers based on total spending into `Low Value` (<= $500), `Medium Value` ($500–$2000), and `High Value` (> $2000).
  - `Order Size`: Grouped items per transaction into `Small` (<= 10), `Medium` (11–50), and `Large` (> 50).

### Task 4 – Data Exploration (EDA)
- Analyzed overall distributions, unique counts, missingness, and data types.
- Evaluated key categorical distributions for `Country`, `CustomerID`, `InvoiceNo`, and `StockCode`.
- Aggregated metrics by country and monthly timeline to identify key commercial hubs and demand seasonality.

### Task 5 – Data Wrangling
- Aggregated metrics (Total Revenue, Total Orders, Total Quantity, Average Price) grouped by `Country`.
- Identified top revenue-generating customers across countries (e.g., CustomerID `14646` in Netherlands generating $282,207.28).
- Constructed monthly revenue pivot tables (`Country` vs. `Month`) to visualize international sales momentum over time.

### Task 6 – Statistical Analysis
Computed statistical measures (Mean, Median, Mode, Standard Deviation, Variance, and Interquartile Ranges) for key numerical attributes:

| Metric | Quantity | UnitPrice ($) | TotalPrice ($) |
| :--- | :--- | :--- | :--- |
| **Mean** | 12.86 | 3.47 | 22.25 |
| **Median** | 5.00 | 1.95 | 11.70 |
| **Mode** | 1 | 1.25 | 15.00 |
| **Std Dev** | 179.58 | 69.76 | 315.24 |
| **Min / Max** | 0 / 80,995 | 0.001 / 38,970 | 0.00 / 168,469.60 |

### Task 7 – Data Visualization
Implemented visual data analysis using `matplotlib.pyplot`:
1. **Monthly Revenue Trend Line Chart:** Plotted temporal sales movement throughout 2010–2011, highlighting peak holiday purchasing spikes around November.
2. Additional distributions across product performance, hourly purchase density, and order volume categories.

---

## Installation & Setup

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/your-username/online-retail-analysis.git
   cd online-retail-analysis
   ```

2. **Install Required Packages:**
   ```bash
   pip install pandas openpyxl matplotlib
   ```

3. **Run the Notebook / Script:**
   Launch Jupyter Notebook or Google Colab and run `Online_Retail_Analysis.ipynb`.

---

## Tech Stack
- **Language:** Python 3
- **Libraries:** Pandas, NumPy, Matplotlib
- **Environment:** Google Colab / Jupyter Notebook
