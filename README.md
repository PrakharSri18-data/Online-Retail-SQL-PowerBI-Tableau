# 🛒 Online Retail — SQL + Power BI Analytics Project

A complete end-to-end data analytics project on a real-world online retail dataset. Raw transactional data is cleaned, structured, and analyzed using **MySQL**, then visualized through an interactive **Power BI** dashboard.

---

## 📁 Repository Structure

```
Online-Retail-SQL-PowerBI/
│
├── Online Retail.sql           # Full SQL script: DB setup, ETL, KPIs & analysis
├── Online Retail Dashboards.pbix  # Power BI dashboard file
├── Online Retail Dataset.zip   # Raw dataset (CSV)
├── SQL Outputs/                # Query result screenshots / exports
└── LICENSE                     # MIT License
```

---

## 🗂️ Dataset

The dataset is a UK-based online retail transaction record containing all purchases between **2010 and 2011**. It includes:

| Column | Description |
|---|---|
| `InvoiceNo` | Unique transaction identifier |
| `StockCode` | Product code |
| `Description` | Product name |
| `Quantity` | Units purchased per transaction |
| `InvoiceDate` | Date and time of transaction |
| `UnitPrice` | Price per unit (GBP) |
| `CustomerID` | Unique customer identifier |
| `Country` | Customer's country |

> The raw CSV is provided as `Online Retail Dataset.zip` in the repository.

---

## 🛠️ Tools & Technologies

- **MySQL** — Database creation, data cleaning, ETL pipeline, and analytical queries
- **Power BI** — Interactive dashboard and data visualization
- **SQL Concepts Used** — CTEs, Window Functions (`RANK`, `NTILE`), Joins, Subqueries, Temporary Tables, Indexing, Date Functions

---

## 🔄 SQL Workflow

### 1. Database Setup
- Created the `ONLINE_RETAIL` database and a `RAW_DATA` table to load the CSV.
- Imported data using `LOAD DATA LOCAL INFILE`.
- Converted `INVOICE_DATE` from string to proper `DATETIME` format using `STR_TO_DATE`.
- Created indexes on `CUSTOMER_ID`, `INVOICE_NO`, `STOCK_CODE`, and `INVOICE_DATE` for query performance.

### 2. Data Modeling (Star Schema)
Normalized the raw data into four structured tables:

```
CUSTOMERS     ──┐
                ├──> ORDERS ──> ORDER_ITEMS <── PRODUCTS
```

| Table | Key Columns |
|---|---|
| `CUSTOMERS` | `CUSTOMER_ID`, `COUNTRY`, `REGISTRATION_DATE` |
| `PRODUCTS` | `PRODUCT_ID`, `PRODUCT_NAME` |
| `ORDERS` | `ORDER_ID`, `CUSTOMER_ID`, `ORDER_DATE` |
| `ORDER_ITEMS` | `ORDER_ID`, `PRODUCT_ID`, `QUANTITY`, `UNIT_PRICE` |

### 3. KPIs & Business Analysis
Queries written to power the dashboard and answer business questions:

| Analysis | Description |
|---|---|
| **Total Revenue** | Overall revenue from all orders |
| **Total Orders** | Count of distinct invoices |
| **Average Order Value** | Revenue divided by total orders |
| **Monthly Revenue** | Revenue trend grouped by month |
| **Revenue by Country** | Country-wise revenue breakdown |
| **Top 10 Products by Revenue** | Best-selling products |
| **Top Customer per Country** | Highest spender in each country using `RANK() OVER PARTITION BY` |
| **Customer Lifetime Value (CLV)** | Total revenue attributed per customer |
| **Repeat Customer Rate** | % of customers with more than one order |
| **Average Order Frequency** | Average number of orders per customer |
| **Customer Ranking by Revenue** | Global ranking of customers by spend |
| **Customer Ranking by Orders** | Global ranking by number of orders |
| **Cohort Analysis** | Monthly retention — tracks when customers first purchased vs. when they returned |
| **RFM Segmentation** | Recency, Frequency, Monetary scoring using `NTILE(5)` + rule-based segmentation into Champions, Loyal Customers, At Risk, New Customers, and Others |

---

## 📊 Power BI Dashboard

The `.pbix` file (`Online Retail Dashboards.pbix`) connects to the SQL outputs and presents:

- 📈 **Revenue Trends** — Monthly revenue chart
- 🌍 **Geographic Analysis** — Revenue by country
- 🏆 **Top Products** — Best-performing SKUs
- 👥 **Customer Segmentation** — RFM-based segments
- 🔄 **Cohort Retention** — Customer cohort analysis
- 💰 **CLV Overview** — Customer lifetime value distribution

> Open the `.pbix` file in **Power BI Desktop** to explore or modify the dashboards.

---

## 🚀 How to Run This Project

### Prerequisites
- MySQL Server (v8.0+) with `LOCAL_INFILE` enabled
- Power BI Desktop (free download from Microsoft)

### Steps

1. **Clone the repository**
   ```bash
   git clone https://github.com/PrakharSri18-data/Online-Retail-SQL-PowerBI.git
   ```

2. **Prepare the dataset**
   - Extract `Online Retail Dataset.zip`
   - Place the CSV file at the path referenced in the SQL script (update the `LOAD DATA` path to match your local system)

3. **Run the SQL script**
   - Open `Online Retail.sql` in MySQL Workbench (or any MySQL client)
   - Execute the full script top-to-bottom
   - Tables will be created and populated automatically

4. **Open the dashboard**
   - Open `Online Retail Dashboards.pbix` in Power BI Desktop
   - Refresh the data source connection if needed

---

## 💡 Key Insights (from SQL Analysis)

- **RFM Segmentation** identifies high-value "Champions" vs. churning "At Risk" customers — enabling targeted retention strategies.
- **Cohort Analysis** reveals how customer retention evolves month-over-month after the first purchase.
- **Country-wise revenue** highlights geographic concentration, helping prioritize marketing spend.
- **Top 10 products** by revenue can guide inventory and promotional decisions.

---

## 📄 License

This project is licensed under the [MIT License](LICENSE) © 2026 Prakhar Srivastava.

---

## 🙋 Author

**Prakhar Srivastava**  
Data Analyst | SQL · Power BI · Python  
[GitHub](https://github.com/PrakharSri18-data)
