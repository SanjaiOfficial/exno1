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

# DATA CLEANING

CODING

```
import pandas as pd
df=pd.read_csv("SAMPLEIDS.csv")
df
```
![Screenshot 2024-08-22 075459](https://github.com/user-attachments/assets/d2930715-d011-4ffc-942b-b1e59e8e425e)
```
df.isnull().sum()
```
![Screenshot 2024-08-22 075517](https://github.com/user-attachments/assets/91f29c5e-2179-4875-a364-358ee40ebfdb)
```
df.isnull().any()
```
![image](https://github.com/user-attachments/assets/9f388835-cb57-4887-9e90-8c7dbfe7d372)

```
df.dropna()
```
![Screenshot 2024-08-22 075624](https://github.com/user-attachments/assets/50c55050-acb5-4e22-83e4-798b7d0f0d57)

```
df.fillna(0)
```
![image](https://github.com/user-attachments/assets/c004d1e3-7662-4bd5-ab56-049e0b93fe7c)

```
df.fillna(method='ffill')
```
![image](https://github.com/user-attachments/assets/9ca091f1-bfdb-425c-b51e-616703832e9d)
```
df.fillna(method='bfill')
```
![image](https://github.com/user-attachments/assets/e4d2915c-2242-414c-b818-04a60302b84e)
```
df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![image](https://github.com/user-attachments/assets/b9fe0f38-7613-4bd3-87e1-2a62d200286c)

# IQR(Inter Quartile Range)

```
import pandas as pd
ir=pd.read_csv('iris.csv')
ir

```
![image](https://github.com/user-attachments/assets/0ea2733b-c26c-4b64-a561-befedf2de87e)
```
ir.describe()
```
![image](https://github.com/user-attachments/assets/e079dab3-03b2-4714-9461-fbcb1d6cc139)
```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/user-attachments/assets/d6928a07-3273-4404-a1a8-98d39e3ea20c)
```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![image](https://github.com/user-attachments/assets/6ccfb346-d8cc-4bd5-b270-c18ae5a85c90)
```
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/4812b9c2-b609-439d-978c-a374399a1e5e)
```
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```
![image](https://github.com/user-attachments/assets/e92e7a96-3fe2-4705-8e32-b9ce9dd472ff)
```
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/user-attachments/assets/4a3ce094-6d92-415f-9809-a045a37200de)

# Z-Score


```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
dataset=pd.read_csv("heights.csv")
dataset
```
![image](https://github.com/user-attachments/assets/51040ee2-a06f-4f16-b21b-638908324ece)
```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
iqr = q3-q1
iqr
```
![image](https://github.com/user-attachments/assets/e9363b83-3055-42b0-9f49-ecf3d8b868c4)

```
iqr = q3-q1
iqr
```
![image](https://github.com/user-attachments/assets/65f2bf1b-134d-4f3f-ae43-d620f4d869f3)
```
low = q1 - 1.5*iqr
low
```
![image](https://github.com/user-attachments/assets/76ae3e9a-9b1e-483e-a7ad-f68ad5b50b10)

```
high = q3 + 1.5*iqr
high
```
![image](https://github.com/user-attachments/assets/f5153b35-b62d-41e6-93f0-b8468ab5de1f)
```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```
![image](https://github.com/user-attachments/assets/b230d5a6-339c-4e13-b586-021e755033f2)

```
z = np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/user-attachments/assets/bebf5468-c3a1-4bf6-a4ab-8744672b08b9)

```
df1 = df[z<3]
df1
```
![image](https://github.com/user-attachments/assets/a71e30af-3d53-4f99-bb34-5456a19609ce)



            








# Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method
