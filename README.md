Section 1 — Project Overview
"Built an end-to-end Banking Business Intelligence system simulating real banking operations in Nepal. The project covers data generation, ETL transformation using Power Query, star-schema data modeling, DAX measure development, and interactive dashboard creation in Power BI."
Section 2 — Data Model Diagram
 

DAX Measures
-- Total Transaction Amount
Total Amount = SUM(Transactions[Amount_NPR])

-- Transaction Count
Total Transactions = COUNT(Transactions[TransactionID])

-- Average Transaction Value
Avg Transaction = AVERAGE(Transactions[Amount_NPR])

-- Total Deposits Only
Total Deposits =
CALCULATE(SUM(Transactions[Amount_NPR]),
Transactions[TransactionType] = "Deposit")

-- Total Withdrawals Only
Total Withdrawals =
CALCULATE(SUM(Transactions[Amount_NPR]),
Transactions[TransactionType] = "Withdrawal")

-- Completed Transaction Rate (%)
Completion Rate =
DIVIDE(
CALCULATE(COUNT(Transactions[TransactionID]),
Transactions[Status] = "Completed"),
COUNT(Transactions[TransactionID])
) * 100

-- Total Loan Amount Disbursed
Total Loans = SUM(Loans[LoanAmount_NPR])

-- Active Loan Count
Active Loans =
CALCULATE(COUNT(Loans[LoanID]),
Loans[Status] = "Active")

-- Loan Default Rate (%)
Default Rate =
DIVIDE(
CALCULATE(COUNT(Loans[LoanID]),
Loans[Status] = "Defaulted"),
COUNT(Loans[LoanID])
) * 100

-- Total Customers
Total Customers = DISTINCTCOUNT(Transactions[CustomerID])

-- MoM Growth (Month-over-Month)
MoM Growth =
VAR CurrentMonth = [Total Amount]
VAR PrevMonth = CALCULATE([Total Amount],
DATEADD(Transactions[TransactionDate], -1, MONTH))
RETURN DIVIDE(CurrentMonth - PrevMonth, PrevMonth) * 100


Section 4 — Business Insights Found
4.1 Executive Summary 
•	Birgunj leads branch volume... 
•	Digital channels exceed 51%...
 4.2 Customer Analytics 
•	76.4% customers are Basic segment... 
•	Fixed Deposit adoption is lowest... 
4.3 Loan Portfolio 
•	Default rate at 10.75% — above safe threshold...
•	Business loans dominate at NPR 200M+... 
4.4 Branch Performance 
•	92.13% completion rate — 3% below target... 
•	Branch maturity correlates with volume...

screenshot
<img width="1132" height="678" alt="Screenshot 2026-04-21 202443" src="https://github.com/user-attachments/assets/49a8517a-a48a-4031-808a-c45e7c537646" />
<img width="1097" height="642" alt="Screenshot 2026-04-21 202533" src="https://github.com/user-attachments/assets/28293d2e-65a2-4dd1-84b9-b536f292f9a1" />
<img width="1087" height="674" alt="Screenshot 2026-04-21 202634" src="https://github.com/user-attachments/assets/274aed48-3007-4aac-be91-21fd5f961f09" />
<img width="1101" height="634" alt="Screenshot 2026-04-21 202705" src="https://github.com/user-attachments/assets/e5c7cf3d-8d00-49eb-b1b3-4f097f1c0686" />



