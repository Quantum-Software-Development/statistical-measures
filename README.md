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

