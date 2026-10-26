# Vodafone Egypt Customers & Product Analysis

A one-page Power BI dashboard in Vodafone's colours. It tracks revenue, ARPU, app logins, data usage and subscribers for 2023 to 2025 and compares each year with the year before. I wrote each chart title as the question it answers.

**Note:** the data is simulated. I generated it in Python for this project, so it is not real Vodafone data, and the trends come from the rules I set in the generator.

![Customers & Product Analysis dashboard](screenshots/dashboard.png)

## Questions the dashboard answers

- Which customer class brings the most revenue?
- How many subscribers are still active?
- Which class uses the most data?
- Are customers paying more often?
- Do bigger plans bring more revenue?
- Do ARPU and app use grow together?

The cards at the top show how each KPI changed compared with the previous year. You pick the year with the 2023 / 2024 / 2025 buttons.

| KPI | 2025 | vs 2024 |
|---|---|---|
| Revenue | EGP 22.3M | +20.8% |
| ARPU (per subscriber per month) | EGP 340 | +9.4% |
| App logins (Ana Vodafone app) | 640.7K | +22.3% |
| Data used | 1.23M GB | +16.6% |
| Subscribers | 5,781 | +9.9% |

## What I found (2025 vs 2024)

- Revenue grew 20.8% to EGP 22.3M, from more subscribers (+9.9%) and higher ARPU (EGP 310 to 340).
- Customers pay more often. The average gap between payments went down from 29.6 to 27.8 days.
- 97.7% of subscribers are still active (5,647 active, 134 suspended).
- A+ customers bring the most revenue (EGP 4.6M) and use the most data, 52.7 GB a month. That's about 10 times class D.
- Large plans bring the most revenue, but customers on small plans use 104% of their quota, compared with 70% on large plans. They are good candidates for an upgrade.
- ARPU and app use went up together. Logins per subscriber per month went from 8.9 to 10.4.

## Data

One Excel file with 5 tables, January 2022 to December 2025. I only included 2022 so that 2023 has a year to compare with. All amounts are in EGP.

| Table | Rows | One row is |
|---|---|---|
| Fact_Monthly | 228,621 | one customer in one month |
| Fact_Payments | 231,401 | one payment |
| Dim_Customer | 6,000 | one customer |
| Dim_Plan | 8 | one plan (Flex 50 to 300 prepaid, RED 400 to 1000 postpaid) |
| Dim_Date | 1,461 | one day |

Before loading it, I checked the data with a Python script: no nulls or duplicates, all keys match, and revenue always equals plan fee plus extra charges. I checked the totals again in Power BI.

## Data model

A star schema with two fact tables (Fact_Monthly and Fact_Payments) and three dimensions (Dim_Customer, Dim_Plan, Dim_Date). A separate Years table drives the year buttons. All 48 measures are in one _Measures table.

## Tools

- Power BI: Power Query, data modeling and DAX (current year vs previous year, ARPU, quota use, colour measures for green/red), with a custom theme and background
- Python (pandas, NumPy) to generate and check the data

## Files

- `Vodafone_Dashboard.pbix` is the Power BI file
- `data/Vodafone_Simulated_Data_2022_2025.xlsx` is the data
- `screenshots/` has the dashboard image

To refresh the data, change the Excel file path in Power Query to where you saved it.

## Contact

Mohamed Yasser Kamal, [mohamedyasser6044@gmail.com](mailto:mohamedyasser6044@gmail.com)
