# 🌟 Retail Analytics Data Engineering Project (Medallion Architecture on Azure)

---

# Project Overview
This project is a **real-world batch data pipeline** using **Medallion Architecture** (Bronze, Silver, Gold layers) on Azure with free-tier resources.

You will build an automated, scalable, production-grade data pipeline for a retail company.


# 📊 Medallion Architecture

| Layer  | Purpose | Storage Format |
|:------ |:--------|:---------------|
| Bronze | Raw data ingestion with minimal transformation | CSV/Parquet |
| Silver | Cleaned, validated, enriched data | Delta Lake |
| Gold   | Aggregated, analytics-ready data | Delta Lake / Azure SQL |

---

# 🎓 Technologies Used

- Azure Data Lake Storage Gen2
- Azure Event Grid
- Azure Functions
- Azure Data Factory (ADF)
- Azure Databricks (PySpark)
- Azure SQL Database (for Gold layer)
- Power BI Desktop (Optional Visualization)
- Azure Monitor + Logging

---

# 📁 Project Flow

```
(Local CSV Upload)
    ↓
Azure Data Lake (Bronze Zone - /bronze/)
    ↓
Databricks: Clean and Validate (Silver Zone - /silver/)
    ↓
Databricks: Aggregate & Prepare Analytics Tables (Gold Zone - /gold/)
    ↓
Azure SQL Database (Optional for serving BI tools)
    ↓
(Optional) Power BI Dashboard
```

---

# 📂 Folder Structure in Azure Data Lake

```
/retail_data/
    /bronze/
        /products/
        /customers/
        /transactions/
        /stores/
    /silver/
        /products/
        /customers/
        /transactions/
        /stores/
    /gold/
        /sales_summary/
    /logs/
        pipeline_logs.parquet
```

---

# 💼 Local Files to Prepare

```bash
/local/retail_data/
    products.csv
    customers.csv
    transactions.csv
    stores.csv
```

Each CSV should have 500–1000 rows with headers.

| File | Description |
|:-----|:------------|
| products.csv | id, name, category, price |
| customers.csv | id, name, email, signup_date |
| transactions.csv | id, customer_id, product_id, store_id, quantity, price, date |
| stores.csv | id, store_name, location |


---

# 📊 Azure SQL Database Tables (Gold Layer)

- **dim_product**
- **dim_customer**
- **dim_store**
- **fact_transaction**
- **sales_summary** (Aggregated)
- **pipeline_run_log** (Monitoring)


---

# 💚 Key Features Implemented

- Medallion Architecture: Bronze -> Silver -> Gold
- Event-driven ingestion with Azure Event Grid and Functions
- Data Lake raw/cleaned/aggregated zones
- Delta Lake storage in Silver and Gold layers
- PySpark transformation pipelines
- Automated orchestration with Azure Data Factory
- Data Validation and Cleaning in Silver
- Aggregations in Gold layer
- Monitoring and Logging with Azure Monitor and Custom Logs
- (Optional) Power BI Visualization


---

# 📌 Step-by-Step Pipeline Execution

### 1. Upload Local CSVs to Data Lake Bronze Zone
- Upload raw files manually or automate later.

### 2. Event Grid + Azure Function
- Detect file upload.
- Trigger Azure Data Factory pipeline.

### 3. Bronze Layer -> Silver Layer (Databricks Job 1)
- Read raw data.
- Clean, Validate, Standardize.
- Save as Delta Tables into Silver zone.

### 4. Silver Layer -> Gold Layer (Databricks Job 2)
- Read clean data.
- Build fact/dim tables.
- Aggregate sales into monthly/yearly summaries.
- Save into Gold zone.

### 5. Load Gold Tables into Azure SQL Database
- Use `.write.jdbc()` method from Databricks.

### 6. Monitoring and Logging
- Log pipeline run metadata.
- Monitor Azure resources.

### 7. (Optional) Visualization
- Create Power BI dashboard connecting to Azure SQL Database.


---

# 🎯 Future Enhancements

- Incremental loads (based on watermark columns)
- Schema evolution handling
- Data deduplication strategies
- Alerting system on pipeline failures
- CI/CD Deployment pipelines


---

# 👨‍💻 Author

**Designed by: Aakash Patel**

---




