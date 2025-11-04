# University Rankings Project

## Table of Contents
1. [Project Overview](#project-overview)  
2. [Data Acquisition](#data-acquisition)  
3. [Data Wrangling and Transformation](#data-wrangling-and-transformation)  
4. [Data Storage](#data-storage)  
5. [Technical Report](#technical-report)  
6. [Challenges](#challenges)  

---

## Project Overview
This project analyzes the 2025 CWUR global university rankings dataset, which includes key indicators such as institutional rank, national rank, employability rank, research rank, and overall score for 2,000 universities worldwide. The goal is to acquire, clean, structure, and store the dataset in both relational and columnar formats for future analysis.

---

## Data Acquisition
Data was acquired using Python scripts, primarily through web scraping with `requests` and `BeautifulSoup`. The script collected university names, ranks, country, and scores from multiple pages. All data was compiled into a raw CSV for initial analysis. APIs were considered but proved restrictive due to permissions and rate limits.

**Deliverable:** `acquisition.ipynb` – outputs the raw dataset.

---

## Data Wrangling and Transformation
The raw dataset contained missing values, non-numeric characters in numeric columns, and inconsistent formatting. Key steps included:

- Converting numeric columns (`Rank`, `Score`) to appropriate types.
- Handling missing values using Random Forest-based iterative imputation for columns with high missingness.
- Creating a new categorical column `Global_Region` based on country.
- Normalizing the score column to `Score_Normalized` (0–1 scale).
- Removing duplicates and ensuring unique identifiers.

**Deliverable:** `wrangling.ipynb` – outputs a clean, structured DataFrame.

---

## Data Storage
The cleaned dataset was stored in two formats:

1. **SQLite** (`rankings.db`) – relational storage suitable for structured queries.
2. **Parquet** (`rankings.parquet`) – columnar storage optimized for analytics and large-scale processing.

A validation function confirms data integrity in both formats.

**Deliverable:** `storage.ipynb` – handles storage and verification.

---

## Technical Report
A PDF/Word report summarizes:

- **Data Profile:** Initial and cleaned dataset statistics, including column types, missingness, numeric ranges, and categorical uniqueness.
- **Decision Rationale:** Research problem, hypotheses, objectives, and justifications for all major data wrangling steps.
- **Storage Comparison:** Brief evaluation of SQLite vs. Parquet formats.
- **Challenges:** Issues encountered during data acquisition (web scraping limitations, API restrictions) and data cleaning (handling high missingness with Random Forest imputation).

**Deliverable:** `TechnicalReport.docx`.

---

## Challenges
- **Data Acquisition:** Web scraping required simulating a browser to bypass bot restrictions. APIs were limited and often required authentication or payment.  
- **Data Cleaning:** Some columns had up to 48% missing values, requiring advanced imputation methods. Compatibility issues with Python libraries (e.g., ordinal forests) also arose.
