# Biscobis Customer Service Statistical Analysis

## Project Overview

This repository contains a statistical analysis of customer service ratings for Biscobis Ltd. The analysis is based on a survey of 100 customers who rated seven different aspects of the company's services.

## Dataset

The dataset `biscobis-statistical-measures.csv` contains customer ratings for the following categories:

1. Shipping speed
2. Price level
3. Negotiation flexibility
4. Image
5. Services provided
6. Sales force
7. Product quality

## Python Code for Statistical Analysis

This project offers two Python scripts for analyzing the Biscobis customer service data: a concise version for quick analysis and a comprehensive version for detailed insights.

### Concise Python Code for Quick Analysis

## Python Code for Statistical Analysis

This project offers two Python scripts for analyzing the Biscobis customer service data: a concise version for quick analysis and a comprehensive version for detailed insights.

### Concise Python Code for Quick Analysis

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

This concise code quickly calculates and outputs the main statistical measures and is perfect for quick analyses or when you need a rapid overview of the data's statistical properties.


### Comprehensive Python Code for Detailed Analysis

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

This comprehensive code provides detailed statistics and creates visualizations for deeper insights.

## Running the Analysis

To run either version of the code, follow these steps:
1. Ensure you have Python installed on your system.
2. Install the required libraries:
   - For the concise version: `pip install pandas`
   - For the comprehensive version: `pip install pandas numpy scipy matplotlib seaborn`
3. Place the `biscobis-statistical-measures.csv` file in the same directory as the Python script.
4. Run the script using Python.


## Note on Displaying Graphs







