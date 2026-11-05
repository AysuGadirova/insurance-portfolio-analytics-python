# Insurance Portfolio Analytics --- Python
------------------------------------------------------------------------
Turning insurance data into actionable analytical
insights.

## Project Overview

This project explores an insurance portfolio using Python. It combines
customer, policy, claims, and payment records to assess portfolio
performance, examine claims activity, and identify policy-level risk
patterns.

The analysis follows a practical workflow: data quality checks, data
preparation, KPI calculations, exploratory analysis, risk assessment,
and an executive summary.

## Project Objectives

-   Assess the quality and consistency of the source datasets.
-   Combine customer, policy, claims, and payment information into one
    analytical dataset.
-   Calculate key insurance portfolio metrics.
-   Explore premium distribution and identify statistical outliers.
-   Examine claims frequency and severity across regions.
-   Review relationships between selected financial metrics.
-   Segment insurance policies into low-, medium-, and high-risk groups.

## Dataset Structure

The analysis uses four Excel worksheets:

  -----------------------------------------------------------------------
  Dataset                             Description
  ----------------------------------- -----------------------------------
  `customers`                         Customer information, including
                                      birth date, join date, and region

  `policies`                          Policy details, including insurance
                                      type, premium amount, status, and
                                      policy dates

  `claims`                            Claim records, claim amounts, and
                                      approved amounts

  `payments`                          Payment records and payment amounts
  -----------------------------------------------------------------------

**Note:** The source Excel workbook is not included in this repository.
The notebook expects an Excel file containing these four worksheets.
Update the file path in the data import cell to match your local
environment.

## Analysis Workflow

### 1. Data Import & Quality Checks

-   Imported the four worksheets with Pandas.
-   Converted relevant date columns to datetime format.
-   Checked duplicate rows, missing values, and data types.
-   Replaced missing broker names with `Not Broker` where applicable.
-   Filtered customer records where the join date precedes the birth
    date.
-   Flagged claims recorded after the policy end date for review; these
    records were retained.

### 2. Data Preparation

-   Aggregated claims by `policy_id` to calculate claim count, total
    claim amount, and approved claim amount.
-   Aggregated payments by `policy_id` to calculate payment count and
    total paid amount.
-   Merged policy, customer, claims, and payment information into a
    consolidated policy-level dataset.
-   Replaced missing values in the aggregated numeric claim and payment
    fields with zero.

### 3. Portfolio KPI Analysis

Calculated the following metrics:

-   Total insurance premium
-   Total claimed amount
-   Total approved claim amount
-   Claim ratio
-   Policy renewal rate

### 4. Premium Distribution & Outlier Analysis

-   Compared total premium amounts across insurance types.
-   Applied the Interquartile Range (IQR) method to identify unusually
    high or low premium values.
-   Used a boxplot to visualize premium distribution by insurance type.

### 5. High-Risk Policy Identification

Flagged policies as high risk when either of the following conditions
was met:

-   Loss ratio greater than 0.8
-   More than two claims recorded

### 6. Regional Risk Analysis

Compared regions using:

-   Claim frequency: total number of claims divided by the number of
    policies.
-   Average claim severity: total claim amount divided by the number of
    claims.

The results were visualized with bar charts.

### 7. Correlation Analysis

Examined correlations between:

-   Premium amount
-   Claim amount
-   Approved claim amount
-   Total payments

A correlation matrix and heatmap were used to explore relationships
between these numerical variables.

### 8. Policy Risk Segmentation

Classified policies into three risk groups using loss ratio and claim
count:

  Risk Level    Rule
  ------------- ---------------------------------------------------
  High Risk     Loss ratio \> 0.8 or claim count \> 2
  Medium Risk   Loss ratio \> 0.3 or at least one claim
  Low Risk      Does not meet the medium- or high-risk conditions

The distribution of policies across risk groups was visualized in a pie
chart.

### Executive Summary
- **Data Quality:** Duplicate records, missing values, and column data types were checked across all four tables. Date columns were converted to the datetime format, and logically inconsistent dates (e.g., enrollment dates preceding dates of birth) were filtered out.

- **Regional Risk:** Regional differences were identified in claim frequency and claim severity. Although some regions have a lower number of claims, the average amount of an individual claim (severity) is higher.

- **Risk Segmentation:** Customers with a Loss Ratio greater than 0.8 or more than 2 claims were consistently classified as "High Risk" during both the early detection and segmentation stages. This segment accounts for a significant portion of the company's overall claims portfolio.

- **Recommendations:** It is recommended to increase insurance premiums or apply stricter underwriting conditions to the high-risk customer segment


## Tools & Libraries

-   **Python** --- analysis workflow
-   **Pandas** --- data cleaning, aggregation, and merging
-   **NumPy** --- numerical operations
-   **Matplotlib** --- data visualization
-   **Seaborn** --- statistical charts and heatmaps
-   **Jupyter Notebook** --- interactive analysis environment

## Key Takeaways

The analysis provides a consolidated view of insurance portfolio metrics
and highlights differences in claim frequency and average claim severity
across regions. It also identifies policies that meet the defined
high-risk criteria and summarizes the portfolio's risk-group
distribution.

These findings can help guide further investigation of claims patterns,
regional exposure, and policy performance. The risk rules used in this
notebook are analytical screening criteria and should not be treated as
a formal underwriting model.

## Repository Structure

``` text
insurance-portfolio-analytics-python/
│
├── Insurance_Python_Assessment_Aysu_Qadirova.ipynb
├── README.md
└── data/
    └── (source Excel workbook — not included)
```

## How to Run

1.  Clone or download this repository.

2.  Install the required libraries:

    ``` bash
    pip install pandas numpy matplotlib seaborn openpyxl jupyter
    ```

3.  Place the source Excel workbook in your preferred local folder.

4.  Update the Excel file path in the notebook's data import cell.

5.  Open and run the notebook:

    ``` bash
    jupyter notebook Insurance_Python_Assessment_Aysu_Qadirova.ipynb
    ```

## Author

**Aysu Qadirova**\
Aspiring Data Analyst

[LinkedIn](https://www.linkedin.com/in/aysu-qadirova-08951b220)

------------------------------------------------------------------------
