# banking-domain-data-analysis
Develop a basic understanding of risk analytics in banking and financial services and understand how data is used to minimise the risk of losing money while lending to customers.
#  Banking Customer Data Analytics

## Project Overview

**Banking Customer Data Analytics** is an end-to-end data analytics project designed to analyze customer banking information and generate meaningful business insights.

The project combines **Python, PostgreSQL/SQL, and Microsoft Power BI** to perform data exploration, data preparation, statistical analysis, visualization, and interactive dashboard development.

The analysis focuses on customer demographics, income, banking products, loans, deposits, accounts, credit cards, loyalty classification, and risk-related attributes.

---

##  Objectives

The main objectives of this project are:

* Analyze customer banking data to identify meaningful patterns.
* Understand customer demographics and banking behavior.
* Analyze customer income and create meaningful income segments.
* Study credit card, loan, deposit, and account information.
* Examine customer loyalty classifications.
* Analyze risk-weighting patterns.
* Identify relationships between important numerical variables.
* Store and query the processed data using PostgreSQL.
* Create an interactive Power BI dashboard for business reporting.
* Provide data-driven insights that can support banking decisions.

---

##  Technologies Used

| Technology           | Purpose                             |
| -------------------- | ----------------------------------- |
| **Python**           | Data analysis and preprocessing     |
| **Pandas**           | Data manipulation                   |
| **NumPy**            | Numerical operations                |
| **Matplotlib**       | Data visualization                  |
| **Seaborn**          | Statistical visualization           |
| **PostgreSQL**       | Database storage and SQL analysis   |
| **SQLAlchemy**       | Python–PostgreSQL connection        |
| **Power BI**         | Interactive dashboard and reporting |
| **Jupyter Notebook** | Exploratory Data Analysis           |
| **Git/GitHub**       | Version control and project sharing |

---

##  Project Files

```text
Banking-Data-Analytics/
│
├── 📓 banking eda.ipynb
├── 🗄️ banking dbsql.sql
├── 📊 banking dashboard.pbix
└── 📄 README.md
```

### File Description

* **`banking eda.ipynb`** — Python-based Exploratory Data Analysis.
* **`banking dbsql.sql`** — SQL query used to retrieve banking customer data.
* **`banking dashboard.pbix`** — Power BI interactive dashboard.
* **`README.md`** — Project documentation.

The SQL file currently contains a query to retrieve records from the `customer_banking_data` table.

---

#  Dataset

The project works with customer banking data containing attributes related to:

### 👤 Customer Information

* Client ID
* Name
* Age
* Location
* Nationality
* Occupation
* Gender
* Bank joining date

###  Financial Information

* Estimated income
* Superannuation savings
* Credit card balance
* Bank loans
* Bank deposits
* Business lending

###  Banking Products & Accounts

* Number of credit cards
* Checking accounts
* Saving accounts
* Foreign currency accounts
* Properties owned

###  Customer Classification

* Fee structure
* Loyalty classification
* Risk weighting
* Banking relationship identifiers

---

#  Exploratory Data Analysis

The EDA was performed using Python with Pandas, Matplotlib, Seaborn, and NumPy.

## 1. Data Loading

The dataset is loaded into a Pandas DataFrame for analysis.

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import numpy as np

df = pd.read_csv('Banking.csv')
```

## 2. Data Understanding

The following operations were performed:

* Previewing the dataset
* Checking column names
* Understanding data types
* Generating descriptive statistics
* Checking missing values

```python
df.head()
df.columns
df.info()
df.describe(include='all')
df.isnull().sum()
```

## 3. Data Cleaning

Column names were standardized by converting them to lowercase and replacing spaces with underscores.

```python
df.columns = df.columns.str.lower()
df.columns = df.columns.str.replace(' ', '_')
```

This makes the dataset easier to work with in Python, SQL, and Power BI.

---

#  PostgreSQL Database Integration

The processed dataset was loaded into a PostgreSQL database using SQLAlchemy.

```text
Database: banking_data
Table: customer_banking_data
```

Python was connected to PostgreSQL using SQLAlchemy, and the DataFrame was written to the database.

The SQL layer can then be used to retrieve and analyze customer banking records.

Example:

```sql
SELECT *
FROM customer_banking_data
LIMIT 20;
```

---

#  Income Band Analysis

Customer income was divided into three groups using quantile-based segmentation:

* **Low**
* **Medium**
* **High**

The project uses `pd.qcut()` to divide estimated income into three approximately equal-sized groups.

```python
labels = ['low', 'medium', 'high']

df['income_band'] = pd.qcut(
    df['estimated_income'],
    q=3,
    labels=labels
)
```

This helps compare customer characteristics across different income segments.

---

#  Categorical Analysis

Several categorical variables were analyzed using count plots.

The analysis includes attributes such as:

* Banking relationship
* Gender
* Age/identity-related classifications
* Number of credit cards
* Nationality
* Occupation
* Fee structure
* Loyalty classification
* Properties owned
* Risk weighting
* Income band

The analysis was also extended by comparing categories across **gender** and **nationality**.

---

#  Numerical Analysis

The following financial variables were explored using distributions and histograms:

* Estimated income
* Superannuation savings
* Credit card balance
* Bank loans
* Bank deposits
* Checking accounts
* Saving accounts
* Foreign currency accounts
* Business lending

These visualizations help identify:

* Distribution patterns
* Concentration of values
* Possible outliers
* Differences in customer financial behavior

---

#  Correlation Analysis

A correlation matrix was created for the major numerical variables.

```python
numerical_cols = [
    'estimated_income',
    'superannuation_savings',
    'credit_card_balance',
    'bank_loans',
    'bank_deposits',
    'checking_accounts',
    'saving_accounts',
    'foreign_currency_account',
    'business_lending'
]

correlation_matrix = df[numerical_cols].corr()
```

The correlation analysis helps identify relationships between financial variables.

For example, it can help investigate whether higher-income customers tend to have higher deposits, loans, or account balances.

**Note:** Correlation indicates association, not causation.

---

#  Power BI Dashboard

The processed banking data is visualized through an interactive **Power BI dashboard**.

The dashboard is designed to provide a business-friendly overview of customer banking behavior.

### Key analytical areas

* Customer overview
* Customer demographics
* Income analysis
* Banking accounts
* Credit cards
* Loans
* Deposits
* Customer loyalty
* Risk analysis
* Banking product usage

### Example KPI Concepts

Depending on the measures implemented in the dashboard, important KPIs can include:

* Total Customers
* Total Accounts
* Total Bank Deposits
* Total Bank Loans
* Total Credit Card Balance
* Average Customer Income
* Average Age
* Customer Distribution by Loyalty
* Customer Distribution by Risk Category

---

#  Business Insights

The project can help banking organizations answer questions such as:

1. Which customer groups generate the highest banking value?
2. How are customers distributed across income bands?
3. What banking products are most commonly used?
4. How are loans and deposits distributed among customers?
5. What relationship exists between income and banking activity?
6. Which customer segments have higher credit card balances?
7. How does loyalty classification vary across customer groups?
8. How are customers distributed across different risk categories?
9. What financial variables have strong relationships with each other?
10. Which customer segments could be targeted for specific banking products?

---

#  Project Workflow

```text
Raw Banking Dataset
        ↓
Data Loading
        ↓
Data Cleaning & Standardization
        ↓
Exploratory Data Analysis
        ↓
Income Segmentation
        ↓
Statistical & Correlation Analysis
        ↓
PostgreSQL Database
        ↓
SQL Analysis
        ↓
Power BI Data Modeling
        ↓
DAX Measures & KPIs
        ↓
Interactive Dashboard
        ↓
Business Insights
```

---

# How to Run the Project

## Step 1 — Clone the Repository

```bash
git clone <repository-url>
cd Banking-Data-Analytics
```

## Step 2 — Install Python Libraries

```bash
pip install pandas numpy matplotlib seaborn sqlalchemy psycopg2-binary jupyter
```

## Step 3 — Run the EDA Notebook

Open:

```text
banking eda.ipynb
```

Run the notebook cells sequentially to perform the analysis.

## Step 4 — Configure PostgreSQL

Create a PostgreSQL database named:

```text
banking_data
```

Then configure your PostgreSQL connection details before running the database-loading section.

> **Security Note:** Never commit real database passwords, API keys, or other credentials to GitHub. Use environment variables or a `.env` file instead.

## Step 5 — SQL Analysis

Use:

```text
banking dbsql.sql
```

to execute SQL queries against the `customer_banking_data` table.

## Step 6 — Open the Power BI Dashboard

Open:

```text
banking dashboard.pbix
```

in Microsoft Power BI Desktop.

Update the data source/credentials if required and refresh the dashboard.

---

#  Key Skills Demonstrated

This project demonstrates practical knowledge of:

* Data Cleaning
* Exploratory Data Analysis
* Data Visualization
* Statistical Analysis
* Correlation Analysis
* Feature/Category Engineering
* Income Segmentation
* SQL
* PostgreSQL
* Python–Database Integration
* Power BI
* DAX Measures
* Dashboard Development
* Business Intelligence
* Data Storytelling

---

#  Future Improvements

Potential improvements include:

* Adding automated data pipelines.
* Adding customer segmentation using clustering.
* Developing customer churn analysis.
* Building predictive risk models.
* Adding time-based banking trends.
* Creating automated Power BI refresh workflows.
* Adding more advanced DAX calculations.
* Developing a machine-learning-based customer recommendation system.

---

#  Author

**Mustafa Syed**

### Data Analytics Project

**Tools:** Python • SQL • PostgreSQL • Power BI • DAX

---

# ⭐ Project Summary

This project demonstrates an end-to-end **Banking Data Analytics workflow**, starting from raw customer data and progressing through Python-based EDA, PostgreSQL database integration, SQL analysis, and Power BI visualization.

The overall goal is to transform raw banking customer data into **clear, interactive, and actionable business insights** that can support customer analysis and banking decision-making.
