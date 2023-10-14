# EX 04 MULTIVARIATE ANALYSIS
### Aim:
To perform Multivariate EDA on the given data set.
### Explanation:
Exploratory data analysis is used to understand the messages within a dataset. This technique involves many iterative processes to ensure that the cleaned data is further sorted to better understand the useful meaning.The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
### Algorithm:
- Step1: Import the built libraries required to perform EDA and outlier removal.
- Step2: Read the given csv file.
- Step3: Convert the file into a dataframe and get information of the data.
- Step4: Return the objects containing counts of unique values using (value_counts()).
- Step5: Plot the counts in the form of Histogram or Bar Graph.
```
Developed By: 212222230167  
Register Number: Vasanthamukilan M
```
### Program:
- SuperStore.csv
```Python
import pandas as pd
import seaborn as sns
from scipy import stats
import matplotlib.pyplot as plt
df=pd.read_csv('SuperStore.csv')
df.describe()
df.isnull().sum()
df.info()
# FILLING NULL VALUES
df['Postal Code']=df['Postal Code'].fillna(df['Postal Code'].mode()[0])
sns.boxplot(df)
sns.scatterplot(x=df['Region'],y=df['Sales'])
plt.figure(figsize=(10,3))
sns.barplot(x=df['State'],y=df['Sales'])
plt.xticks(rotation=90)
sns.heatmap(df.corr(),annot=True)
sns.displot(df,x='Region',hue="Category")
```
- Output: (SuperStorE.csv)
- 
![4_1](https://github.com/Vasanthamukilan/ODD2023-Datascience-Ex-04/assets/119559694/ce5d0568-0e16-4e29-ba56-5651f31d3128)

![4_2](https://github.com/Vasanthamukilan/ODD2023-Datascience-Ex-04/assets/119559694/1d5dd5a2-1a62-46b2-8cc5-4e0a16118e30)

![4_3](https://github.com/Vasanthamukilan/ODD2023-Datascience-Ex-04/assets/119559694/fb05e968-db00-46a5-b56b-cd27e952f65b)

![4_4](https://github.com/Vasanthamukilan/ODD2023-Datascience-Ex-04/assets/119559694/996208ed-9c79-47c3-b093-889dc16c10bc)

![4_5](https://github.com/Vasanthamukilan/ODD2023-Datascience-Ex-04/assets/119559694/ae80a7bd-816d-4c58-b9ec-b8b9babeb066)

![4_6](https://github.com/Vasanthamukilan/ODD2023-Datascience-Ex-04/assets/119559694/8fc2f36a-6175-4ecc-a099-eacc87843dcf)

![4_7](https://github.com/Vasanthamukilan/ODD2023-Datascience-Ex-04/assets/119559694/a73bb274-e93a-4504-bcd3-d15bca088dba)

![4_8](https://github.com/Vasanthamukilan/ODD2023-Datascience-Ex-04/assets/119559694/808bb94a-a06c-4606-beaf-5a966ad13022)


- Diabetes.csv
```Python
import pandas as pd
import seaborn as sns
from scipy import stats
import matplotlib.pyplot as plt
df=pd.read_csv('diabetes.csv')
df.describe()
df.isnull().sum()
# REMOVING OUTLIER
z = np.abs(stats.zscore(df['Glucose']))
df=df[(z<2)]
z = np.abs(stats.zscore(df['BloodPressure']))
df=df[(z<2)]
z = np.abs(stats.zscore(df['SkinThickness']))
df=df[(z<3)]
z = np.abs(stats.zscore(df['BMI']))
df=df[(z<2)]
z = np.abs(stats.zscore(df['Insulin']))
df=df[(z<2)]
z = np.abs(stats.zscore(df['DiabetesPedigreeFunction']))
df=df[(z<2)]
z = np.abs(stats.zscore(df['Age']))
df=df[(z<2)]
z = np.abs(stats.zscore(df['Outcome']))
df=df[(z<3)]
sns.boxplot(data=df)
plt.xticks(rotation=90)
sns.boxplot(data=df)
plt.xticks(rotation=90)
sns.scatterplot(x=df['Glucose'], y=df['BloodPressure'], hue=df['Outcome'])
Age=df.loc[:,["Age","BMI"]]
Age=Age.groupby(by=["Age"]).sum().sort_values(by="BMI")
plt.figure(figsize=(12,5))
plt.xticks(rotation=90)
sns.barplot(x=Age.index,y="BMI",data=Age)
sns.boxplot(x=df['DiabetesPedigreeFunction'],y=df['Insulin'])
sns.displot(df, x="Glucose", hue="Outcome")
df.corr()
sns.heatmap(df.corr(),annot=True)
```
- Output (Diabetes.csv):

![Screenshot 2023-10-14 000109](https://github.com/Vasanthamukilan/ODD2023-Datascience-Ex-04/assets/119559694/356586f6-3c77-42ad-891b-e0ed2d0b2428)

![4_9](https://github.com/Vasanthamukilan/ODD2023-Datascience-Ex-04/assets/119559694/45797b52-4dc6-48d0-8134-be037421332b)

![4_10](https://github.com/Vasanthamukilan/ODD2023-Datascience-Ex-04/assets/119559694/d682827a-066f-4efd-86af-ecb77840f3ee)

![4_11](https://github.com/Vasanthamukilan/ODD2023-Datascience-Ex-04/assets/119559694/818c2ec8-5726-45e3-a684-3cf159d7fd42)

![4_12](https://github.com/Vasanthamukilan/ODD2023-Datascience-Ex-04/assets/119559694/96ea6956-0d78-4a04-9948-1877715ccfe7)

![4_13](https://github.com/Vasanthamukilan/ODD2023-Datascience-Ex-04/assets/119559694/553048e3-d50d-4aaf-8a9c-79ebec49213c)

![4_14](https://github.com/Vasanthamukilan/ODD2023-Datascience-Ex-04/assets/119559694/07f878e7-5330-4996-b8bb-93e68d327248)

![4_15](https://github.com/Vasanthamukilan/ODD2023-Datascience-Ex-04/assets/119559694/dc9e09d2-e33b-4b43-81e8-d42c4042d65c)



### RESULT:
Thus we have read the given data and performed the multivariate analysis with different types of plots.
