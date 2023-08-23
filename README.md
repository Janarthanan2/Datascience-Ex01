# Ex-01_DS_Data_Cleansing


## AIM
To read the given data and perform data cleaning and save the cleaned data to a file. 

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. 
Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information. 

# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Get the information about the data
### STEP 3
Remove the null values from the data
### STEP 4
Save the Clean data to the file

# CODE and OUTPUT
### PROGRAM1:
```
import numpy as np
import pandas as pd
import seaborn as sns
df=pd.read_csv("/content/Data_set (1).csv")
print(df.info())
df.head(10)
df.shape
print(df.describe())

'''Reason: Aired on is not a sensitive data , since, it may aired on some other days in the week.'''
df['aired_on'] = df['show_name'].fillna(df['aired_on'].mode()[0])
print(df.isnull().sum())

'''Reason: Assuming that network may used the top.'''
df['original_network'] = df['original_network'].fillna(df['original_network'].mode()[0])
df.head(5)
print(df.isnull().sum())

'''Reason: Assuming that watchers may watched the shows. '''
df['watchers'] = df['watchers'].fillna(df['watchers'].median())
df.head(5)
print(df.isnull().sum())

'''Reason: Mostly the rating will be average'''
df['rating'] = df['rating'].fillna(df['rating'].mean())
df.head(5)
print(df.isnull().sum())

'''Reason: Showname has unique names for every data. So We have to drop the values '''
df = df.dropna(subset=['show_name'])
df.head(5)
print(df.isnull().sum())

'''Reason: The show is not in the overall rank list.'''
df = df.dropna(subset=['current_overall_rank'])
df.head(5)
print(df.isnull().sum())

print(df.info())
print(df.describe())

```
### PROGRAM2:
```
import pandas as pd
import numpy as np
import seaborn as sns
df=pd.read_csv("/content/Loan_data.csv")
df.describe()
df.info()
df.isnull().sum()

'''Reason: Gender cannot be replaced.'''
df = df.dropna(subset="Gender")
df.head(5)

'''Reason: Gender cannot be replaced.'''
df = df.dropna(subset="Gender")
df.head(5)
df.isnull().sum()

'''Reason: The dependents are most important in loan data. So, it should be removed.'''
df = df.dropna(subset=["Dependents"])
df.isnull().sum()

'''Reason: Most probably bank allocate loan for employed'''
df['Self_Employed'] = df['Self_Employed'].fillna(df['Self_Employed'].mode()[0])
df.head(5)
df.isnull().sum()

'''Reason: Bank will allot loan amount for a person according to its credits '''
df['LoanAmount'] = df['LoanAmount'].fillna(df['LoanAmount'].mean())
df.head(5)
df.isnull().sum()

'''Reason: Loan amount term will most probably same.'''
df['Loan_Amount_Term'] = df['Loan_Amount_Term'].fillna(df['Loan_Amount_Term'].median())
df.head(5)
df.isnull().sum()
```
