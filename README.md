

```markdown
# Task 1: Data Cleaning and Preprocessing

**Codveda Technologies — Data Analyst Internship**

This repository contains **Task 1** of the Codveda Data Analyst internship: cleaning and preprocessing a social-media sentiment dataset so it is accurate, consistent, and ready for analysis.

---

## Overview

The raw dataset contains social media posts with sentiment labels, timestamps, users, platforms, hashtags, engagement metrics, and country information.

The original file had extra index columns, inconsistent text (extra spaces, mixed casing), float-typed counts, and duplicate rows after standardization. This notebook inspects data quality, applies a cleaning pipeline, and exports a cleaned CSV for further analysis.

| Metric | Before | After |
| --- | --- | --- |
| Rows | 732 | 711 |
| Columns | 15 | 13 |
| Missing values | 0 | 0 |
| Duplicate rows | 0 (raw) | 0 (after cleaning) |

---

## Dataset

**Source file:** `3) Sentiment dataset.csv`

| Column | Description |
| --- | --- |
| `Text` | Post content |
| `Sentiment` | Sentiment / emotion label |
| `Timestamp` | Date and time of the post |
| `User` | Username |
| `Platform` | Social platform (`Twitter`, `Instagram`, `Facebook`) |
| `Hashtags` | Hashtags used in the post |
| `Retweets` | Retweet / share count |
| `Likes` | Like count |
| `Country` | Country of the user |
| `Year`, `Month`, `Day`, `Hour` | Time parts extracted from `Timestamp` |

Two unused index columns (`Unnamed: 0.1`, `Unnamed: 0`) were dropped.

### After cleaning — key distributions

**Platform**

| Platform | Posts |
| --- | ---: |
| Instagram | 258 |
| Twitter | 243 |
| Facebook | 231 |

**Top countries**

| Country | Posts |
| --- | ---: |
| USA | 188 |
| UK | 143 |
| Canada | 135 |
| Australia | 75 |
| India | 70 |

Sentiment has **191 unique labels** after stripping whitespace and applying title case (e.g. Positive, Joy, Excitement, Contentment, Neutral).

---

## Cleaning Pipeline

1. **Load and inspect**  
   Shape, column names, data types, missing values, and duplicates.

2. **Drop unused columns**  
   Remove `Unnamed: 0` and `Unnamed: 0.1`.

3. **Standardize column names**  
   Strip spaces, convert to lowercase, replace spaces with underscores.

4. **Parse timestamps**  
   Convert `Timestamp` to datetime and re-extract `Year`, `Month`, `Day`, and `Hour`.

5. **Standardize categorical text**  
   Strip extra spaces and apply title case to `Platform`, `Sentiment`, and `Country` (e.g. `usa` → `Usa`).

6. **Fix data types**  
   Convert `Retweets` and `Likes` from float to integer. Keep date parts as integers.

7. **Remove duplicates**  
   Drop duplicate rows that appear after standardization.

8. **Final quality check**  
   Confirm no missing values, no duplicates, and a consistent schema.

9. **Export**  
   Save the cleaned file as `Sentiment_Dataset_Cleaned.csv`.

---

## Project Structure

```text
├── Task_01_codveda.ipynb              # Cleaning notebook
├── 3) Sentiment dataset.csv           # Original dataset
├── Sentiment_Dataset_Cleaned.csv      # Cleaned output
└── README.md
```

---

## Tools

- **Python 3**
- **pandas** — loading, cleaning, type conversion, and export
- **Jupyter Notebook** — exploration, documentation, and quality checks

---

## How to Run

1. Clone the repository:

```bash
git clone https://github.com/<your-username>/<your-repo>.git
cd <your-repo>
```

2. Install pandas (if needed):

```bash
pip install pandas jupyter
```

3. Open the notebook:

```bash
jupyter notebook Task_01_codveda.ipynb
```

4. Update the CSV path in the load cell if your file is in a different location, then run all cells.

The cleaned dataset is written to:

```text
Sentiment_Dataset_Cleaned.csv
```

---

## Results

- Removed 2 unused index columns  
- Standardized platform, sentiment, and country labels  
- Converted timestamps and engagement counts to proper types  
- Removed 21 duplicate rows after cleaning (`732 → 711`)  
- Final dataset: **711 rows × 13 columns**, 0 missing values, 0 duplicates  

The cleaned file is ready for exploratory analysis, dashboards, and reporting.

---

## Author

**[Towsifa Towa]**  
Codveda Technologies — Data Analyst Intern  

---

## License

This project is for internship / educational use.
```

Replace `<your-username>`, `<your-repo>`, `[Your Name]`, and the notebook filename with your real details before you push.
