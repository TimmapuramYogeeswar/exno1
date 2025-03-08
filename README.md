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
df=pd.read_csv("/content/SAMPLEIDS.csv")
df
```
![image](https://github.com/user-attachments/assets/a53da605-5b04-4f1a-8553-3d6acf293ed8)

```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/60db1390-5a4a-4a31-a3dd-819df6d81f53)

```
df.isnull().any()<br>
```
![image](https://github.com/user-attachments/assets/c70b487a-2568-4e15-9281-0195cc659018)

```
df.dropna()
```
![image](https://github.com/user-attachments/assets/c6a9c897-f8e9-4f5f-bd08-6e39fc02ee77)

```
df.fillna(0)
```
![image](https://github.com/user-attachments/assets/7fe07799-b9ec-497d-882b-6a3095381879)
```
df.fillna(method='ffill')
```
![image](https://github.com/user-attachments/assets/5049aa96-dd44-4fa7-83c9-4c5f6336b7dd)
```
df.fillna(method='bfill')
```
![image](https://github.com/user-attachments/assets/47fe3d8d-b0e3-4c6c-ae28-54f9879b805a)
```
df_dropped = df.dropna()
df_dropped
```
![image](https://github.com/user-attachments/assets/574a20dc-2943-4cb4-bd24-258c43cf917a)
```
df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![image](https://github.com/user-attachments/assets/9fbcb790-7098-4157-80e9-fc6804dc646e)
```
ir=pd.read_csv("/content/iris.csv")
ir
```
![image](https://github.com/user-attachments/assets/5a98d20b-e4e8-4f88-824f-a1a58fafe3b3)
```
ir.describe()
```
![image](https://github.com/user-attachments/assets/523574ce-fd08-40ae-bca6-cd123083b3bd)
```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/user-attachments/assets/c8d49d53-ab0f-4817-8a54-3122674393e3)
```
q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
iq=q3-q1
print(q3)
```
![image](https://github.com/user-attachments/assets/3357a83b-62f4-496b-94bd-eb5bfb2f39bf)
```
rid=ir[((ir.sepal_width<(q1-1.5*iq))|(ir.sepal_width>(q3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/fed7867b-0148-4145-8c7e-074fd0cf5d32)

```
delid=ir[~((ir.sepal_width<(q1-1.5*iq))|(ir.sepal_width>(q3+1.5*iq)))]
delid
```
![image](https://github.com/user-attachments/assets/a135b9a6-0a91-452a-bae6-36e6b1d89393)

```
sns.boxplot(x='sepal_width',data=delid)

```
![image](https://github.com/user-attachments/assets/2036e6ec-d23c-433f-9255-1c6523ff8d30)


```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
``

dataset=pd.read_csv("heights.csv")
dataset
```
![image](https://github.com/user-attachments/assets/df85581f-11b2-481c-8bd8-69d146d61e01)

```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
``

iqr = q3-q1
iqr
```
![image](https://github.com/user-attachments/assets/0f3bcc76-07c9-42e7-b62d-863e27b5bf7e)

```
low = q1- 1.5*iqr
low
```
![image](https://github.com/user-attachments/assets/03b006c7-a2bb-47f5-a40d-8f37ec3bef0b)

```
high = q3 + 1.5*iqr
high
```
![image](https://github.com/user-attachments/assets/c05e21ed-e781-4497-90c2-77d5a3e5e11c)

```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```
![image](https://github.com/user-attachments/assets/31c73385-00c2-4981-93f8-581bf021e628)

```
z = np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/user-attachments/assets/85777a09-8864-4b8f-b6cc-94bf2f612a4d)

```
df1 = df[z<3]
df1
```
![image](https://github.com/user-attachments/assets/4333ec52-4b08-42ba-9b64-f9e6cdce933d)

# Result
Thus the given data successfully performed data cleaning and saved the cleaned data to a file.
