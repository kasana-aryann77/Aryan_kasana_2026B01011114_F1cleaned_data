# Formula 1 Drivers Dataset - Data Cleaning Project

## Overview
This project focuses on cleaning and validating a Formula 1 drivers dataset before performing exploratory data analysis (EDA). The dataset contains driver information including names, dates of birth, nationalities, and reference URLs.

---
## Data Source
https://www.kaggle.com/datasets/rohanrao/formula-1-world-championship-1950-2020

## Dataset Information

| Attribute | Description |
|------------|------------|
| driverId | Unique driver identifier |
| driverRef | Driver reference name |
| forename | Driver first name |
| surname | Driver last name |
| dob | Date of birth |
| nationality | Driver nationality |
| url | Wikipedia reference URL |

---

## Tools & Libraries

- Python 3.x
- Pandas
- NumPy
- Jupyter Notebook

---

## Data Cleaning Process

### 1. Initial Data Inspection
Performed an initial examination of the dataset using:

```python
df.head()
df.info()
df.describe()
df.isnull().sum()
```

**Objective**
- Understand dataset structure
- Identify missing values
- Verify data types
- Detect potential inconsistencies

---

### 2. Missing Value Analysis

Checked all columns for missing values:

```python
df.isnull().sum()
```

#### Findings
- Missing values detected primarily in the `dob` column.
- Several records contained incomplete information.

#### Action Taken
Missing DOB values were imputed using the central tendency approach (mean/median date strategy) to retain records and avoid unnecessary data loss.

```python
df['dob'].fillna(imputed_value)
```

---

### 3. Data Type Validation

Verified that all columns were stored using appropriate data types.

| Column | Data Type |
|----------|----------|
| driverId | int64 |
| driverRef | object |
| forename | object |
| surname | object |
| dob | datetime64[ns] |
| nationality | object |
| url | object |

#### Action Taken

Converted DOB to datetime format.

```python
df['dob'] = pd.to_datetime(df['dob'])
```

---

### 4. Duplicate Record Detection

Checked for duplicate records.

```python
df.duplicated().sum()
```

#### Action Taken
Any identified duplicates were reviewed and removed.

```python
df.drop_duplicates(inplace=True)
```

---

### 5. Text Data Cleaning

Performed string cleaning operations.

#### Operations
- Removed leading spaces
- Removed trailing spaces
- Standardized text formatting

```python
df['forename'] = df['forename'].str.strip()
df['surname'] = df['surname'].str.strip()
df['nationality'] = df['nationality'].str.strip()
```

---

### 6. Character Encoding Investigation

Identified character encoding anomalies in driver names.

Examples:

```text
JosÃ© → José
FranÃ§ois → François
AndrÃ© → André
```

Attempted UTF-8 validation and encoding correction procedures during cleaning.

---

### 7. Data Validation

Final quality checks were performed to ensure:

- No unexpected missing values
- Correct datetime formatting
- Consistent column structure
- Valid record counts
- Analysis-ready dataset

```python
df.isnull().sum()
df.info()
df.shape
```

---

## Cleaning Summary

| Task | Status |
|--------|--------|
| Missing Value Treatment | ✅ |
| Data Type Validation | ✅ |
| Date Conversion | ✅ |
| Duplicate Check | ✅ |
| Text Standardization | ✅ |
| Data Quality Verification | ✅ |
| Encoding Review | ✅ |

---

## Final Output

A cleaned and validated Formula 1 drivers dataset ready for:

- Exploratory Data Analysis (EDA)
- Data Visualization
- Statistical Analysis
- Machine Learning Preparation

---

## Conclusion

Data Cleaning & Preparation using Python and Pandas.
