# EX-05-Feature-Generation

# Aim
To read the given data and perform Feature Generation process and save the data to a file. 

# Explanation
Feature Generation (also known as feature construction, feature extraction or feature engineering) is the process of transforming features into new features that better relate to the target.

# Algorithm
### Step 1
Read the given Data
### Step 2
Clean the Data Set using Data Cleaning Process
### Step 3
Apply Feature Generation techniques to all the feature of the data set
### Step 4
Save the data to the file

# Code
```python
import pandas as pd
from sklearn.preprocessing import OrdinalEncoder,LabelEncoder,MinMaxScaler,Normalizer,OneHotEncoder

df1=pd.read_csv('bmi.csv')
df1
# feature encoding using LabelEncoder
le=LabelEncoder()
df1c=df1.copy()
df1c['gender']=le.fit_transform(df1c['Gender'])
df1c
# feature scaling usign Normalizer
scaler=Normalizer()
df1c[['Height','Weight']]=scaler.fit_transform(df1c[['Height','Weight']])
df1c

df2=pd.read_csv('data.csv')
df2
# feature encoding usign Label Encoder
df2c=df2.copy()
le=LabelEncoder()
df2c['bin_1t']=le.fit_transform(df2c['bin_1'])a
df2c['bin_2t']=le.fit_transform(df2c['bin_2'])
df2c
# feature encoding using One Hot Encoder
ohe=OneHotEncoder(sparse_output=False)
enc=pd.DataFrame(ohe.fit_transform(df2[['City']]))
df2c=pd.concat([df2c,enc],axis=1)
df2c.rename(columns={0:'City_Bangalore',1:'City_Chennai',2:'City_Delhi',3:'City_Mumbai'},inplace=True)
df2c=df2c.drop(columns=['City'])
df2c
# feature encoding using Ordinal Encoder
degree=['High School','Diploma','Bachelors','Masters','PhD']
oe=OrdinalEncoder(categories=[degree])
df2c['ord_2t']=oe.fit_transform(df2[['Ord_2']])
df2c
# feature encoding using Ordinal Encoder
climate=['Cold','Warm','Hot','Very Hot']
oe=OrdinalEncoder(categories=[climate])
df2c['ord_1t']=oe.fit_transform(df2[['Ord_1']])
df2c

df3=pd.read_csv('Encoding Data.csv')
df3
# feature encoding usign Label Encoder
df3c=df3.copy()
le=LabelEncoder()
df3c['bin_1t']=le.fit_transform(df3c['bin_1'])
df3c['bin_2t']=le.fit_transform(df3c['bin_2'])
df3c['nom_0t']=le.fit_transform(df3c['nom_0'])
df3c
# feature encoding using Ordinal Encoder
climate=['Cold','Warm','Hot']
oe=OrdinalEncoder(categories=[climate])
df3c['ord_2t']=oe.fit_transform(df3[['ord_2']])
df3c
```
# Output
### bmi file before feature generation
![image](https://github.com/yasin-sharif-SEC/EX-05-Feature-Generation/assets/142985837/4d3ee3c8-ad02-419d-840a-22f4e50b0913)

### Label Encoder
![image](https://github.com/yasin-sharif-SEC/EX-05-Feature-Generation/assets/142985837/472c2af4-7729-4cae-a93a-b24ffbbf955b)

### Normalizer
![image](https://github.com/yasin-sharif-SEC/EX-05-Feature-Generation/assets/142985837/3b94a58c-e3d8-4d47-b64f-4c6de21f011f)

### data file before feature generation
![image](https://github.com/yasin-sharif-SEC/EX-05-Feature-Generation/assets/142985837/8b9d2319-9bb9-434e-93b7-205f18f4acda)

### Label Encoder
![image](https://github.com/yasin-sharif-SEC/EX-05-Feature-Generation/assets/142985837/9c3925c2-e2d2-459e-9346-fa87127eaced)

### One Hot Encoder
![image](https://github.com/yasin-sharif-SEC/EX-05-Feature-Generation/assets/142985837/32d51d1b-7041-44ca-a48d-d3dbf6b4e4da)

### Ordinal Encoder
![image](https://github.com/yasin-sharif-SEC/EX-05-Feature-Generation/assets/142985837/819c9c0b-e3cf-466e-bca7-27812e239f6d)

### encoding data file
![image](https://github.com/yasin-sharif-SEC/EX-05-Feature-Generation/assets/142985837/599f24ff-d8ba-4180-8e90-287b28fc5c9d)

### Label Encoder
![image](https://github.com/yasin-sharif-SEC/EX-05-Feature-Generation/assets/142985837/d1d05eb6-bf42-4e7b-8cb8-c1aeff270b79)

### Ordinal Encoder
![image](https://github.com/yasin-sharif-SEC/EX-05-Feature-Generation/assets/142985837/852306ad-122b-417d-ae57-4cecb2c1f59a)

# Result
Thus different feature encoding and feature scaling techniques are applied to the data.
