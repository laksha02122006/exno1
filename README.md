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

import pandas as pd
df=pd.read_csv("/content/iris.csv")
df

 <img width="810" height="630" alt="image" src="https://github.com/user-attachments/assets/c1eb1868-29e5-4be5-8e2f-6050324fd38c" />
 
df.head()

<img width="755" height="313" alt="image" src="https://github.com/user-attachments/assets/3350eab1-3706-492a-a2ed-94c94ddbb07b" />

df.tail()

<img width="811" height="323" alt="image" src="https://github.com/user-attachments/assets/0051429d-0331-455e-957f-27f3ae7639a9" />

df.isnull()

<img width="753" height="588" alt="image" src="https://github.com/user-attachments/assets/48b85670-5be9-468c-a255-161c1fde9895" />  

df.dropna(axis=0)

<img width="819" height="573" alt="image" src="https://github.com/user-attachments/assets/e0cc5cd8-2e2d-4281-bfaf-2c259f6357cc" />

df.dropna(axis=1)

<img width="794" height="597" alt="image" src="https://github.com/user-attachments/assets/a9494fa1-8e96-4eea-b552-fe2baf8716e7" />

df.fillna(0)

<img width="787" height="581" alt="image" src="https://github.com/user-attachments/assets/378d5834-ca58-4442-a89e-3a35fc797e3e" />

df_dropped=df.dropna()
df_dropped

<img width="804" height="599" alt="image" src="https://github.com/user-attachments/assets/1a0da5e9-7a05-4017-bf99-5f89281e57e2" />

import seaborn as sns
suren=pd.read_csv('/content/iris.csv')
df

<img width="773" height="641" alt="image" src="https://github.com/user-attachments/assets/780b84a7-e611-445f-a317-2373001a438b" />

df.describe()

<img width="757" height="440" alt="image" src="https://github.com/user-attachments/assets/75f48dd5-5425-4fd3-bf95-29397075e3ed" />

sns.boxplot(x='sepal_width',data=df)

<img width="748" height="635" alt="image" src="https://github.com/user-attachments/assets/5d4cfa0d-ccd9-43c3-a712-9945f6abb05f" />

q1=df.sepal_width.quantile(0.25)
q3=df.sepal_width.quantile(0.75)
iqr=q3-q1
print(iqr)


rid=df[((df.sepal_width<(q1-1.5*iqr))|(df.sepal_width>(q3+1.5*iqr)))]
rid['sepal_width']

<img width="761" height="522" alt="image" src="https://github.com/user-attachments/assets/5d98d9e0-257a-4f70-a9e3-945f51884e91" />

delid=df[~((df.sepal_width<(q1-1.5*iqr))|(df.sepal_width>(q3+1.5*iqr)))]
delid

<img width="756" height="604" alt="image" src="https://github.com/user-attachments/assets/fbe71434-7159-43d0-bd76-9b960cd60451" />

sns.boxplot(x='sepal_width',data=delid)

<img width="741" height="653" alt="image" src="https://github.com/user-attachments/assets/1397d7f3-3200-4f25-b142-88d764893c39" />

import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats

dataset=pd.read_csv("/content/heights.csv")
dataset

<img width="474" height="783" alt="image" src="https://github.com/user-attachments/assets/f7bfb375-0129-4f73-9b3b-e3024f697ec3" />

df=pd.read_csv("/content/heights.csv")
q1=df['height'].quantile(0.25)
q2=df['height'].quantile(0.5)
q3=df['height'].quantile(0.75)


iqr=q3-q1
iqr

low=q1-1.5*iqr
low

high=q3+1.5*iqr
high

<img width="487" height="564" alt="image" src="https://github.com/user-attachments/assets/fdb2e7fb-85f4-440e-8a34-99999d4c43d8" />


z=np.abs(stats.zscore(suren['sepal_length']))
z


<img width="799" height="748" alt="image" src="https://github.com/user-attachments/assets/41d4e46f-713f-426e-af9e-0833a36bfb60" />

suren1=suren[z<3]
suren1

<img width="782" height="600" alt="image" src="https://github.com/user-attachments/assets/6f01ea96-91e8-4bc0-904f-f16761b71394" />



# Result

Thus we have cleaned the data and removed the outliers by 
detection using IQR and Z-score method.
