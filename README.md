```markdown
# 📊 Sentiment Dataset: Data Cleaning & Preprocessing

Welcome to **Task 1** of the Codveda Data Science project! This repository contains the code and documentation for cleaning, standardizing, and preprocessing a raw social media sentiment dataset, making it ready for exploratory data analysis (EDA) and machine learning modeling.

## 📌 Project Overview
The objective of this task is to take a raw, messy dataset containing social media posts and transform it into a clean, structured, and reliable format. The pipeline handles missing values, duplicates, incorrect data types, and inconsistent categorical formatting.

---

## 📂 Dataset Details
- **Original File:** `3) Sentiment dataset.csv`
- **Cleaned File:** `Sentiment_Dataset_Cleaned.csv`
- **Original Shape:** 732 rows × 15 columns
- **Cleaned Shape:** 711 rows × 13 columns

### Features Included:
| Feature | Description |
| :--- | :--- |
| `Text` | The actual social media post content. |
| `Sentiment` | The emotional tone of the post (e.g., Positive, Negative, Joy, etc.). |
| `Timestamp` | Exact date and time of the post. |
| `User` | The username/handle of the poster. |
| `Platform` | Social media platform (Twitter, Instagram, Facebook). |
| `Hashtags` | Tags associated with the post. |
| `Retweets` / `Likes` | Engagement metrics. |
| `Country` | Geographic location of the user. |
| `Year`, `Month`, `Day`, `Hour` | Extracted temporal features for time-series analysis. |

---

## 🛠️ Data Cleaning Pipeline
The following steps were executed in the Jupyter Notebook to clean the data:

1. **Initial Inspection:** Analyzed the dataset shape, columns, data types, and checked for initial missing values and duplicates.
2. **Dropping Unnecessary Columns:** Removed index artifacts (`Unnamed: 0.1`, `Unnamed: 0`) that were carried over from previous CSV exports.
3. **Column Standardization:** Stripped whitespace and converted all column names to lowercase for uniformity.
4. **Datetime Parsing & Feature Extraction:** 
   - Converted the `Timestamp` column to standard `datetime64` objects.
   - Extracted `Year`, `Month`, `Day`, and `Hour` into separate integer columns for easier temporal analysis.
5. **Categorical Standardization:** Applied `.strip()` and `.title()` to `Platform`, `Sentiment`, and `Country` columns to fix casing issues (e.g., converting "usa" to "Usa", "twitter" to "Twitter").
6. **Data Type Correction:** Ensured numerical columns (`Retweets`, `Likes`) and temporal columns (`Year`, `Month`, `Day`, `Hour`) are strictly formatted as `int64`.
7. **Deduplication:** Identified and removed duplicate rows to ensure data integrity (reduced dataset from 732 to 711 rows).

---

## 💻 Tech Stack & Dependencies
- **Language:** Python 3.x
- **Core Library:** `pandas`
- **Environment:** Jupyter Notebook

### Installation
To run this project locally, ensure you have Python installed and install the required dependencies:
```bash
pip install pandas jupyter
```

---

## 🚀 How to Run
1. Clone this repository:
   ```bash
   git clone https://github.com/your-username/codveda-task-1.git
   cd codveda-task-1
   ```
2. Open the Jupyter Notebook:
   ```bash
   jupyter notebook Task_01_codveda.ipynb
   ```
3. Run all cells sequentially. The cleaned dataset will be automatically exported as `Sentiment_Dataset_Cleaned.csv` in your working directory.

---

## 📈 Final Data Quality Check
After executing the pipeline, the final dataset boasts:
- ✅ **0 Missing Values**
- ✅ **0 Duplicate Rows**
- ✅ **Standardized Data Types**
- ✅ **Consistent Categorical Formatting**

---

## 📬 Contact / Author
**Prepared for:** Codveda Task 1  
**Author:** [Towsifa Towa]  
**Date:** [28/8/2026]  

