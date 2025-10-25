# End-to-End Healthcare Data Engineering Pipeline

![Azure](https://img.shields.io/badge/Azure-Cloud-blue?logo=microsoft-azure&style=flat-square)
![PySpark](https://img.shields.io/badge/PySpark-Big%20Data-orange?logo=apache-spark&style=flat-square)
![Azure Data Factory](https://img.shields.io/badge/Azure-Data%20Factory-blue?logo=microsoft-azure&style=flat-square)
![Azure Synapse](https://img.shields.io/badge/Azure-Synapse%20Analytics-blue?logo=microsoft-azure&style=flat-square)
![Python](https://img.shields.io/badge/Python-3.9+-yellow?logo=python&style=flat-square)
![Databricks](https://img.shields.io/badge/Databricks-PySpark-red?logo=databricks&style=flat-square)
![PowerBI](https://img.shields.io/badge/Power%20BI-Dashboard-orange?logo=power-bi&style=flat-square)
![Git](https://img.shields.io/badge/Git-CI%2FCD-green?logo=git&style=flat-square)

---

## 📑 Table of Contents
- [📌 Project Overview](#-project-overview)
- [🎯 Objectives](#-objectives)
- [📂 Project Structure](#-project-structure)
- [🛠️ Tools & Technologies](#️-tools--technologies)
- [🏗️ Data Architecture](#️-data-architecture)
- [⭐ Star Schema Design](#-star-schema-design)
- [⚙️ Step-by-Step Implementation](#️-step-by-step-implementation)
  - [1. Event Hub Setup](#1-event-hub-setup)
  - [2. Data Simulation](#2-data-simulation)
  - [3. Storage Setup](#3-storage-setup)
  - [4. Databricks Processing](#4-databricks-processing)
  - [5. Synapse SQL Pool](#5-synapse-sql-pool)
  - [6. Version Control](#6-version-control)
- [📊 Data Analytics](#-data-analytics)
- [✅ Key Outcomes](#-key-outcomes)

---

## 📌 Project Overview
This project showcases a **real-time healthcare data engineering pipeline** built on **Microsoft Azure**.  
It simulates hospital operations such as **patient admissions, transfers, and discharges**, processes the live stream using **Databricks**, and delivers insights through **Power BI dashboards** connected to **Synapse SQL Pool**.

The solution bridges **data engineering** and **data analytics**—from ingestion to insight—enabling hospitals to track patient movement and bed utilization efficiently.


## Pipeline

<img width="4719" height="2432" alt="Architecture" src="https://github.com/SahiLmb/Real-time-Hospital-flow-Analytics/blob/main/Architecture%20Diagram/Flowchart.jpg" />


---

## 🎯 Objectives
- Stream real-time hospital data via **Azure Event Hub**.  
- Build a **multi-layer ETL pipeline** (Bronze → Silver → Gold) in **Azure Databricks**.  
- Design a **Star Schema** in **Synapse SQL Pool** for analytical queries.  
- Visualize patient and department metrics in **Power BI**.  
- Maintain **version control** using Git.

---

## 📂 Project Structure
```plaintext
real-time-patient-flow-azure/
│
├── databricks-notebooks/  # Transformation notebooks
│   ├── 01_bronze_rawdata.py
│   ├── 02_silver_cleandata.py
│   └── 03_gold_transform.py
├── simulator/             # Data simulation scripts
│   └── patient_flow_generator.py
├── sqlpool-queries/        # SQL scripts for Synapse
│   └── SQL_queries.sql
├── Architecure Diagram/FLowchart                  # Flowchart
└── README.md              # Project documentation
```

---

## 🛠️ Tools & Technologies
- **Azure Event Hub** – Real-time data ingestion
- **Azure Databricks** – PySpark-based data transformation
- **Azure Data Lake Gen2** – Layered data storage
- **Azure Synapse SQL Pool** – Data warehouse for analytics
- **Power BI** – Dashboard and visualization
- **Python 3.9+** – Core programming
- **Git** – Version control

---

## 🏗️ Data Architecture
The pipeline follows a **medallion architecure**:
- **Bronze Layer**: Raw JSON data from Event Hub stored in ADLS.
- **Silver Layer**: Cleaned and structured data (validated types, null handling).
- **Gold Layer**: Created analytical models and star schema tables for BI.

---

## ⭐ Star Schema Design
The **Gold layer** data in Synapse follows a **star schema** for optimized analytics:
- **Fact Table**: `FactPatientFlow` (patient visits, timestamps, wait times, discharge)
- **Dimension Tables**:
  - `DimDepartment` – Department details
  - `DimPatient` – Patient demographic info
  - `DimTime` – Date and time dimension

---

## ⚙️ Step-by-Step Implementation

### **1. Event Hub Setup**
- Created **Event Hub namespace** and **patient-flow hub**.
- Configured **consumer groups** for Databricks streaming.

---

### **2. Data Simulation**
- Developed **Python script** `patient_flow_generator.py` to stream fake patient data (departments, wait time, discharge status) to Event Hub.
- [Producer Code](simulator/patient_flow_generator.py)

---

### **3. Storage Setup**
- Configured **Azure Data Lake Storage (ADLS Gen2)**.
- Created three containers:
- bronze/ → Raw JSON from Event Hub
- silver/ → Clean and structured data
- gold/ → Transformed fact and dimension tables.

---

### **4. Databricks Processing**
- [**Notebook 1**](databricks-notebooks/01_bronze_rawdata.py): Reads Event Hub stream into Bronze.
- [**Notebook 2**](databricks-notebooks/02_silver_cleandata.py): Cleans and validates schema.
- [**Notebook 3** ](databricks-notebooks/03_gold_transform.py): Aggregates and prepares star schema tables.

---

### **5. Synapse SQL Pool**
- Created **dedicated SQL Pool**.
- Executed schema and fact/dimension creation queries from:
  - [DDL_Queries](sqlpool-queries/SQL_queries.sql)

---

### **6. Version Control**
- Version control with **Git**:

---

## 📊 Data Analytics

Once the **data pipeline** was established and a **Star Schema** implemented in Synapse SQL Pool, the next step was to build an **interactive dashboard in Power BI**.  

### **🔗 Synapse → Power BI Connection**
- Connected **Azure Synapse SQL Pool** to Power BI using a direct SQL connection.  
- Imported **FactPatientFlow** and **Dimension tables**.  
- Established relationships for **Star Schema-based reporting**.  

### **📈 Dashboard Features**
The **Healthcare Patient Flow Dashboard** provides insights into:  
- **Bed Occupancy Rate** by department and gender.  
- **Patient Flow Trends** (admissions, wait times).  
- **Department-Level KPIs** (length of stay, Total Patients).  
- **Interactive Filters & Slicers** for gender.

<img width="1282" height="724" alt="update this" src="" />

---

## ✅ Key Outcomes
- **End-to-End Pipeline:** From **real-time ingestion → transformation → warehouse → analytics**.  
- **Scalable Architecture:** Easily adaptable for different hospital datasets.  
- **Business Insights:** Hospital admins can monitor **bed usage, patient flow, and department efficiency** in real time.
- **Technical Impact:** Delivered actionable hospital insights using Power BI and demonstrated a complete Azure Data Engineering lifecycle in one project 

---

**Author**: *Sahil Bodke* 

**LinkedIn**: [Sahil Bodke](https://www.linkedin.com/in/sahil-bodke-45570a251/) 

**Contact**: [work.bodke@gmail.com](mailto:work.bodke@gmail.com)
