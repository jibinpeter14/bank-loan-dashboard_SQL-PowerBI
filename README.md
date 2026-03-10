# Bank Loan Analysis (SQL + Power BI)
![SQL](https://img.shields.io/badge/SQL-Database-blue)
![Power BI](https://img.shields.io/badge/PowerBI-Visualization-yellow)
![Data Analytics](https://img.shields.io/badge/Data-Analytics-green)
This project analyzes bank loan performance using SQL and Power BI to identify lending patterns, borrower risk behavior, and loan portfolio performance.

## Project Overview
This project analyzes bank loan performance using SQL for data exploration and Power BI for interactive data visualization.

The goal of this analysis is to understand loan performance, identify risk patterns, and evaluate borrower repayment behavior.

The dashboard provides insights into loan applications, funded amounts, repayments, interest rates, and loan risk classification.

---
## Dashboard Preview

![Dashboard Overview](screenshot/dashboard_overview.png)
***Main Dashboard Overview***:
This dashboard displays high-level KPIs such as total loan applications, total funded amount, total amount received, average interest rate, and average debt-to-income ratio. It also includes breakdowns by state, loan term, home ownership, employment length, and loan purpose.

![Loan Summary](screenshot/loan_summary.png)
***Loan Performance Summary***:
This section highlights the distribution between Good Loans and Bad Loans, allowing analysts to quickly evaluate portfolio health and risk exposure.

![Loan Details](screenshot/loan_details_table.png)
***Loan Details Table***:
A detailed table showing individual loan records including loan purpose, home ownership status, loan grade, installment amount, total payment received, and loan status.

![Data Model](screenshot/data_model.png)
***Data Model***:
The Power BI data model showing relationships between the main loan dataset and the date table used for time-based analysis and filtering.

---
## SQL Analysis Examples

Below are some key SQL queries used to analyze the bank loan dataset.

---

### 1. Total Loan Applications

```sql
SELECT COUNT(id) AS Total_Loan_Applications
FROM Bank_loan_data;
```

This query calculates the total number of loan applications received.

---

### 2. Total Funded Loan Amount

```sql
SELECT SUM(loan_amount) AS Total_Funded_Amount
FROM Bank_loan_data;
```

This query calculates the total amount funded across all loans.

---

### 3. Good Loans vs Bad Loans

```sql
SELECT 
    CASE 
        WHEN loan_status = 'Fully Paid' OR loan_status = 'Current' THEN 'Good Loan'
        ELSE 'Bad Loan'
    END AS Loan_Category,
    COUNT(*) AS Total_Loans
FROM Bank_loan_data
GROUP BY Loan_Category;
```

This query classifies loans into Good Loans and Bad Loans using conditional logic.

---

### 4. Monthly Loan Applications Trend

```sql
SELECT 
    DATENAME(MONTH, issue_date) AS Month_Name,
    COUNT(id) AS Loan_Applications
FROM Bank_loan_data
GROUP BY DATENAME(MONTH, issue_date)
ORDER BY Loan_Applications DESC;
```

This query analyzes loan application trends by month.

---

### 5. Average Interest Rate by Loan Grade

```sql
SELECT 
    grade,
    ROUND(AVG(int_rate) * 100, 2) AS Avg_Interest_Rate
FROM Bank_loan_data
GROUP BY grade
ORDER BY Avg_Interest_Rate DESC;
```

This query calculates the average interest rate for each loan grade.

---

### 6. Top States by Loan Applications

```sql
SELECT 
    address_state,
    COUNT(id) AS Total_Loans
FROM Bank_loan_data
GROUP BY address_state
ORDER BY Total_Loans DESC;
```

This query identifies which states have the highest number of loan applications.

---

### 7. Loan Status Distribution

```sql
SELECT 
    loan_status,
    COUNT(*) AS Loan_Count
FROM Bank_loan_data
GROUP BY loan_status
ORDER BY Loan_Count DESC;
```

This query shows the distribution of loans across different loan statuses.

---

More SQL queries used in this project are available in the file:

**sql_queries.sql**

---

## Tools & Technologies

- SQL Server
- Power BI
- Power Query
- Data Modeling
- Data Visualization

---

## Dataset

The dataset contains detailed information about loan applications including:

- Loan ID
- Loan Amount
- Funded Amount
- Total Payment Received
- Loan Status
- Interest Rate
- Debt to Income Ratio
- Borrower State
- Employment Length
- Loan Purpose

---

## Key Business Questions

This project answers several important business questions:

1. How many loan applications were received?
2. What is the total funded loan amount?
3. What is the total repayment received from borrowers?
4. What percentage of loans are good loans vs bad loans?
5. What is the average interest rate charged to borrowers?
6. What is the average debt-to-income ratio of borrowers?

---

## SQL Analysis

SQL queries were used to analyze the dataset and calculate the main KPIs.

Example queries include:

- Total Loan Applications
- Total Funded Amount
- Total Amount Received
- Average Interest Rate
- Average Debt to Income Ratio
- Good Loans vs Bad Loans

The SQL queries used in this project are available in the file:

`sql_queries.sql`

---

## Power BI Dashboard

The Power BI dashboard provides an interactive view of the loan portfolio.

### Dashboard Features

- KPI Cards for key metrics
- Good Loans vs Bad Loans analysis
- Loan Status summary table
- Loan performance insights

---

## Key Metrics

| Metric | Value |
|------|------|
| Total Loan Applications | 38.6K |
| Total Funded Amount | $436M |
| Total Amount Received | $473M |
| Average Interest Rate | 12% |
| Average DTI | 13% |

---

## Project Files
Bank Loan Dashboard_Project.pbix → Power BI dashboard
Bank_Loan_data.csv → Dataset
sql_queries.sql → SQL analysis queries


---

## Business Insights

- The majority of loans are classified as **good loans (86%)**
- Only **14% of loans are bad loans**
- The average borrower interest rate is around **12%**
- Borrowers have an average **DTI ratio of approximately 13%**

These insights help financial institutions evaluate loan risk and portfolio performance.

---

## Author

**Jibin Peter**

Business Analyst | Data Analytics Enthusiast
