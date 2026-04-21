# 🏦 NepalBank Business Intelligence Dashboard

## 📌 Project Overview

Built an **end-to-end Banking Business Intelligence solution** simulating real banking operations in Nepal.  
This project demonstrates complete BI workflow including:

✅ Synthetic Banking Data Generation  
✅ ETL Transformation using Power Query  
✅ Star Schema Data Modeling  
✅ Advanced DAX Measure Creation  
✅ Interactive Dashboard Development in Power BI  
✅ Business Insight Extraction for Decision Making  

This dashboard helps management monitor transactions, customer behavior, loan performance, and branch efficiency.

---

# 🚀 Tech Stack

| Tool | Usage |
|------|-------|
| Power BI | Dashboard & Reporting |
| Power Query | ETL / Data Cleaning |
| DAX | KPI Measures |
| SQL | Data Preparation |
| Excel / CSV | Source Data |
| Star Schema | Data Modeling |

---

# 🧩 Data Model

The project uses a **Star Schema Model** for optimized analytics performance.

### Fact Tables:
- Transactions
- Loans

### Dimension Tables:
- Customers
- Branches
- Calendar

---

# 📊 Key DAX Measures

```DAX
-- Total Transaction Amount
Total Amount = SUM(Transactions[Amount_NPR])

-- Transaction Count
Total Transactions = COUNT(Transactions[TransactionID])

-- Average Transaction Value
Avg Transaction = AVERAGE(Transactions[Amount_NPR])

-- Total Deposits
Total Deposits =
CALCULATE(
    SUM(Transactions[Amount_NPR]),
    Transactions[TransactionType] = "Deposit"
)

-- Total Withdrawals
Total Withdrawals =
CALCULATE(
    SUM(Transactions[Amount_NPR]),
    Transactions[TransactionType] = "Withdrawal"
)

-- Completion Rate
Completion Rate =
DIVIDE(
    CALCULATE(
        COUNT(Transactions[TransactionID]),
        Transactions[Status] = "Completed"
    ),
    COUNT(Transactions[TransactionID])
) * 100

-- Total Loans
Total Loans = SUM(Loans[LoanAmount_NPR])

-- Active Loans
Active Loans =
CALCULATE(
    COUNT(Loans[LoanID]),
    Loans[Status] = "Active"
)

-- Default Rate
Default Rate =
DIVIDE(
    CALCULATE(
        COUNT(Loans[LoanID]),
        Loans[Status] = "Defaulted"
    ),
    COUNT(Loans[LoanID])
) * 100

-- Total Customers
Total Customers =
DISTINCTCOUNT(Transactions[CustomerID])

-- Month-over-Month Growth
MoM Growth =
VAR CurrentMonth = [Total Amount]
VAR PrevMonth =
    CALCULATE(
        [Total Amount],
        DATEADD(Transactions[TransactionDate], -1, MONTH)
    )
RETURN
DIVIDE(CurrentMonth - PrevMonth, PrevMonth) * 100
screenshot
<img width="1132" height="678" alt="Screenshot 2026-04-21 202443" src="https://github.com/user-attachments/assets/49a8517a-a48a-4031-808a-c45e7c537646" />
<img width="1097" height="642" alt="Screenshot 2026-04-21 202533" src="https://github.com/user-attachments/assets/28293d2e-65a2-4dd1-84b9-b536f292f9a1" />
<img width="1087" height="674" alt="Screenshot 2026-04-21 202634" src="https://github.com/user-attachments/assets/274aed48-3007-4aac-be91-21fd5f961f09" />
<img width="1101" height="634" alt="Screenshot 2026-04-21 202705" src="https://github.com/user-attachments/assets/e5c7cf3d-8d00-49eb-b1b3-4f097f1c0686" />



