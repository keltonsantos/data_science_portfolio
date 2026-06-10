---
title: "Mining Process Quality Analysis"
date: 2023-11-10
description: "Exploratory data analysis of a flotation plant process to investigate iron concentrate quality and silica levels using Python and Pandas."
tags: ["Python", "Pandas", "Seaborn", "EDA", "Manufacturing", "Data Visualization"]
showTableOfContents: true
#showSummary: false

---

## Overview

Data analysis project for a fictional mining company called **Metals R' Us**, using real-world data from a flotation plant. The goal was to investigate process quality — specifically iron concentrate purity — and identify anomalies in the production data.

**Dataset:** [Kaggle — Quality Prediction in a Mining Process](https://www.kaggle.com/datasets/edumagalhaes/quality-prediction-in-a-mining-process)  
**Notebook:** [View on Deepnote](https://deepnote.com/app/data-analystics-accelerator/Mining-Project-7983f6fd-8b68-4392-811b-e4f6145de140)

---

## Problem statement

The engineering team flagged an anomaly on **June 1, 2017** and needed a data analyst to investigate what happened to the iron concentrate quality on that day. Key variables of interest were:

- % Iron Concentrate ← primary quality metric
- % Silica Concentrate
- Ore Pulp pH
- Flotation Column 05 Level

---

## Dataset

- **Size:** 737,453 rows × 24 columns
- **Source:** Flotation plant sensor readings over time
- **Format:** CSV with comma-decimal notation, timestamped readings

---

## Approach

### 1. Data loading & cleaning
Loaded the dataset with Pandas, handling the European decimal format (`decimal=","`) and converting the date column to proper datetime format.

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

df = pd.read_csv('MiningProcess_Flotation_Plant_Database.csv', decimal=",")
df['date'] = pd.to_datetime(df['date'])
```

### 2. Filtering to the anomaly window
Isolated data around the flagged date to focus the investigation:

```python
df_june = df[
    (df['date'] > "2017-05-31 23:59:59") &
    (df['date'] < "2017-06-02")
].reset_index(drop=True)
```

### 3. Descriptive analytics
Used `df.describe()` to generate summary statistics across all 24 columns and identify unusual ranges in the key variables.

### 4. Correlation analysis
Built a pair plot and correlation matrix to check for relationships between the important variables during the anomaly window.

```python
sns.pairplot(df_june_important)
round(df_june_important.corr(), 2)
```

### 5. Time series visualization
Plotted line charts for each key variable across June 1st to visually identify where the anomaly occurred.

```python
for col in important_cols[1:]:
    sns.lineplot(x='date', y=col, data=df_june)
    plt.show()
```

---

## Key findings

- The correlation matrix showed **low correlation** among the key variables during the anomaly window — ruling out a systemic process shift
- Line charts revealed the specific time windows where % Iron Concentrate deviated from normal operating range
- % Silica Concentrate and Ore Pulp pH remained relatively stable, suggesting the issue was isolated

---

## Skills demonstrated

- Data loading and cleaning with Pandas
- Date filtering and time series slicing
- Descriptive statistics and summary reporting
- Correlation analysis
- Data visualization with Seaborn and Matplotlib
- Communicating findings to a non-technical stakeholder (the boss)

---

## How to run

```bash
# Download the dataset from Kaggle first
pip install pandas matplotlib seaborn
jupyter notebook mining_analysis.ipynb
```
