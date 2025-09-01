# Ex.No: 01A PLOT A TIME SERIES DATA
###  Date: 01-09-2025

# AIM:
To Develop a python program to Plot a time series data (population/ market price of a commodity
/temperature.
# ALGORITHM:
1. Import the required packages like pandas and matplot
2. Read the dataset using the pandas
3. Calculate the mean for the respective column.
4. Plot the data according to need and can be altered monthly, or yearly.
5. Display the graph.
# PROGRAM:
```
import matplotlib.pyplot as plt
import seaborn as sns
import numpy as np
import pandas as pd
df = pd.read_csv("/content/House Price Prediction Dataset.csv")
df.head(5)
df.tail(5)
for col in df.columns:
    if df[col].dtype in ['float64', 'int64']:
        df[col] = df[col].fillna(df[col].median())
    else:
        df[col] = df[col].fillna("Unknown")
df = df.sort_values(by='YearBuilt')
df['Date'] = pd.to_datetime(df['YearBuilt'], format='%Y', errors='coerce')
df['Year'] = df['Date'].dt.year

yearly_prices = df.groupby('Year')['Price'].mean()

plt.figure(figsize=(10, 6))
sns.lineplot(x=yearly_prices.index, y=yearly_prices.values, color='red')
plt.title("Average House Price per Year", fontsize=14)
plt.xlabel("Year")
plt.ylabel("Average Price")
plt.show()
```
# OUTPUT:

<img width="818" height="511" alt="image" src="https://github.com/user-attachments/assets/c1043def-6226-459c-84fb-4ff23e9b7cb8" />

# RESULT:
Thus we have created the python code for plotting the time series of given data.
