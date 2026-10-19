# Banking Customer Churn Analytics | Power BI Dashboard

An interactive four-page Power BI report that analyses customer churn for a retail bank. It shows how many customers are leaving, who they are, and which segments carry the highest churn risk, so retention teams can focus on the right customers.

> **Headline result:** 2,038 of 10,000 customers churned, a **20.38% churn rate** and a 79.62% retention rate.

---

## Table of contents

1. [Business problem](#business-problem)
2. [Dashboard pages](#dashboard-pages)
3. [Key insights](#key-insights)
4. [Recommendations](#recommendations)
5. [KPIs and DAX measures](#kpis-and-dax-measures)
6. [Dataset](#dataset)
7. [Tech stack](#tech-stack)
8. [How to use](#how-to-use)
9. [Project structure](#project-structure)
10. [Future improvements](#future-improvements)
11. [Author](#author)

---

## Business problem

Acquiring a new customer costs far more than keeping an existing one. This project answers questions a retention team would ask:

- What is the overall churn rate, and how has it split across the customer base?
- Which countries, age groups, genders and card types lose the most customers?
- Do activity status, satisfaction score or complaints relate to churn?
- Which customer segments should be prioritised for retention campaigns?

---

## Dashboard pages

### 1. Executive Overview
High-level view of the customer base and churn.

![Executive Overview]()

- KPI cards: Total Customers (10K), Churned Customers (2K), Churn Rate (20.38%), Average Balance (76.49K), Average Credit Score (650.53)
- Customers by Country, Active vs Inactive Members, Customers by Gender
- Churn by Age Group

### 2. Customer Analytics
Profile of the whole customer base.

![Customer Analytics](images/02_customer_analytics.png)

- Customers by Credit Score Category
- Churned Customers by Tenure (treemap)
- Customer Age Distribution
- Customers by Number of Products
- Balance vs Estimated Salary (retained vs churned)

### 3. Churn Analysis
Deep dive into the 2,038 churned customers.

![Churn Analysis](images/03_churn_analysis.png)

- KPI cards: Total Customers, Churn Rate, Retention Rate (79.62%), Churned Customers
- Churned Customers by Card Type, Complaint Status, Satisfaction Score, Gender and Activity Status

### 4. Customer Segmentation
Customer segments and what drives churn inside them.

![Customer Segmentation](images/04_customer_segmentation.png)

- Total Customers by Customer Segment (Active, Standard, High Value Active, High Balance Inactive)
- Churned Customers by Customer Segment
- Retained vs Churned customers
- Decomposition tree: Geography → Gender → Age Group → Activity Status

---

## Key insights

| # | Insight | Evidence |
|---|---------|----------|
| 1 | **Overall churn is 20.38%** | 2,038 churned customers out of 10,000 |
| 2 | **Germany churns at a much higher rate than France or Spain** | Germany has 814 churned customers from roughly 2.5K customers, while France has 811 from roughly 5K. This is about double the rate (approximate, from rounded counts) |
| 3 | **Customers aged 40-49 churn the most** | 807 churned customers, about 40% of all churn |
| 4 | **Inactive members drive most churn** | 1,303 of 2,038 churned customers (about 64%) were inactive |
| 5 | **Female customers churn more than their share of the base** | Females are 45.43% of customers but 55.89% of churned customers |
| 6 | **High Balance Inactive is the largest churn pool** | 772 churned customers, the highest of the four segments |
| 7 | **Satisfaction score alone does not explain churn** | Churned customers are spread almost evenly across scores 1 to 5 (387 to 439 each) |
| 8 | **Card type shows only small differences** | Diamond 546, Platinum 508, Silver 502, Gold 482 |
| 9 | **Complaints are almost universal among churned customers** | 99.8% of churned customers had a complaint. This is a very strong signal, but it should be validated before use in a predictive model |

---

## Recommendations

1. **Target Germany** with a dedicated retention review (pricing, service quality, local competition).
2. **Re-engage inactive members**, especially the *High Balance Inactive* segment, using personalised offers or relationship-manager outreach.
3. **Build age-specific retention offers** for the 40-49 group, the largest churn group.
4. **Fix the complaint process.** Faster resolution and follow-up could reduce churn.
5. **Use segment-based campaigns** rather than one-size-fits-all offers.

---

## KPIs and DAX measures

Example measures used in the report. Table and column names may differ in your model, so adjust them.

```DAX
Total Customers = DISTINCTCOUNT ( Customers[CustomerId] )

Churned Customers =
CALCULATE ( [Total Customers], Customers[Exited] = 1 )

Churn Rate % = DIVIDE ( [Churned Customers], [Total Customers] )

Retention Rate % = 1 - [Churn Rate %]

Average Balance = AVERAGE ( Customers[Balance] )

Average Credit Score = AVERAGE ( Customers[CreditScore] )
```

---

## Dataset

- **Source:** *add a link to the dataset here (for example Kaggle)*
- **Size:** 10,000 customer records
- **Fields used (examples):** CustomerId, Geography, Gender, Age, Tenure, Balance, EstimatedSalary, CreditScore, NumOfProducts, IsActiveMember, Complain, Satisfaction Score, Card Type, Exited
- **Derived fields:** Age Group, Credit Score Category, Customer Segment, Activity Status (Active / Inactive)

---

## Tech stack

- **Power BI Desktop** for report design and visuals
- **Power Query** for data cleaning and transformation
- **DAX** for measures and calculated columns
- Custom theme and background design for a consistent, professional look

---

## How to use

1. Download or clone this repository:
   ```bash
   git clone https://github.com/<your-username>/<your-repo-name>.git
   ```
2. Open `"C:\Users\DELL\Downloads\Customer-Churn-Records.csv"` in **Power BI Desktop** (latest version recommended).
3. If prompted, update the data source path under **Home → Transform data → Data source settings**.
4. Click **Refresh** and use the page tabs at the bottom to move between the four pages.

---


## Future improvements

- Add slicers for Geography, Gender and Age Group on every page
- Build a churn prediction model (for example logistic regression or random forest) and bring the scores into Power BI
- Add a time dimension to track churn trend month by month
- Publish to Power BI Service with scheduled refresh

---

## Author

**Your Name**
- LinkedIn: [your-profile](https://www.linkedin.com/in/your-profile)
- GitHub: [@your-username](https://github.com/your-username)
- Email: kashish19v@gmail.com

If you found this project useful, please give it a ⭐ on GitHub.
