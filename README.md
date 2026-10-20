# SQL Data Warehouse Project

An end-to-end data warehouse I built using **SQL Server**, following the **Medallion Architecture** (Bronze → Silver → Gold).

The goal of this project was to design and implement a modern data warehouse that consolidates sales data from multiple source systems (CRM and ERP) into a clean, analytics-ready star schema.

---

## 🏗️ Architecture

I structured the warehouse using the Medallion Architecture:

| Layer     | Purpose                              | What I implemented                          |
|-----------|--------------------------------------|---------------------------------------------|
| **Bronze**    | Raw data storage                     | Ingested CSV files as-is from CRM & ERP     |
| **Silver**    | Cleaned & standardized data          | Data cleansing, standardization, and integration |
| **Gold**      | Business-ready data                  | Star schema with dimensions and a fact table |

---

## 📊 What I Built

### Data Pipeline
- Loaded raw data from CRM and ERP source systems into the **Bronze** layer
- Cleaned, standardized, and integrated the data in the **Silver** layer
- Modeled a **Star Schema** in the **Gold** layer for analytics

### Gold Layer (Star Schema)
- **`gold.dim_customers`** – Customer dimension enriched with demographic and geographic data
- **`gold.dim_products`** – Product dimension with category and cost information
- **`gold.fact_sales`** – Sales fact table linked to customers and products

Full column-level documentation is available in [`docs/data_catalog.md`](docs/data_catalog.md).

### Data Quality
- Created quality check scripts for both the Silver and Gold layers to validate data integrity

---

## 🛠️ Technologies Used

- **SQL Server**
- **T-SQL** (DDL, stored procedures, views)
- **SQL Server Management Studio (SSMS)**
- **Git & GitHub**

---

## 📂 Project Structure
sql-data-warehouse-project/
├── datasets/                  # Source CSV files
├── docs/
│   └── data_catalog.md        # Gold layer documentation
├── scripts/
│   ├── init_database.sql      # Database & schema creation
│   ├── bronze/                # Bronze layer scripts
│   ├── silver/                # Silver layer scripts
│   └── gold/                  # Gold layer scripts
├── tests/                     # Data quality checks
└── README.md
text---

## 🚀 How to Run the Project

1. Clone the repository
2. Place the source CSV files in the `datasets/` folder (or update the file paths in the Bronze load procedure)
3. Execute the scripts in the following order:

```sql
-- 1. Create database and schemas
scripts/init_database.sql

-- 2. Bronze layer
scripts/bronze/ddl_bronze.sql
scripts/bronze/proc_load_bronze.sql   -- then EXEC bronze.load_bronze;

-- 3. Silver layer
scripts/silver/ddl_silver.sql
scripts/silver/proc_load_silver.sql   -- then EXEC silver.load_silver;

-- 4. Gold layer
scripts/gold/ddl_gold.sql

(Optional) Run the quality checks in the tests/ folder


📄 License
This project is licensed under the MIT License [blocked].

Built by Dumebi Ezenwa
