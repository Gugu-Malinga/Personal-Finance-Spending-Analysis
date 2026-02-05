## 📌 Personal Finance Spending Analysis (Python, Pandas, Matplotlib)
- This project analyzes a real-world personal finance transactions dataset to uncover spending patterns, identify seasonal spikes, and understand which spending categories contribute most to monthly expenses. The project uses Python to perform data cleaning, feature engineering, time-series analysis, spending group consolidation, and year-over-year comparisons.

## 📌 Key Skills Demonstrated
- Data cleaning & preprocessing (Pandas)
- Feature engineering (custom spending groups, month extraction)
- Time-series analysis
- Aggregations & groupby operations
- Data visualization with Matplotlib
- Anomaly detection & trend interpretation
- YoY % change analysis
- Financial data storytelling & insight communication

## 📂 Dataset
This project uses the *Personal Finance* transactions dataset from Kaggle:

🔗 https://www.kaggle.com/datasets/bukolafatunde/personal-finance/data
- Date
- Description
- Category
- Transaction Type
- Amount
- Account Name

## 🔧 Project Workflow
**1. Data Loading & Cleaning**
- Converted Date column to datetime format
- Created a Month period column
- Standardized spending categories using a custom mapping dictionary
- Removed non-spending transactions:
   -  Income
   -  Credit Card Payments
**2. Monthly Spending Trends**
- Calculated total spending per month using:
   ``` python
     monthly_spending = (
     spending_df
     .groupby('Month')['Amount']
     .sum()
     .reset_index()
     )

- Insight:
Clear spending spikes occurred in:
   - May 2018
   - May 2019
   - June 2019 (highest overall)
**3. Category Breakdown of Spike Months**
- Analyzed the top spending categories driving each spike month:
   - May 2018
   - May 2019
   - June 2019
- Breakdown performed using:
   - ```python
     month_df.groupby('Spending_Group')['Amount'].sum()
- Insight:
   - The Shopping & Personal category consistently dominated these peak months, suggesting seasonal discretionary spending (e.g., summer prep, vacations, events, or large purchases).
**4. Multiple-Month Comparison**
- Created a comparison table of category totals for all spike months:
   - ```python
      comparison = pd.DataFrame({
     '2018-05': may_2018_breakdown,
     '2019-05': may_2019_breakdown,
     '2019-06': june_2019_breakdown
     }).fillna(0)
- Plotted the comparison using:
   - ```python
     comparison.T.plot(kind='bar')
**5. Year-over-Year Analysis**
- To understand spending behavior changes over time, two comparisons were calculated:
   - May 2018 → May 2019 YoY % Change
     ```python
        comparison['YoY May % Change'] = (
        (comparison['2019-05'] - comparison['2018-05'])
        / comparison['2018-05']
        ) * 100
   - May 2018 → June 2019 (Major Spike Shift)
     ```python
        comparison['2018-to-2019_June % Change'] = (
        (comparison['2019-06'] - comparison['2018-05'])
        / comparison['2018-05']
        ) * 100
- Insight:
   - Spending behavior shifted from a May peak in 2018 to an even higher June peak in 2019.
     This suggests a seasonal spending pattern that expanded or shifted later in the year.

## 📊 Visualizations Included
- Monthly spending line chart
- Category comparison bar chart (3 months)
- YoY % Change bar chart
- Spending group distribution views
**These visuals clearly highlight:**
- Seasonal trends
- Category-level spikes
- Drivers behind increases in spending

## 🧠 Key Findings
- Spending spikes occur consistently in late spring/early summer.
- The major spike shifted from **May (2018)** to **June (2019)**.
- **Shopping & Personal spending** is a major driver across spike months.
- Housing & Utilities remain stable, showing fixed-cost consistency.
- Food spending increases modestly during seasonal spikes.

## 🛠️ Tech Stack
- Python 3
- Pandas
- Matplotlib
- Kaggle Notebooks

## 💬 Future Improvements
- Add merchant-level clustering
- Group transaction descriptions using NLP
- Build a dashboard version in Streamlit
- Predict future spending using a simple ML model
