###Name : MUHAMMAD ASJAD E
###Register No: 212225240091
###Date: 28.10.2026

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
df= pd.read_csv("/content/SAMPLEIDS (3).csv")
df
```


<img width="698" height="557" alt="image" src="https://github.com/user-attachments/assets/be26d84b-c5f0-497a-a3cf-f5edfec06dbb" />


```
df.head()
```
<img width="616" height="177" alt="image" src="https://github.com/user-attachments/assets/08b285b5-3478-465f-91f7-9841a4882858" />


```
df.tail()
```
<img width="625" height="193" alt="image" src="https://github.com/user-attachments/assets/23a296e9-6a52-49f1-b541-591b5fd35482" />


```
df.head(6)
```

<img width="610" height="195" alt="image" src="https://github.com/user-attachments/assets/5a4c75d8-51a3-40ab-bb9b-047ffa48056d" />


```
df.tail(7)
```

<img width="637" height="210" alt="image" src="https://github.com/user-attachments/assets/e0242ce2-1a59-4f88-bdd2-9d296abfd9da" />



```
df.shape
```

<img width="195" height="61" alt="image" src="https://github.com/user-attachments/assets/a43512f2-537a-455f-b6d2-ae84a6c0b1cd" />


```
df.info()
```



<img width="331" height="281" alt="image" src="https://github.com/user-attachments/assets/740b4986-bd6c-4005-ae1c-f0e48acf8214" />



```
df.describe()
```

<img width="588" height="216" alt="image" src="https://github.com/user-attachments/assets/3c479e84-b49f-4a16-856f-26a5a4b3cdf0" />


```
df.isnull()
```

<img width="537" height="557" alt="image" src="https://github.com/user-attachments/assets/527e8916-90ff-4f8c-a9e2-d48faaf8b44a" />


```
df.notnull()
```

<img width="532" height="518" alt="image" src="https://github.com/user-attachments/assets/acebf21b-7ba9-4dc3-936c-2e82e887e718" />


```
df.isnull().sum()
```

<img width="185" height="336" alt="image" src="https://github.com/user-attachments/assets/376a9c65-b425-41f4-8699-61bf124cefac" />


```
df.isnull().any()
```

<img width="232" height="347" alt="image" src="https://github.com/user-attachments/assets/46ffce12-d834-451e-a80b-b50730c8d345" />


```
df.dropna()
```

<img width="638" height="347" alt="image" src="https://github.com/user-attachments/assets/7410b1c0-86fc-4016-a2af-fa6ee5049d87" />


```
df.dropna(axis=1)
```

<img width="242" height="517" alt="image" src="https://github.com/user-attachments/assets/fbb26db7-1c97-48e4-88a3-c92096d3c950" />


```
df.fillna(9)
```

<img width="653" height="535" alt="image" src="https://github.com/user-attachments/assets/fe206610-b705-48c0-8878-0c0790796cc8" />



```
df.fillna(method='ffill')
```

<img width="646" height="535" alt="image" src="https://github.com/user-attachments/assets/233470b7-2fa3-40f9-a4c5-40ab8aa471d6" />


```
df.fillna(method='bfill')
```

<img width="667" height="535" alt="image" src="https://github.com/user-attachments/assets/4b583710-1053-401c-9716-fd2941afc377" />


```
df.fillna({'GENDER':'FEMALE', 'NAME' : 'ANU'})
```

<img width="708" height="537" alt="image" src="https://github.com/user-attachments/assets/fb583c5f-84c1-4f3f-8042-d17991009d9f" />


```
ir = pd.read_csv("/content/iris.csv")
ir
```

<img width="438" height="315" alt="image" src="https://github.com/user-attachments/assets/b7dcc027-9a20-41a8-aca2-523fadfe4c6f" />



```
ir.isnull()
```

<img width="465" height="322" alt="image" src="https://github.com/user-attachments/assets/9c406a7b-e9cb-422d-9653-a1b8c517fd2c" />


```
ir.isnull().sum()
```

<img width="191" height="176" alt="image" src="https://github.com/user-attachments/assets/960be88f-f5d7-4770-9d30-d97a25825790" />


```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```

<img width="466" height="351" alt="image" src="https://github.com/user-attachments/assets/134efb7a-2d52-4061-956b-bf1a632f7a11" />


```
sns.boxplot(x='sepal_length', data=ir)
```

<img width="546" height="373" alt="image" src="https://github.com/user-attachments/assets/27c5878b-4851-41d7-ab86-9b0e268c68b0" />



```
Q1 = ir.sepal_width.quantile(0.25)
Q3 = ir.sepal_width.quantile(0.75)
(IQR) = Q3-Q1 
print(IQR)
```

<img width="286" height="85" alt="image" src="https://github.com/user-attachments/assets/4fd7b028-0c98-4112-9494-cbc1f131a2f3" />



```
ran = ir[((ir.sepal_width <(Q1-1.5*IQR)) | (ir.sepal_width > (Q3 + 1.5 * IQR)))]
ran['sepal_width']
```

<img width="565" height="162" alt="image" src="https://github.com/user-attachments/assets/d1e2c514-bdf7-4fa0-9e12-306dd3392cb3" />



```
ran = ir[~((ir.sepal_width <(Q1-1.5*IQR)) | (ir.sepal_width > (Q3 + 1.5 * IQR)))]
ran['sepal_width']
```


<img width="637" height="346" alt="image" src="https://github.com/user-attachments/assets/e05df5d6-2a89-4ed0-b205-1c3f9f2d254e" />



```
import numpy as np
import scipy.stats as stats

z= np.abs(stats.zscore(ir['petal_length']))
z
```

<img width="461" height="462" alt="image" src="https://github.com/user-attachments/assets/c4e0f8fe-4ca4-4b05-a32f-9034fb821f47" />



```
ir1 =ir[z<3]       
ir1
```


<img width="487" height="323" alt="image" src="https://github.com/user-attachments/assets/c4502cee-46f1-4739-927a-0d21b528f0c9" />





            
# Result
          Hence the data was cleaned , outliers were detected and removed.
