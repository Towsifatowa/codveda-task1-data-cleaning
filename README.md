markdown
# Codveda Task 1 – Data Cleaning and Preprocessing

## 📌 Project Overview

This project was completed as part of the **Codveda Technologies Data Analysis Internship**.

The objective of this task is to clean and preprocess a **Sentiment Dataset** using Python and Pandas. The dataset contains information related to social media sentiment, including timestamps, platforms, countries, sentiments, retweets, and likes.

The preprocessing workflow focuses on improving data quality, standardizing values, converting data types, handling duplicate records, and preparing the dataset for further analysis.



## 🎯 Objectives

The main objectives of this task are:

- Load the sentiment dataset using Pandas
- Explore the dataset structure
- Check the number of rows and columns
- Inspect column names and data types
- Check for missing values
- Identify duplicate rows
- Remove unnecessary columns
- Standardize column names
- Convert timestamps into a standard datetime format
- Extract Year, Month, Day, and Hour from timestamps
- Standardize categorical values
- Convert numerical columns to appropriate data types
- Remove duplicate records
- Perform a final data quality check
- Save the cleaned dataset as a CSV file



## 🛠️ Tools and Technologies

- **Python**
- **Pandas**
- **Jupyter Notebook**


## 📂 Dataset

The project uses the following dataset:

**Dataset:** `3) Sentiment dataset.csv`

The dataset contains sentiment-related social media information with columns such as:

- Timestamp
- Platform
- Sentiment
- Country
- Retweets
- Likes



## 🔄 Data Cleaning and Preprocessing Workflow

### 1. Import Libraries

The project uses the Pandas library for data loading, manipulation, cleaning, and preprocessing.

python
import pandas as pd


### 2. Load Dataset

The CSV dataset is loaded using Pandas.

python
df = pd.read_csv(r"C:\Users\LENOVO\Downloads\3) Sentiment dataset.csv")


The first five rows are displayed to understand the structure of the dataset.



### 3. Dataset Exploration

The dataset shape is checked to determine the number of rows and columns.

python
print("Shape:", df.shape)


Column names are also displayed:

python
print(df.columns)


The `info()` function is used to inspect:

* Column names
* Data types
* Non-null values
* Dataset structure



### 4. Missing Values and Duplicate Check

Missing values are checked using:

python
df.isnull().sum()


Duplicate rows are identified using:

python
df.duplicated().sum()


This helps assess the initial data quality before preprocessing.



### 5. Remove Unnecessary Columns

A copy of the original dataset is created for cleaning:

python
df_clean = df.copy()


Columns containing `"Unnamed"` are identified and removed because they are unnecessary index-like columns.

python
unnamed_cols = [col for col in df_clean.columns if 'Unnamed' in col]
df_clean = df_clean.drop(columns=unnamed_cols)



### 6. Standardize Column Names

Column names are standardized by:

* Removing extra spaces
* Converting names to lowercase
* Replacing spaces with underscores

python
df.columns = (
    df.columns
    .str.strip()
    .str.lower()
    .str.replace(" ", "_")
)


This makes column names easier to work with during analysis.


### 7. Convert Timestamp

The `Timestamp` column is converted into a standard datetime format.

python
df_clean['Timestamp'] = pd.to_datetime(
    df_clean['Timestamp'],
    errors='coerce'
)


The following time-based features are extracted:

* Year
* Month
* Day
* Hour

python
df_clean['Year']  = df_clean['Timestamp'].dt.year
df_clean['Month'] = df_clean['Timestamp'].dt.month
df_clean['Day']   = df_clean['Timestamp'].dt.day
df_clean['Hour']  = df_clean['Timestamp'].dt.hour

These features can be useful for future time-based sentiment analysis.



### 8. Standardize Categorical Columns

The following categorical columns are standardized:

* Platform
* Sentiment
* Country

Extra spaces are removed and values are converted to title case.

Example:

python
df_clean['Platform'] = df_clean['Platform'].str.strip().str.title()


The same process is applied to the `Sentiment` and `Country` columns.

Value counts are then checked to verify the standardized categories.


### 9. Convert Data Types

The `Retweets` and `Likes` columns are converted into integer data types.

```python
df_clean['Retweets'] = pd.to_numeric(
    df_clean['Retweets'],
    errors='coerce'
).astype(int)

df_clean['Likes'] = pd.to_numeric(
    df_clean['Likes'],
    errors='coerce'
).astype(int)
```

The extracted time features are also converted into integer data types:

```python
for col in ['Year', 'Month', 'Day', 'Hour']:
    df_clean[col] = df_clean[col].astype(int)
```



### 10. Remove Duplicate Rows

Duplicate records are removed after cleaning and standardization.

```python
df_clean = df_clean.drop_duplicates()
```

The dataset is then checked again to confirm that duplicate rows have been removed.



### 11. Final Data Quality Check

A final quality check is performed by comparing the original and cleaned datasets.

The following are checked:

* Original dataset shape
* Cleaned dataset shape
* Total missing values
* Remaining duplicate rows
* Sample of the cleaned dataset

```python
print("Original shape :", df.shape)
print("Cleaned shape  :", df_clean.shape)
print("Missing values :", df_clean.isnull().sum().sum())
print("Duplicates     :", df_clean.duplicated().sum())
```



## 💾 Output

After completing the cleaning and preprocessing steps, the cleaned dataset is saved as:

**`Sentiment_Dataset_Cleaned.csv`**

The cleaned file is saved without the Pandas index:

```python
df_clean.to_csv("Sentiment_Dataset_Cleaned.csv", index=False)
```



## 📊 Data Quality Improvements

The preprocessing workflow improves the dataset by:

| Data Quality Issue                  | Action Taken                             |
| ----------------------------------- | ---------------------------------------- |
| Unnecessary columns                 | Removed `Unnamed` columns                |
| Inconsistent column names           | Standardized column names                |
| Timestamp format                    | Converted to datetime                    |
| Timestamp information               | Extracted Year, Month, Day, Hour         |
| Extra spaces in categories          | Removed                                  |
| Inconsistent categorical formatting | Converted to title case                  |
| Numerical data types                | Converted Retweets and Likes to integers |
| Duplicate records                   | Removed                                  |
| Final data quality                  | Verified after preprocessing             |

---

## 📁 Project Structure

```text
Codveda-Task-1/
│
├── Task_1_Data_Cleaning.ipynb
├── 3) Sentiment dataset.csv
├── Sentiment_Dataset_Cleaned.csv
└── README.md
```



## 🚀 Conclusion

This project demonstrates a basic **data cleaning and preprocessing workflow** using Python and Pandas.

The raw sentiment dataset was explored, cleaned, standardized, and transformed into a more structured format. Duplicate records and unnecessary columns were removed, categorical values were standardized, timestamps were converted and decomposed into useful time-based features, and numerical columns were converted to appropriate data types.

The resulting cleaned dataset is now better prepared for **exploratory data analysis, visualization, and further sentiment analysis**.



## 👩‍💻 Author

**Towsifa Towa**

Data Analyst Intern
Codveda Technologies

