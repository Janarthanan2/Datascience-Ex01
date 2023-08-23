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
# OUTPUT
## DATA1:
![Screenshot 2023-08-23 124329](https://github.com/Janarthanan2/Datascience-Ex01/assets/119393515/6124ddd7-146e-4d0e-b9d0-2e820bae5d04)
### NON NULL BEFORE:
![Screenshot 2023-08-23 150208](https://github.com/Janarthanan2/Datascience-Ex01/assets/119393515/fd1ea313-9283-4995-9600-b8cc4543bb45)
![Screenshot 2023-08-23 150321](https://github.com/Janarthanan2/Datascience-Ex01/assets/119393515/9ec9921d-7114-4e1c-b6c4-2fd8320e86f1)
### NON NULL AFTER:
![Screenshot 2023-08-23 150502](https://github.com/Janarthanan2/Datascience-Ex01/assets/119393515/d7b79a9e-cf7a-4036-8a6d-d988a3744639)
![Screenshot 2023-08-23 150732](https://github.com/Janarthanan2/Datascience-Ex01/assets/119393515/7e515e0a-2458-4c90-9327-6956b4ad3a59)
![Screenshot 2023-08-23 150944](https://github.com/Janarthanan2/Datascience-Ex01/assets/119393515/ecd44637-01d7-423b-b802-8d47974824ae)
![Screenshot 2023-08-23 151004](https://github.com/Janarthanan2/Datascience-Ex01/assets/119393515/5f8c9b79-d2b4-4026-8e43-4be37a08b2fc)
![Screenshot 2023-08-23 151033](https://github.com/Janarthanan2/Datascience-Ex01/assets/119393515/57ca54f1-a86c-497f-8cbc-7bc331698e16)
![Screenshot 2023-08-23 151053](https://github.com/Janarthanan2/Datascience-Ex01/assets/119393515/9a5832b9-69c3-49c8-abe4-105dea925c9f)
### OUTCOME:
![Screenshot 2023-08-23 151204](https://github.com/Janarthanan2/Datascience-Ex01/assets/119393515/593ad16c-da7a-4fe6-9fd5-facee634d2f8)


## DATA2:
![Screenshot 2023-08-23 124543](https://github.com/Janarthanan2/Datascience-Ex01/assets/119393515/92d0f85d-2093-44c5-9eca-ccfb7a3f1927)
### NON NULL BEFORE:
![Screenshot 2023-08-23 150237](https://github.com/Janarthanan2/Datascience-Ex01/assets/119393515/87f7b1e9-4cd5-484c-a119-63c8a627d175)
![Screenshot 2023-08-23 150342](https://github.com/Janarthanan2/Datascience-Ex01/assets/119393515/4ee05570-b0be-4aa9-937e-4b97eec84473)

### NON NULL AFTER:
![Screenshot 2023-08-23 153636](https://github.com/Janarthanan2/Datascience-Ex01/assets/119393515/cca12e81-2b5f-4e78-939b-3b5b5b410f94)
![Screenshot 2023-08-23 153717](https://github.com/Janarthanan2/Datascience-Ex01/assets/119393515/728bee35-4231-40a7-8719-b908bc25e370)
![Screenshot 2023-08-23 153823](https://github.com/Janarthanan2/Datascience-Ex01/assets/119393515/0abd1c0c-07c6-45c0-b2c0-fb9bc2d3df4c)
![Screenshot 2023-08-23 153934](https://github.com/Janarthanan2/Datascience-Ex01/assets/119393515/a991a828-0a4e-424a-b64d-678b8c361a5f)
![Screenshot 2023-08-23 154103](https://github.com/Janarthanan2/Datascience-Ex01/assets/119393515/3d96ef29-b604-47f6-b1dd-3ed9b8f1aac1)

### OUTCOME:
![Screenshot 2023-08-23 154418](https://github.com/Janarthanan2/Datascience-Ex01/assets/119393515/1e6dc7af-1cc8-4d3c-9e0d-baff36e5f1bc)


