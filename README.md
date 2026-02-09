
<h2 style="font-size:40px;">Clinical Data Analysis (Power BI + SQL Server)</h2>

Link: https://app.powerbi.com/view?r=eyJrIjoiM2ZlZDcyMzgtNDhiZS00NTRlLTgxM2UtZDRhNGRjMDBhYmRiIiwidCI6IjIzODk2NDkwLTdlNzMtNGQ1Zi1hZjQ5LTBmMjUwMzQ5NWQ3NSJ9&pageName=91d4fd5c4a058e7c845d

Overview

This project presents a **Clinical Data Analysis Dashboard** built using **Power BI** with **SQL Server** as the data source. The dataset contains **approximately 20 million (2 crore) clinical records**, designed to simulate large-scale healthcare data.

The primary objective of this dashboard is to analyze hospital-level and year-wise clinical trends while ensuring **high performance** by performing all data preparation directly in **SQL Server**.

The report consists of **two analytical pages**:

* **Hospital Analysis**
* **Analysis by Year**

---

Problem Statement

Healthcare datasets are often extremely large and complex, making in-memory transformations inefficient. This project focuses on handling **high-volume clinical data** efficiently by pushing all data cleaning, profiling, and transformations to the **SQL Server layer**, enabling seamless **query folding** in Power BI.

Using this dashboard, users can:

* Monitor admissions, readmissions, infections, and deaths by hospital
* Analyze year-wise trends in clinical metrics
* Handle large datasets without performance degradation
* Ensure accurate reporting using pre-cleaned SQL data

---

Tools & Technologies Used

* **SQL Server**
* **Power BI Desktop**
* **SQL (Dynamic SQL, Data Profiling)**
* **Query Folding**
* **Large-scale Data Handling (20M+ records)**
* **Custom Background Images for UI**

---

Steps Followed

Data Creation & Preparation (SQL Server)

* **Step 1:** Created a clinical database and table structure in SQL Server to store hospital-level clinical data.
* **Step 2:** Generated **20 million+ records** across multiple hospitals using SQL loops and randomization logic.
* **Step 3:** Performed **complete data cleaning and transformation in SQL Server**, including:

  * Handling null values
  * Correcting invalid date ranges
  * Standardizing clinical metrics
* **Step 4:** Implemented **data profiling using dynamic SQL**, calculating:

  * Min / Max
  * Mean, Median, Mode
  * Standard Deviation
  * Null count, Zero count, Distinct count
* **Step 5:** Ensured **query folding** so Power BI only consumes optimized, pre-processed data.

---

Data Profiling (SQL-Driven)

Data profiling was performed entirely in SQL Server using **dynamic SQL**, enabling column-wise analysis without manual intervention.

Example: Column Distribution & Profiling (Dynamic SQL)

```sql
SELECT column_name, ordinal_position, data_type
FROM INFORMATION_SCHEMA.COLUMNS
WHERE TABLE_NAME = 'ClinicalData';
```

```sql
SELECT 
    HospitalID,
    COUNT(*) AS RecordCount
FROM ClinicalData
GROUP BY HospitalID;
```

```sql
SELECT 
    MIN(AdmissionDate) AS MinDate,
    MAX(AdmissionDate) AS MaxDate
FROM ClinicalData;
```

> All statistical calculations were executed in SQL Server to avoid Power BI memory overhead.

---

Power BI Report Design

Page 1: Hospital Analysis

* Number of Admissions by Hospital
* Number of Readmissions by Hospital
* Number of Infections by Hospital
* Number of Deaths by Hospital

Page 2: Analysis by Year

* Year-wise Admissions trend
* Year-wise Readmissions trend
* Year-wise Infections trend
* Year-wise Deaths trend

> No DAX measures were created; all aggregations are handled by SQL Server.

---

Performance Optimization

* Leveraged **query folding** to push all transformations to SQL Server
* Avoided calculated columns and measures in Power BI
* Optimized SQL queries for large-volume data
* Ensured fast report rendering despite **20M+ rows**

---

Key Insights

* Hospital-level analysis highlights variations in admissions, readmissions, infections, and deaths.
* Year-wise trends provide visibility into long-term clinical performance.
* SQL-driven preprocessing ensures accuracy and scalability.
* Dashboard remains responsive despite large dataset size.

---

Conclusion

This project demonstrates a **production-style Power BI solution** built for **large-scale healthcare data**. By shifting all transformations and profiling to **SQL Server**, the solution ensures optimal performance, scalability, and clean analytics consumption in Power BI.

This project strongly showcases:

* Advanced SQL skills
* Query folding expertise
* Large dataset handling
* Power BI performance optimization
