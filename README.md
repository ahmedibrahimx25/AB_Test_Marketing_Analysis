# A/B Test Analysis for a Digital Marketing Campaign

## Project Objective
This project provides a comprehensive analysis of an A/B test conducted on two digital marketing campaigns: a Control Campaign and a Test Campaign. The primary objective is to use statistical analysis to determine which campaign is more effective at converting users, thereby providing a data-driven recommendation for future marketing strategy.

## Dataset
The data is sourced from Kaggle and consists of two separate CSV files:
- `control_group.csv`: Performance data for the existing (control) ad creative.
- `test_group.csv`: Performance data for the new (test) ad creative.

Each record in the dataset represents the aggregated performance of a campaign for a single day. The key metrics include:
- **Spend**: The amount of money spent on the campaign that day.
- **Impressions**: The number of times the ad was shown.
- **Reach**: The number of unique users who saw the ad.
- **Website Clicks**: The number of clicks on the ad.
- **Purchases**: The number of conversions or sales.

## Methodology

### 1. Data Cleaning and Preparation
The raw data was first loaded and prepared for analysis. This involved several key steps:
- **Correct Loading**: Loaded the semicolon-delimited CSV files into pandas DataFrames.
- **Data Consolidation**: Merged the control and test group data into a single, unified DataFrame.
- **Standardization**: Cleaned and standardized column names for easier access (e.g., `"# of Purchase"` became `Purchase`).
- **Missing Value Handling**: Removed one row that contained missing values to ensure data integrity.
- **Type Conversion**: Converted all numerical columns to the appropriate data types for calculations.

### 2. Exploratory Data Analysis (EDA) & KPI Calculation
With clean data, I calculated the overall performance of each campaign by summing the daily metrics. The primary Key Performance Indicators (KPIs) chosen to evaluate the campaigns were:
- **Conversion Rate**: The primary success metric, calculated as `(Total Purchases / Total Reach) * 100`.
- **Cost Per Acquisition (CPA)**: The average cost to acquire one paying customer, calculated as `Total Spend / Total Purchases`.
- **Click-Through Rate (CTR)**: The percentage of impressions that resulted in a click, calculated as `(Total Website Clicks / Total Impressions) * 100`.

### 3. Hypothesis Testing
To ensure the observed differences in performance were not due to random chance, a formal hypothesis test was conducted on the primary metric, Conversion Rate.
- **Null Hypothesis (H₀)**: There is no significant difference in the conversion rate between the Test Campaign and the Control Campaign.
- **Alternative Hypothesis (H₁)**: The conversion rate of the Test Campaign is significantly *higher* than that of the Control Campaign.
- **Statistical Test**: A **two-proportion z-test** was used, as it is the appropriate method for comparing the proportions (rates) of two different groups.
- **Significance Level**: An alpha (α) of **0.05** was chosen.

## Key Findings

The analysis revealed a clear winner. The Test Campaign significantly outperformed the Control Campaign across key engagement and conversion metrics.

| KPI                 | Control Campaign | Test Campaign | Winner |
| ------------------- | ---------------- | ------------- | ------ |
| **Conversion Rate** | 0.59%            | **0.97%**     | Test   |
| **CTR**             | 4.86%            | **8.09%**     | Test   |
| **CPA**             | **$4.41**        | $4.92         | Control|

The p-value from the z-test was **p < 0.0001**, which is well below the significance level of 0.05. This allows us to confidently **reject the null hypothesis** and conclude that the Test Campaign's higher conversion rate is statistically significant.

## Final Business Recommendation

**The analysis strongly supports allocating future marketing budget to the Test Campaign strategy. The new creative is the clear winner, demonstrating a statistically significant and substantial improvement in user conversion.**

### Key Points:
- **Higher Effectiveness**: The Test Campaign increased the conversion rate by **64%** compared to the control group, proving it is far more effective at turning viewers into customers.
- **Higher Engagement**: The Click-Through Rate (CTR) saw a massive lift, indicating the new ad creative is significantly more engaging.

### Consideration:
- **Cost Per Acquisition (CPA)**: While highly effective, the Test Campaign's CPA is currently 11.5% higher than the Control's ($4.92 vs. $4.41). However, the dramatic 64% increase in conversion rate justifies this modest increase in cost per purchase.

### Action Plan:
1.  **Immediate Adoption**: Roll out the **Test Campaign creative** as the new standard for this marketing channel.
2.  **Future Optimization**: Task the marketing team with optimizing the spend and targeting of the new campaign to see if the CPA can be reduced over time, further increasing its overall profitability.

## How to Run This Project

1.  **Clone the repository:**
    ```bash
    git clone <your-repo-url>
    cd AB_Test_Marketing_Analysis
    ```
2.  **Install dependencies:**
    ```bash
    pip install -r requirements.txt
    ```
3.  **Place data:** Ensure `control_group.csv` and `test_group.csv` are inside the `data/` folder.

4.  **Execute the script:**
    

## Tools & Libraries Used
- **Python**
- **Pandas**: For data manipulation and cleaning.
- **Statsmodels**: For conducting the statistical z-test.
