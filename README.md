# Global Layoffs Data Cleaning

A MySQL data-cleaning project that transforms a raw global layoffs dataset into a consistent, analysis-ready table for later exploration and visualization.

## Project Objective

Prepare the dataset for reliable analysis by removing duplicates, standardizing inconsistent values, resolving missing data where supported, and converting fields into appropriate formats.

## Cleaning Workflow

1. **Created a staging table** to preserve the raw source data.
2. **Identified duplicate rows** with `ROW_NUMBER()` in a CTE.
3. **Removed confirmed duplicates** while retaining one valid record.
4. **Standardized text fields** including company, industry, country, and location values.
5. **Handled blanks and nulls** without inventing unsupported values.
6. **Converted the date column** into a proper SQL date type.
7. **Removed helper columns** after completing validation.
8. **Reviewed the cleaned result** for consistency and analysis readiness.

## Skills Demonstrated

**MySQL · MySQL Workbench · Data Cleaning · CTEs · Window Functions · String Functions · Date Conversion · Null Handling · Data Validation**

## Outcome

The final table provides a cleaner foundation for analyzing layoffs by company, industry, location, funding stage, and time period. This repository focuses on the preparation stage of the analytics workflow; the cleaned data is intended for a separate exploratory analysis or dashboard.

## SQL Walkthrough

### Inspecting and Staging the Source Data

![Reviewing the raw layoffs dataset](https://imgur.com/BDNl1kq.png)

![Creating a staging copy of the layoffs table](https://imgur.com/Dq12Tp5.png)

A staging table protects the original data while cleaning logic is developed and validated.

### Finding and Removing Duplicates

![Identifying duplicates with a row number window function](https://imgur.com/fz1aha2.png)

![Reviewing duplicate records before deletion](https://imgur.com/u9urF6V.png)

`ROW_NUMBER()` partitions the data by the fields that define a repeated record, making duplicate removal traceable.

### Standardizing Values and Dates

![Standardizing company and category values](https://imgur.com/ekBihGl.png)

![Converting text dates into a SQL date type](https://imgur.com/ye12UGr.png)

Text cleanup and date conversion make later grouping, filtering, and time-series analysis more dependable.

### Resolving Missing Values and Finalizing the Table

![Reviewing blank and null values](https://imgur.com/MycLCo2.png)

![Populating supported missing industry values](https://imgur.com/iqco7aA.png)

![Removing rows that cannot support analysis](https://imgur.com/tMcW7rr.png)

![Dropping the temporary duplicate-tracking column](https://imgur.com/da8KYp9.png)

![Reviewing the final cleaned dataset](https://imgur.com/SDgTfjy.png)

Missing values are only populated when another matching record provides defensible information. Temporary cleaning fields are removed after validation.

## Design Decisions

- The raw table is preserved through a staging workflow.
- Duplicate logic is based on the complete business record rather than company name alone.
- Missing values are not replaced with guesses.
- Cleaning and analysis are kept separate so each stage is easier to audit.

## Limitations and Next Steps

- This repository demonstrates data preparation rather than business analysis.
- Findings depend on the completeness and accuracy of the source dataset.
- A logical next step is an exploratory analysis and dashboard covering layoff trends by time, industry, company, location, and funding stage.
