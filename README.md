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

<img width="1071" height="892" alt="Screenshot 2025-09-05 225827" src="https://github.com/user-attachments/assets/d452259f-8336-42b7-abd4-8c6d06854fe0" />

```
df.head()
```

<img width="1038" height="253" alt="Screenshot 2025-09-05 225917" src="https://github.com/user-attachments/assets/8484f0bb-ef37-4c62-8b1a-4b3fb491883c" />

```
df.tail()
```

<img width="1058" height="248" alt="Screenshot 2025-09-05 230003" src="https://github.com/user-attachments/assets/1f11b0c3-2dec-43f9-b5c2-09cd1197d0b8" />

 ```
df.isnull()
```

<img width="875" height="868" alt="Screenshot 2025-09-05 230057" src="https://github.com/user-attachments/assets/196880f9-572f-4ba8-b3ae-e06ee9a434d4" />

```
df.notnull()
```

<img width="1056" height="868" alt="Screenshot 2025-09-05 230148" src="https://github.com/user-attachments/assets/6d553314-5215-4598-ac97-4e0a4664b99a" />

```
df.isnull().sum()
```

<img width="322" height="568" alt="Screenshot 2025-09-05 230221" src="https://github.com/user-attachments/assets/aa6aee69-5a75-4f6b-9bdd-bcfb0db2bba1" />

```
df.isnull().any()
```

<img width="323" height="573" alt="Screenshot 2025-09-05 230312" src="https://github.com/user-attachments/assets/3fecbac8-88ab-44ba-80af-f1ae6d3f54db" />

```
df.dropna(axis=0)
```

<img width="1099" height="559" alt="Screenshot 2025-09-05 230404" src="https://github.com/user-attachments/assets/a53bafa3-3318-41a9-9bb3-ab8328760ae2" />

```
df.dropna(axis=1)
```

<img width="461" height="870" alt="Screenshot 2025-09-05 230455" src="https://github.com/user-attachments/assets/ed0ce720-8995-4320-bbf7-3af5b76bf24c" />

```
df.fillna({'GENDER' : 'MALE' ,'ADDRESS': 'KANCHIPURAM'})
```

<img width="1101" height="867" alt="Screenshot 2025-09-05 230620" src="https://github.com/user-attachments/assets/05e2c778-9025-4903-a8e2-58209b6c9b6a" />

```
ir=pd.read_csv("/content/iris.csv")
ir
```

<img width="778" height="525" alt="Screenshot 2025-09-05 230709" src="https://github.com/user-attachments/assets/db8128a8-a572-40d8-ba91-3a5ed78f35b8" />

```
import seaborn as sns
sns.boxplot (x='sepal_width',data=ir)
```

<img width="914" height="582" alt="Screenshot 2025-09-05 230750" src="https://github.com/user-attachments/assets/c787b6e1-f77e-47a6-b538-56c4c0609020" />

```
Q1=ir.sepal_width.quantile(0.25)
Q3=ir.sepal_width.quantile(0.75)
IQR=Q3-Q1
print(IQR)
```

<img width="61" height="48" alt="Screenshot 2025-09-05 230835" src="https://github.com/user-attachments/assets/21ce73e7-3442-4274-9e36-cc9f6e530d3f" />

```
ran=ir[((ir.sepal_width<(Q1-1.5*IQR))|(ir.sepal_width>(Q3+1.5*IQR)))]
ran['sepal_width']
```


<img width="286" height="264" alt="Screenshot 2025-09-05 230916" src="https://github.com/user-attachments/assets/f45dc24e-7f58-46f1-b7bf-f07c4cf49148" />

```
ran=ir[~((ir.sepal_width<(Q1-1.5*IQR))|(ir.sepal_width>(Q3+1.5*IQR)))]
ran['sepal_width']
```


<img width="403" height="562" alt="Screenshot 2025-09-05 231044" src="https://github.com/user-attachments/assets/84135dcd-e699-4c7f-9a62-97a11d7a0acf" />

```
sns.boxplot(x='sepal_width',data=ran)
```

<img width="805" height="583" alt="Screenshot 2025-09-05 231143" src="https://github.com/user-attachments/assets/5f343112-8949-428b-a4dd-497eed34dd20" />

```
import numpy as np
import scipy.stats as stats
```
```
z=np.abs(stats.zscore(ir['petal_length']))
z
```

<img width="756" height="672" alt="Screenshot 2025-09-05 231307" src="https://github.com/user-attachments/assets/8b8d79b1-f3c4-4baa-b9d8-3a8996c40d16" />

```
ir1=ir[z<3]
ir1
```

<img width="873" height="556" alt="Screenshot 2025-09-05 231339" src="https://github.com/user-attachments/assets/854b7fac-c855-4a93-a68b-2973f76ad48b" />


# Result
Thus the given data successfully performed data cleaning and saved the cleaned data to a file.
