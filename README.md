# Statistical Measures: Calculation in Excel and Python

## Introduction

Welcome to the "Comprehensive Statistical Analysis of Biscobis Dataset" repository. This repository aims to conduct a detailed statistical analysis of the biscobis-statistical-measures.csv dataset, covering various measures such as mean, median, mode, minimum, maximum, range, variance, standard deviation, and coefficient of variation.

## Project Overview

This repository presents a statistical analysis of customer service ratings for Biscobis Ltd., based on a survey of 100 customers who evaluated seven different aspects of the company's services.

## Setup
To use this repository, ensure you have Python installed on your system along with the Pandas and NumPy libraries. Clone this repository and place your biscobis-statistical-measures.csv file in the root directory.



## Dataset 

### [Click here to download the dataset](dataset/bicobbis-statistical-measures.csv)

The dataset `biscobis-statistical-measures.csv` contains customer ratings for the following categories:

1. Shipping speed
2. Price level
3. Negotiation flexibility
4. Image
5. Services provided
6. Sales force
7. Product quality

## Python Code for Statistical Analysis

This project provides three Python scripts for analyzing Biscobis customer service data: a concise version for quick analysis, a comprehensive script for calculating statistical measures, and a detailed version for in-depth insights..


## Concise Python Code for Quick Analysis

This concise code quickly calculates and outputs the main statistical measures and is perfect for quick analyses or when you need a rapid overview of the data's statistical properties.

```python
import pandas as pd

# Load the dataset
data = pd.read_csv('biscobis-statistical-measures.csv', skiprows=2, encoding='latin1')

# Calculate statistical measures
statistics = data.describe().T
statistics['mode'] = data.mode().iloc[0]
statistics['coefficient_of_variation'] = (statistics['std'] / statistics['mean']) * 100

# Save the results to a CSV file
statistics.to_csv('statistical_measures.csv')

print(statistics)
```

### Comprehensive Python Code for Calculating Statistical Measures

Here is the Python script to calculate a comprehensive set of statistical measures:


```python
import pandas as pd

# Load the dataset
data = pd.read_csv('biscobis-statistical-measures.csv')

# Calculate comprehensive statistics
stats = {
    "Mean": data.mean(),
    "Median": data.median(),
    "Q1": data.quantile(0.25),
    "Q2": data.quantile(0.50),
    "Q3": data.quantile(0.75),
    "Mode": data.mode().iloc[0],  # Simplified mode; first mode only
    "Minimum": data.min(),
    "Maximum": data.max(),
    "Range": data.max() - data.min(),
    "Variance": data.var(),
    "Standard Deviation": data.std(),
    "Coefficient of Variation": data.std() / data.mean()
}
stats_df = pd.DataFrame(stats)

# Format the results for easy Excel import
formatted_stats = stats_df.applymap(lambda x: f"{x:.2f}")
formatted_stats.to_csv('formatted_statistical_data.csv', index=True)
print(formatted_stats)
```


### Comprehensive Python Code for Detailed Analysis

This comprehensive code provides detailed statistics and creates visualizations for deeper insights.

```python
import pandas as pd
import numpy as np
from scipy import stats
import matplotlib.pyplot as plt
import seaborn as sns

def calculate_statistics(data):
    # [Previous statistics calculation remains the same]

# Load the dataset
df = pd.read_csv('biscobis-statistical-measures.csv', skiprows=2, encoding='latin1')

# Calculate statistics for each column
statistics = df.apply(calculate_statistics)

# Transpose the results for better readability
statistics_transposed = statistics.transpose()

# Display and save the results
print(statistics_transposed)
statistics_transposed.to_csv('biscobis_detailed_statistics.csv')

# Create visualizations
plt.figure(figsize=(12, 6))
sns.boxplot(data=df)
plt.title('Distribution of Ratings by Category')
plt.xticks(rotation=45)
plt.tight_layout()
plt.savefig('boxplot_biscobis.png')
plt.show()  # Added to display the boxplot
plt.close()

plt.figure(figsize=(10, 8))
sns.heatmap(df.corr(), annot=True, cmap='coolwarm')
plt.title('Correlation Heatmap of Categories')
plt.tight_layout()
plt.savefig('heatmap_correlation_biscobis.png')
plt.show()  # Added to display the heatmap
plt.close()

def create_histogram(data, column, bins=10):
    plt.figure(figsize=(8, 6))
    sns.histplot(data[column], bins=bins, kde=True)
    plt.title(f'Distribution of {column}')
    plt.xlabel('Value')
    plt.ylabel('Frequency')
    plt.savefig(f'histogram_{column.lower().replace(" ", "_")}.png')
    plt.show()  # Added to display each histogram
    plt.close()

for column in df.columns:
    create_histogram(df, column)

print("Analysis complete. Results saved in CSV and PNG files.")
```


## Running the Analysis

To run either version of the code, follow these steps:
1. Ensure you have Python installed on your system.
2. Install the required libraries:
   - For the concise version: `pip install pandas`
   - For the comprehensive version: `pip install pandas numpy scipy matplotlib seaborn`
3. Place the `biscobis-statistical-measures.csv` file in the same directory as the Python script.
4. Run the script using Python.


## Note on Displaying Graphs

When running the comprehensive analysis script, you will now see the graphs displayed on your screen in addition to having them saved as PNG files. If you're running the script in a non-interactive environment (like a server or automated pipeline), you may want to comment out the plt.show() lines to prevent the script from hanging.








