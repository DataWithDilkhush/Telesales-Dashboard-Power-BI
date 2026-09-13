# Telesales-Dashboard-Power-BI
📞 Telesales Performance Dashboard — Power BI
---
🖼️ Dashboard Preview
![Telesales Performance Dashboard](C:\Users\Dilkhush\OneDrive\Desktop\Dilkhush\Project\Telesale Power bi Dashboard)
> \*A dark-themed, orange-accented single-page Power BI dashboard — featuring KPI cards, city-wise donut chart, monthly trend line, top agent rankings, call log table, and outcome analysis.\*
---
📌 Project Overview
The Telesales Performance Dashboard is a fully interactive Power BI report designed to monitor and analyze the complete telesales operations of a financial services company selling products like Home Loans, Credit Cards, Insurance, Mutual Funds, Personal Loans, and Demat Accounts.
This dashboard helps sales managers, team leads, and business analysts to:
💰 Track total revenue across teams, agents, cities, and products
🏆 Identify top-performing agents and compare team performance
📍 Analyze city-wise sales split across 10 major Indian cities
📊 Monitor call outcomes — Follow Up, Sale Done, Rejected, No Answer
📈 Spot monthly sales trends and seasonal patterns over 2 years
---
🛠️ Tech Stack
Tool	Purpose
Power BI Desktop	Dashboard design and visualization
Power Query (M)	Data cleaning and transformation
DAX	KPI measures, conversion rate, dynamic calculations
Microsoft Excel	Raw data source (.xlsx)
Data Modeling	Star schema — fact table + date/agent/product dimensions
---
📂 Data Source
> 🔗 \*\*Dataset sourced from \[Kaggle](https://www.kaggle.com/datasets)\*\* — publicly available telesales / financial services call data, modified and enriched for this project.
Property	Detail
Source	Kaggle (Public Dataset)
File	`Telesales\_Dataset.xlsx`
Total Records	2,000 call logs
Time Period	January 2023 – December 2024
Sheets	Telesales Data, Summary
📋 Dataset Columns
Column	Description
Call ID	Unique identifier for each call
Call Date	Date the call was made
Call Time	Time of call
Month / Quarter / Year	Time intelligence dimensions
Agent Name	Sales agent's name (12 agents)
Team	Team A / B / C / D
Product	Financial product pitched
Lead Source	Referral, Walk-in, Outbound, Website, Inbound
Customer Segment	Salaried, Student, Business Owner, Retired, Self Employed
City	10 Indian cities
Call Duration (Mins)	Length of the call
Call Status	Connected / Not Connected / Busy / Switched Off
Outcome	Sale Done / Follow Up / Rejected / No Answer / Callback
Sale Done	Yes / No
Sale Amount INR	Revenue generated
Agent Experience Years	Agent's years of experience
---
📊 Features & Dashboard Walkthrough
💼 Business Problem
Financial services telesales teams make hundreds of calls daily — but without a centralized dashboard, managers struggle to answer:
Which agent or team is performing best this month?
Which product is generating maximum revenue?
Which cities have untapped sales potential?
How many calls are being converted vs rejected?
Raw Excel data alone cannot answer these questions quickly.
---
🎯 Goal of the Dashboard
To build a single-page, dark-themed interactive dashboard that gives sales managers a complete 360° view of telesales operations — from team-level revenue down to individual call logs — with one-click product filtering.
---
🔍 Walkthrough of Key Visuals
1. 💰 KPI Card — Total Sales (Top Left)
Total Sales: ₹144.55M displayed as the hero metric
Sparkline trend showing monthly movement
Team-wise bar breakdown:
🥇 Team D — ₹45M
🥈 Team A — ₹38M
🥉 Team B — ₹33M
Team C — ₹29M
2. 🍩 City-wise Sales — Donut Chart (Top Center)
Visual percentage split of revenue across 10 cities:
City	Revenue Share
🔶 Lucknow	20.33%
🔶 Hyderabad	17.78%
🔶 Ahmedabad	14.95%
🔶 Jaipur	12.48%
🔶 Mumbai	9.42%
Others	25.04%
3. 📈 Monthly Sales Trend — Line Chart (Middle)
12-month trend line (Jan to Dec)
Peak Month 6: ₹10.7M
Lowest Month 12: ₹0.1M
Helps identify seasonal dips and growth patterns
4. 🏅 Call Agent Rankings — Horizontal Bar Chart (Right)
Top agents ranked by total revenue:
Rank	Agent	Revenue
🥇 1	Neha Joshi	₹17.4M
🥈 2	Rahul Sharma	₹15.8M
🥉 3	Suresh Nair	₹15.1M
4	Anjali Tiwari	₹14.9M
5	Kavita Rao	₹14.9M
5. 📋 Call Log Table (Bottom Left)
Detailed individual call records showing:
`Call Date | Call ID | Agent Name | Team | Call Status | Customer Segment | Lead Source | Sale Done | Amount`
Managers can drill down to any individual call.
6. 📊 Call Outcome Analysis — Bar Chart (Bottom Right)
Outcome	Count
Follow Up	5.0K
Sale Done	3.9K
Rejected	3.5K
No Answer	1.9K
Callback Requested	1.4K
Not Interested	0.8K
7. 🔘 Product Filter Tabs — Top Navigation
Interactive one-click buttons to filter the entire dashboard by product:
`Credit Card` | `Demat Account` | `Home Loan` | `Insurance` | `Mutual Fund` | `Personal Loan`
---
📐 DAX Measures Used
```dax
-- Total Sales Revenue
Total Sales = SUM(Telesales\_Data\[Sale Amount INR])

-- Overall Conversion Rate
Conversion Rate =
DIVIDE(
    COUNTROWS(FILTER(Telesales\_Data, Telesales\_Data\[Sale Done] = "Yes")),
    COUNTROWS(Telesales\_Data),
    0
)

-- Call Connection Rate
Connected Rate =
DIVIDE(
    COUNTROWS(FILTER(Telesales\_Data, Telesales\_Data\[Call Status] = "Connected")),
    COUNTROWS(Telesales\_Data),
    0
)

-- Average Call Duration
Avg Call Duration = AVERAGE(Telesales\_Data\[Call Duration Mins])

-- YoY Growth
YoY Growth =
DIVIDE(
    \[Total Sales] - CALCULATE(\[Total Sales], SAMEPERIODLASTYEAR(Calendar\[Date])),
    CALCULATE(\[Total Sales], SAMEPERIODLASTYEAR(Calendar\[Date])),
    0
)
```
---
📈 Key Business Insights
📌 Metric	📊 Value
💰 Total Revenue	₹144.55M
📞 Total Calls Made	2,000
✅ Successful Sales	304
🎯 Conversion Rate	15.2%
⏱️ Avg Call Duration	8.32 minutes
📅 Data Period	Jan 2023 – Dec 2024
🏙️ Cities Covered	10 Indian cities
👥 Total Agents	12
🏆 Top Team	Team D (₹44.9M)
🥇 Top Agent	Neha Joshi (₹17.4M)
📦 Top Product	Home Loan (₹124.2M — 86% of total!)
📍 Top City	Lucknow (₹29.4M)
📈 2024 vs 2023	2024 higher: ₹78.6M vs ₹65.9M
---
❓ Frequently Asked Questions
Q1. Where did you get this dataset?
> The dataset was sourced from \*\*Kaggle\*\* — a public data science platform. The raw data was then cleaned, enriched with additional columns (Lead Source, Agent Experience, Callback Date), and structured into a star-schema model for Power BI.
Q2. Why did you choose telesales as your project topic?
> Telesales dashboards are widely used in Indian financial services companies (banks, NBFCs, insurance firms). This project mirrors a real-world business scenario — making it relevant for recruiters and hiring managers in the BFSI sector.
Q3. What was the biggest challenge in building this dashboard?
> Designing the \*\*dark-themed UI\*\* with proper contrast and color hierarchy was the trickiest part. The orange-on-dark-blue color scheme required careful balancing so every visual remained readable while looking visually impactful.
Q4. How is Conversion Rate calculated?
> Conversion Rate = (Total calls where Sale Done = "Yes") ÷ (Total Calls) × 100
> In this dataset: 304 ÷ 2000 = \*\*15.2%\*\*
Q5. Which product generates the most revenue and why?
> \*\*Home Loan\*\* dominates at ₹124.2M — 86% of total revenue. This is because Home Loan amounts are significantly larger per deal (up to ₹49.7L per sale) compared to products like Credit Cards or Demat Accounts.
Q6. Can this dashboard be used for other industries?
> Yes! The same structure can be adapted for any telesales business — telecom, EdTech, insurance, real estate — by simply replacing the dataset and product names.
---
💡 Business Impact
Manager Efficiency — Identify underperforming agents in seconds without scrolling through spreadsheets
Coaching Decisions — Low conversion agents get targeted for training using call log drilldown
Product Strategy — Home Loan dominates; allocate more agents to maximize this revenue stream
City Targeting — Lucknow and Hyderabad lead; focus marketing budget on these cities
Lead Optimization — Compare Referral vs Outbound conversion to optimize lead acquisition cost
---
🚀 How to Use This Project
Step 1 — Clone or Download
```bash
git clone https://github.com/DataWithDilkhush/telesales-powerbi-dashboard.git
```
Or click Code → Download ZIP
Step 2 — Open Dataset
Open `dataset/Telesales\_Dataset.xlsx` → go to `Telesales Data` sheet
Step 3 — Open Power BI Dashboard
Install Power BI Desktop (Free)
Open `powerbi/Telesales\_Dashboard.pbix`
Click Refresh if prompted for data connection
Step 4 — Explore Interactively
Click product tabs at top to filter by product
Click any city in donut chart to filter all visuals
Click agent bar to see their individual performance
---
🎓 What I Learned
✅ Building a professional dark-themed Power BI dashboard
✅ Implementing button-style product slicers for top navigation
✅ Writing DAX measures — Conversion Rate, YoY Growth, Avg Duration
✅ Designing KPI cards with sparklines for trend visualization
✅ Sourcing and cleaning Kaggle datasets for real-world BI projects
✅ Applying star schema data modeling in Power BI
✅ Creating a detailed call log table for operational drill-down
---
🗂️ More Projects
Project	Tools	Status
Amazon Sales Dashboard	Power BI + SQL + Excel	🔄 In Progress
HR Analytics Dashboard	Power BI + Excel	📅 Coming Soon
SQL Sales EDA	SQL Server	📅 Coming Soon
Python Data Analysis	Python + Pandas	📅 Coming Soon

---

📬 Connect With Me
![LinkedIn](https://linkedin.com/in/dilkhush-godsay)
![GitHub](https://github.com/DataWithDilkhush)

---

🛡️ License
Licensed under the MIT License — free to use, modify, and share with proper credit.
---
⭐ Support This Project
Agar yeh project helpful laga toh Star ⭐ zaroor karo!
Aapka ek star mujhe aur behtar projects banane ke liye motivate karta hai! 🙏
---
Made with ❤️ by Dilkhush | Aspiring Data Analyst | Power BI · SQL · Excel · Python
