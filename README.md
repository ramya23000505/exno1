### Name: RAMYA R
### Register Number: 212223230169

# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
```
import pandas as pd
data = pd.read_csv("SAMPLEIDS.csv")
data
```
![image](https://github.com/user-attachments/assets/f09ee14c-9f12-46b1-957f-8280f018f7a6)
```
data.head(7)
```
![image](https://github.com/user-attachments/assets/280641dc-a6dc-4473-b279-23cf87fbc7d9)
```
data.tail(7)
```
![image](https://github.com/user-attachments/assets/2813cc5f-449f-4ca6-9ff3-d32948a43100)
```
data.isnull().sum()
```
![image](https://github.com/user-attachments/assets/91e5065a-11fd-4c1b-9154-d617e4a967fa)
```
data.isnull().any()
```
![image](https://github.com/user-attachments/assets/6ca2ea4b-a85d-4449-89d6-b20f1be623aa)
```
data.dropna()
```
![image](https://github.com/user-attachments/assets/abffee64-389e-4588-9dcb-117cbab11ec9)
```
data.fillna(1000)
```
![image](https://github.com/user-attachments/assets/515cd3d4-234f-4309-8dd8-9fc45a8b82e9)
```
data.fillna(method='ffill')
```
![image](https://github.com/user-attachments/assets/0ad49fe5-9c6f-4469-8a83-65607c63932d)

```
data.fillna(method='bfill')
```
![image](https://github.com/user-attachments/assets/a75eb942-8718-40a1-b3bf-6ab7cee6bc40)
```
data_dropped = data.dropna()
data_dropped
```
![image](https://github.com/user-attachments/assets/c18d4130-d798-4121-9e06-ef9a002b7b56)
```
 data.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![image](https://github.com/user-attachments/assets/e40a13ec-c3bc-498f-8365-298d82f1b5a2)

###  IQR(Inter Quartile Range)
```
ir=pd.read_csv('iris.csv')
ir
```
![image](https://github.com/user-attachments/assets/0c3913db-6d8c-4d86-b481-eb1de23da4aa)
```
ir.describe()
```
![image](https://github.com/user-attachments/assets/f448db82-071e-4f6f-9293-a2661b895364)
```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/user-attachments/assets/e35fa4a9-136b-4dc4-bece-b5a30c0d1974)
```
 q1=ir.sepal_width.quantile(0.25)
 q3=ir.sepal_width.quantile(0.75)
 iq=q3-q1
 print(iq)
```
0.5
```
 rid=ir[((ir.sepal_width<(q1-1.5*iq))|(ir.sepal_width>(q3+1.5*iq)))]
 rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/1e82e5c6-2d6f-455e-99c3-2bfcdd6ca417)
```
delid=ir[~((ir.sepal_width<(q1-1.5*iq))|(ir.sepal_width>(q3+1.5*iq)))]
delid
```
![image](https://github.com/user-attachments/assets/aeca96d0-a085-4758-9e8e-8e2fab87e87c)
```
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/user-attachments/assets/17de4101-e1a0-41de-9663-b324e0a575f1)

###  Z-Score
```
import matplotlib.pyplot as plt
import numpy as np
import scipy.stats as stats
```
```
dataset=pd.read_csv("heights.csv")
dataset
```
![image](https://github.com/user-attachments/assets/c08df31a-3496-45a6-aae7-de1ac43cf14f)
```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
```
```
iqr = q3-q1
iqr
```
0.9249999999999998
```
low = q1- 1.5*iqr
low
```
3.8625000000000003
```
high = q3 + 1.5*iqr
high
```
7.5625
```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```
![image](https://github.com/user-attachments/assets/930c66b6-a0a4-4cc0-9b54-d54747c929ad)
```
z = np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/user-attachments/assets/829ebd39-2d7b-4e3d-9eb9-325de6d4c481)
```
df1 = df[z<3]
df1
```
![image](https://github.com/user-attachments/assets/bd17fd9e-03bb-4770-bfcc-f5e948f32874)

# Result
          <<include your Result here>>
