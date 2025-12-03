Real Estate Analytics Data Platform
Azure Data Factory | Azure SQL | Data Flows | Stored Procedures
🚀 Project Summary

This project implements a complete cloud-based data warehouse for RealEstateCo.
It integrates data from multiple CSV sources into a unified Azure SQL-based warehouse using ADF pipelines, Data Flows, and Stored Procedures.

🏗 Architecture
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

🗂 Source Entities
Agents
Properties
Listings
Campaigns
Leads
Offers
Viewings
Transactions

🧱 Data Warehouse Schema
Dimensions

DimAgent

DimProperty

DimListing

DimCampaign

DimDate

DimLead

Fact Tables

FactTransaction

FactOffer

FactViewing

FactLead

🔄 ADF Pipelines
1️⃣ copy_all_files

Reads all CSV files from Blob

Uses Get Metadata + ForEach

Dynamically loads each into correct staging table

2️⃣ DWH Load Pipeline

Executes Stored Procedure

Loads dimensions (SCD Type 1)

Loads fact tables

Maintains surrogate keys

🔧 Stored Procedure Framework

Master loader:

dwh.usp_LoadWarehouse


Includes:

Dim loaders

Fact loaders

Reseed identity keys

Re-enable constraints

📊 Analytics Ready

Power BI dashboards can be created for:

Sales trends

Agent performance

Marketing impact

Lead conversions

Property pricing trends

👨‍💻 Tech Stack

Azure Data Factory

Azure SQL Database

Azure Blob Storage

SSMS

Power BI

SQL Stored Procedures

Data Flows
