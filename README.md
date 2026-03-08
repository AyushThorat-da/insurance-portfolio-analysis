CAR INSURANCE POLICIES BUSINESS ANALYTICS.
1.Business Problem & Objective
Insurance companies operate on a delicate balance: collecting premiums upfront while 
preparing for unpredictable future claim liabilities. The primary objective of this 
dashboard is to provide executive stakeholders with a clear, interactive view of portfolio 
profitability, risk distribution, and seasonal claim trends. By monitoring the Loss Ratio
(the percentage of premiums paid out as claims), the business can make data-driven 
decisions on underwriting, pricing, and risk management.
2. Technical Approach & Data Modeling
To ensure accurate reporting, the raw data was structured using best practices in Power 
BI:
• Star Schema Implementation: The data model separates quantitative events 
(Fact Tables: Claims_Data and Policy_Sales_Data) from descriptive attributes 
(Dimension Tables).
• Centralized Time Intelligence: A dedicated Calendar table was implemented. 
This is a critical technique that allows the model to accurately filter and compare 
dates across both the Policy_Start_Date (sales) and the Claim_Date (liabilities) 
without creating circular dependencies.
• Granularity Handling: The dashboard successfully navigates different levels of 
data granularity, aggregating individual Claim_ID records up to monthly trends 
and linking them to broader policy tenures.
3. Core DAX Methodology
Instead of relying on basic drag-and-drop aggregations, explicit DAX (Data Analysis 
Expressions) measures were engineered to ensure business logic remains consistent 
across all visual filters:
• Total Premium = SUM(Policy_Sales_Data[Premium])
o Represents the Gross Written Premium (GWP)the total revenue booked 
(₹240.1M).
• Total Claim Cost = SUM(Claims_Data[Claim_Amount])
o Aggregates the absolute financial payout for the selected period.
• Loss Ratio = DIVIDE([Total Claim Cost], SUM(Policy_Sales_Data[Premium]))
o The most vital metric in the dashboard. A ratio > 1.0 means the company 
is losing money on underwriting.
• Frequency vs. Severity Analysis (Combo Chart):
o By plotting Total Claim Cost (Severity) against the Count of Claim_ID
(Frequency) on a dual-axis chart, the dashboard reveals whether high 
costs are driven by a few massive accidents or a high volume of minor 
fender-benders.
4. Real-World Business Assumptions (For the Company)
When analyzing insurance data, raw numbers don't tell the whole story. The following 
industry-standard assumptions were factored into the analysis:
• The "Earned" vs. "Written" Assumption: The dashboard distinguishes between 
₹240.1M Total Premium and ₹65.90M Earned Premium. The assumption is that the 
company cannot claim all ₹240.1M as profit today; it is only "earned" as the days of 
the policy expire. The remaining unearned premium must be held in reserve.
• Seasonal Environmental Risks: The Loss Ratio by Month chart shows high 
Chances assumed that spikes in late summer or early autumn (August–October) 
correlate with environmental factors. For example, heavy monsoon rains and 
localized flooding in coastal or metro regions frequently lead to surges in vehicle 
engine damage and total-loss claims.
• Inflation Risk on Long-Term Policies: The data shows 4-year policies have the 
highest loss ratio, while 1-3 year policies are the most profitable. The assumption 
here is that the cost of vehicle parts and labor inflates over 4 years, but the premium 
collected upfront remains fixed, gradually eroding profit margins on longer 
contracts.
5. Strategic Insights & Recommendations.
1. Re-evaluate Multi-Year Pricing: Since 4-year policies are underperforming, the 
actuarial team should consider increasing the baseline premium for long-term 
contracts or introducing depreciating coverage limits.
2. Resource Allocation for Peak Months: Claims processing teams should be 
scaled up during historically high-loss months (e.g., Q3) to handle the increased 
volume of Claim_IDs efficiently, ensuring high customer satisfaction.
3. Targeted Sales Strategies: Sales teams should be incentivized to push 1-year 
and 2-year policies, which the data proves are currently the most profitable 
segments of the portfolio.
