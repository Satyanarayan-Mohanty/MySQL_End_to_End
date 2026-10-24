# World Layoffs Data Analysis Using MySQL

## Project Overview
This project explores global company layoffs using MySQL. It combines data cleaning and exploratory data analysis (EDA) to prepare the dataset and identify trends in layoffs across companies, industries, countries, and time periods.

## Dataset
- **Source:** [Layoffs 2022 Dataset on Kaggle](https://www.kaggle.com/datasets/swaptr/layoffs-2022)
- **Database:** `world_layoffs`
- **Main table:** `layoffs`
- **Working tables:** `layoffs_staging` and `layoffs_staging2`

## Tools Used
- MySQL
- SQL (CTEs, joins, aggregate functions, window functions)

## Project Workflow

### 1. Data Cleaning
The SQL scripts clean a staging copy of the original dataset rather than modifying the raw table directly.

Key tasks:
- Create staging tables and copy the raw data.
- Identify potential duplicates using `ROW_NUMBER()` and remove duplicate records.
- Standardize company names by trimming extra spaces.
- Standardize industry values, including variations of `Crypto`.
- Standardize country names by removing trailing periods.
- Convert date strings into the `DATE` data type.
- Inspect missing values and convert blank industry values to `NULL`.
- Fill missing industry values when another record for the same company provides a value.
- Remove records where both `total_laid_off` and `percentage_laid_off` are `NULL`.
- Remove the temporary `row_num` column.

### 2. Exploratory Data Analysis (EDA)
The EDA script uses the cleaned staging data to investigate patterns and trends.

Analysis includes:
- Maximum layoffs and maximum/minimum layoff percentages.
- Companies where 100% of employees were laid off.
- Companies with the largest single-day layoffs and highest total layoffs.
- Layoffs by location, country, industry, and company stage.
- Layoffs by year, date, and month.
- Monthly layoffs and cumulative rolling totals.
- Top five companies by layoffs for each year using CTEs and `DENSE_RANK()`.

## SQL Concepts Practiced
- `SELECT`, `WHERE`, `ORDER BY`, and `LIMIT`
- `GROUP BY` and aggregate functions such as `SUM()`, `MIN()`, and `MAX()`
- `JOIN`
- Common Table Expressions (CTEs)
- Window functions: `ROW_NUMBER()`, `DENSE_RANK()`, and `SUM() OVER()`
- Date conversion and string functions such as `STR_TO_DATE()`, `TRIM()`, and `SUBSTRING()`

## Files
- `Data Cleaning using MySQL.sql` — data cleaning and preparation queries.
- `Layoffs_EDA.sql` — exploratory analysis queries.

## How to Run
1. Install and open MySQL Workbench or another MySQL client.
2. Download the dataset from the Kaggle link above and import it into MySQL.
3. Ensure the database is named `world_layoffs` and the raw table is named `layoffs`.
4. Run `Data Cleaning using MySQL.sql` first to create and clean the staging tables.
5. Run `Layoffs_EDA.sql` to perform the analysis on the cleaned data.

## Project Goal
To practice SQL-based data cleaning and analysis and discover how layoffs vary by company, industry, country, and time.

---
*Note: The scripts expect the database and table names shown above. Review the SQL scripts before running them on an existing database, as they include `UPDATE` and `DELETE` statements on staging tables.*
