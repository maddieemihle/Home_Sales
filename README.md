# Home Sales Analysis with PySpark

## Introduction
This project leverages **Apache Spark** on **Google Colab** to perform large-scale data analysis on home sales data. The primary objective is to efficiently compute insights from real estate transaction records using **SparkSQL**, **DataFrame operations**, and **performance tuning** techniques such as **caching** and **parquet partitioning**. 

By utilizing Spark’s distributed computing capabilities, we explore key housing trends such as pricing by year, bedroom/bathroom configuration, square footage, and view ratings.

---

## Table of Contents
- [Project Setup](#-project-setup)
- [Overview of Analysis](#-overview-of-analysis--instructions-followed)
- [Results](#-results)
- [Conclusion](#-conclusion)
- [Software & Tools](#-software--tools)
- [Technologies Used](#-technologies-used)
- [Resources](#-resources)

---

## Project Setup
The project was implemented in **Google Colab**, which required configuring Apache Spark (v3.5.3) and OpenJDK 11 manually. The steps include:
- Installing Spark and Java
- Setting environment variables
- Initializing a SparkSession
- Importing required PySpark SQL functions
- Loading housing data from a publicly accessible S3 bucket using pandas (then converting to a Spark DataFrame)

---

## Overview of Analysis
This project followed a defined set of analytical instructions that reflect typical industry data engineering tasks. Key steps included:

1. **Reading the CSV file** from an AWS S3 URL using pandas (due to Spark’s incompatibility with direct HTTPS loading).
2. **Creating a temporary SQL view** of the DataFrame for querying via SparkSQL.
3. **Writing SparkSQL queries** to answer the following questions:
   - Query 1: Average price of four-bedroom homes sold per year.
   - Query 2: Average price of homes built each year with 3 bedrooms and 3 bathrooms.
   - Query 3: Average price of homes with 3 beds, 3 baths, 2 floors, and at least 2,000 sq ft.
   - Query 4: Average price by "view" rating, where the average price is ≥ $350,000.
4. **Measuring query performance:**
   - Timed uncached vs. cached queries.
   - Partitioned data using Parquet by `date_built` to optimize future access.
5. **Creating and uncaching temporary views** to manage Spark memory efficiently.

---

## Results
- **Four-bedroom homes:** The average price increased gradually year-over-year, showing market appreciation over time.
- **3 bed/3 bath homes:** Prices varied by construction year, with newer homes typically commanding higher average prices.
- **Filtered homes (3 bed, 3 bath, 2 floors, ≥ 2,000 sqft):** A similar trend appeared, with homes built in recent years averaging higher prices.
- **View ratings ≥ $350,000:** Homes with higher view ratings tended to have significantly higher prices. Query runtimes improved drastically after caching and partitioning.
- **Performance impact:**
  - Caching reduced query runtime from several seconds to under 1 second.
  - Partitioning with Parquet further improved runtime consistency and efficiency.

---
## Conclusion

This project demonstrates the power and efficiency of using PySpark for scalable data analysis. Even with a modestly sized dataset, Spark’s in-memory processing and partitioning features made a clear impact on performance. The combination of SQL-like syntax and distributed computation is a strong fit for real-world big data scenarios such as real estate, finance, and health analytics.

By conducting this analysis in a cloud-based notebook (Google Colab), we proved the accessibility of Spark for students and early-career analysts, even without a dedicated cluster.

---

## Software & Tools
- Google Colab (runtime environment)
- OpenJDK 11 (Java Runtime for Spark)
- PySpark (Python API for Spark)
- pandas (CSV parsing and pre-processing)
- Git & GitHub (version control and hosting)

## Technologies Used
- **Apache Spark 3.5.3**
- **Google Colab (Jupyter Notebook interface)**
- **PySpark**
- **Pandas**
- **Python 3.10+**

## Resources
- [Apache Spark Documentation](https://spark.apache.org/docs/latest/)
- [PySpark SQL API Reference](https://spark.apache.org/docs/latest/api/python/)
- [Google Colab](https://colab.research.google.com/)
- [AWS S3 Home Sales CSV (provided)](https://s3.amazonaws.com/)
- [Home Sales Notebook](https://github.com/maddieemihle/Home_Sales/blob/main/Home_Sales_colab.ipynb)
