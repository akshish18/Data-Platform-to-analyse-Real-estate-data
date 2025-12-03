# 🏡 Real Estate Analytics Data Platform  
### **Azure Data Factory | Azure SQL | Data Flows | Stored Procedures**

## 🚀 Project Summary
This project implements a complete cloud-based **Real Estate Data Warehouse** for *RealEstateCo*.  
It integrates multiple CSV data sources into an Azure SQL-based warehouse using **Azure Data Factory (ADF)** pipelines, mapping data flows, staging layers, and stored procedures.

---

## 🏗 Architecture

    +----------------------+
    | Azure Blob Storage   |
    | Source CSV Files     |
    +----------+-----------+
               |
               v
    +------------------------+
    | Azure Data Factory     |
    | copy_all_files Pipeline|
    +----------+-------------+
               |
               v
    +------------------------+
    | Staging (SQL)          |
    | stg.* tables           |
    +----------+-------------+
               |
               v
    +------------------------+
    | Stored Procedure       |
    | usp_LoadWarehouse      |
    +----------+-------------+
               |
               v
    +------------------------+
    | Data Warehouse (SQL)   |
    | Dimensions + Facts     |
    +------------------------+



---

## 🗂 Source Entities
- Agents  
- Properties  
- Listings  
- Campaigns  
- Leads  
- Offers  
- Viewings  
- Transactions  

---

## 🧱 Data Warehouse Schema

### **Dimensions**
- **DimAgent**  
- **DimProperty**  
- **DimListing**  
- **DimCampaign**  
- **DimDate**  
- **DimLead**

### **Fact Tables**
- **FactTransaction**  
- **FactOffer**  
- **FactViewing**  
- **FactLead**

---

## 🔄 ADF Pipelines

### **1️⃣ copy_all_files**
- Reads all CSV files from Azure Blob Storage  
- Uses **Get Metadata + ForEach**  
- Dynamically identifies file names  
- Loads each CSV into the correct **staging table (stg.\*)**  

### **2️⃣ DWH Load Pipeline**
- Executes master stored procedure  
- Loads all **dimensions (SCD Type 1)**  
- Loads all **fact tables**  
- Maintains surrogate keys  
- Rebuilds constraints  

---

## 🔧 Stored Procedure Framework

### **Master Loader**
- `dwh.usp_LoadWarehouse`

### Includes:
- Dimension loaders  
- Fact loaders  
- Identity reseeding  
- Constraint checks  
- Merge logic for SCD Type-1 dimensions  

---

## 📊 Analytics Ready

Power BI dashboards can be built for:
- Sales trends  
- Agent performance  
- Marketing campaign impact  
- Lead conversions & funnel analysis  
- Property pricing trends  

---

## 👨‍💻 Tech Stack
- **Azure Data Factory**  
- **Azure SQL Database**  
- **Azure Blob Storage**  
- **SQL Stored Procedures**  
- **Mapping Data Flows**  
- **SSMS**  
- **Power BI**  

---

