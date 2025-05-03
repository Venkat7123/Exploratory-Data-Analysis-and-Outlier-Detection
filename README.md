# Exploratory-Data-Analysis-and-Outlier-Detection
# AIM
To read the given data and perform data analysis and outlier detection using Numpy and Pandas.

# Algorithm
STEP 1: Perform Data cleaning process wherever necessary

STEP 2: Implement Boxplot method to detect outliers

STEP 3: Implement IQR method to Remove Outliers 

STEP 4: Implement Count plot method for univariate analysis

STEP 5: Implement DistPlot method for multivariate analysis

# Coding and Output
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```
```
df = pd.read_csv('/content/IOT-temp (1).csv')
df
```
![image](https://github.com/user-attachments/assets/5cae675c-0612-4929-93c8-20e43e647a0a)

```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/dfe8c859-bfd3-4001-ba05-8febf1073d72)

```
df.noted_date.fillna(method='ffill',inplace=True)
df.isna().sum()
```
![image](https://github.com/user-attachments/assets/3c199160-b808-47bb-bc0b-ce342dc9ede1)

```
df.rename(columns={'out/in':'status'},inplace=True)
df
```
![image](https://github.com/user-attachments/assets/4ca6c690-bdd7-40c0-83e0-d622ea9f50c7)

```
df.dtypes
```
![image](https://github.com/user-attachments/assets/9b6c1678-4d07-4a75-96b6-311536d1901c)

```
df.columns
```
![image](https://github.com/user-attachments/assets/d8d5b1c8-e761-4845-9e39-f32d4dcea590)

```
tp = df.temp.median()
tp
```
![image](https://github.com/user-attachments/assets/c2c14094-297a-42ba-a923-c364e850e55d)

```
df.temp.fillna(tp,inplace=True)
df
```
![image](https://github.com/user-attachments/assets/83a1845a-c481-4758-ac18-fd22cff14b64)

```
df.isna().sum()
```
![image](https://github.com/user-attachments/assets/2c2067c4-d597-440b-86e3-179a907ff831)

```
df.status.fillna(method='bfill',inplace=True)
df.isna().sum()
```
![image](https://github.com/user-attachments/assets/6bd7f269-5bfe-4322-bce3-02087d95b5e0)

```
sns.boxplot(data=df['temp'])
```
![image](https://github.com/user-attachments/assets/51b58538-563b-482b-bea2-d01d6f22c521)

```
sns.boxenplot(data=df['temp'])
```
![image](https://github.com/user-attachments/assets/31d3feb2-ebf6-4ce8-99b6-2c0299f62f91)

```
Q1 = np.percentile(df['temp'],25)
Q3 = np.percentile(df['temp'],75)
IQR = Q3-Q1
IQR
```
![image](https://github.com/user-attachments/assets/ae557d30-22ba-4d51-8c3d-d81168b4876f)

```
LB = Q1-1.5*IQR
HB = Q3+1.5*IQR
```
```
LB
```
![image](https://github.com/user-attachments/assets/bbdbb9d9-c20d-42cd-9fdf-2c10c954c643)

```
HB
```
![image](https://github.com/user-attachments/assets/930cf168-a059-446d-b547-0559ba0a28b8)

```
df = df[((df['temp']>=LB) & (df['temp']<=HB))]
df
```
![image](https://github.com/user-attachments/assets/24ebc5d3-4038-4875-b688-302ee943d974)

```
df.dropna(inplace=True)
sns.boxplot(data=df['temp'])
```
![image](https://github.com/user-attachments/assets/555aa87e-88e2-41cf-aae5-96346d4bed3f)

```
sns.boxenplot(data=df['temp'])
```
![image](https://github.com/user-attachments/assets/7545fd12-8dd3-4d08-937a-89709e958542)

```
sns.countplot(data=df,x='status')
```
![image](https://github.com/user-attachments/assets/cef4eda1-f338-4af2-8b7b-301dc4d5047a)

```
sns.displot(data=df,x='temp',hue='status', kde=True)
```
![image](https://github.com/user-attachments/assets/b30d01c2-344f-453c-99eb-26c0d384a30c)

# Result
Exploratory Data Analysis and Outlier Detection was successfully performed using Python libraries like NumPy, Pandas and the results were verified.
