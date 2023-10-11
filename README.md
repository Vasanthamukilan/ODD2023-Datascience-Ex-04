# ODD2023-Datascience-Ex-04
## AIM:
To perform Multivariate EDA on the given data set.
## EXPLANATION:
Exploratory data analysis is used to understand the messages within a dataset. This technique involves many iterative processes to ensure that the cleaned data is further sorted to better understand the useful meaning.The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
## ALGORITHM:
### STEP 1:
Import the built libraries required to perform EDA and outlier removal.
### STEP 2:
Read the given csv file
### STEP 3:
Convert the file into a dataframe and get information of the data.
### STEP 4:
Return the objects containing counts of unique values using (value_counts()).
### STEP 5:
Plot the counts in the form of Histogram or Bar Graph.
### STEP 6:
Use seaborn the bar graph comparison of data can be viewed.
### STEP 7:
Find the pairwise correlation of all columns in the dataframe.corr()
### STEP 8:
Save the final data set into the file.
## PROGRAM:
```
Name : ABINAYA S
Register Number : 212222230002
```
### SuperStore.csv file:
```
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
data=pd.read_csv("/content/SuperStore (1).csv")
df=pd.DataFrame(data)
df.head()
df.info()
df.describe()
df.isnull().sum()
df['Postal Code']=df['Postal Code'].fillna(df['Postal Code'].mode()[0])
df.isnull().sum()

sns.scatterplot(x=df['Region'],y=df['Sales'])

states=df.loc[:,["State","Sales"]]
states=states.groupby(by=["State"]).sum().sort_values(by="Sales")
plt.figure(figsize=(12,5))
plt.xticks(rotation=90)
sns.barplot(x=states.index,y="Sales",data=states)

states=df.loc[:,["Ship Mode","Row ID"]]
states=states.groupby(by=["Ship Mode"]).sum().sort_values(by="Row ID")
sns.barplot(x=states.index,y="Row ID",data=states)
plt.xticks(rotation = 90)
plt.xlabel=("SHIP MODE")
plt.ylabel=("ROW ID")
plt.show()

sns.boxplot(x=df['Ship Date'],y=df['Sales'])
sns.displot(df, x="Region", hue="Category")
df.corr()
sns.heatmap(df.corr(),annot=True)
```
### diabetes.csv file:
```
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
df=pd.read_csv("/content/diabetes.csv")
df
df.describe()
df.info
df.isnull().sum()

sns.scatterplot(x=df['Glucose'],y=df['BloodPressure'])

sns.scatterplot(x=df['Glucose'], y=df['BloodPressure'], hue=df['Outcome'])

Age=df.loc[:,["Age","BMI"]]
Age=Age.groupby(by=["Age"]).sum().sort_values(by="BMI")
plt.figure(figsize=(12,5))
plt.xticks(rotation=90)
sns.barplot(x=Age.index,y="BMI",data=Age)

Age=df.loc[:,["BloodPressure","Glucose"]]
Age=Age.groupby(by=["BloodPressure"]).sum().sort_values(by="Glucose")
sns.barplot(x=Age.index,y="Glucose",data=Age)
plt.xticks(rotation = 90)
plt.xlabel=("BloodPressure")
plt.ylabel=("Glucose")
plt.show()

sns.boxplot(x=df['DiabetesPedigreeFunction'],y=df['Insulin'])

sns.displot(df, x="Glucose", hue="Outcome")

df.corr()

sns.heatmap(df.corr(),annot=True)
```
## OUTPUT:
## SUPERSTORE:
### DATA FRAME OF SUPERSTORE
![DS1](https://github.com/abinayasangeetha/ODD2023-Datascience-Ex-04/assets/119393675/04da1d1e-4305-4abf-825d-effe43521a9f)


### Data information
![DS2](https://github.com/abinayasangeetha/ODD2023-Datascience-Ex-04/assets/119393675/c443883f-8cf6-4f5f-b4ee-eef401730a59)

### Data describing
![DS3](https://github.com/abinayasangeetha/ODD2023-Datascience-Ex-04/assets/119393675/51b07f4d-77eb-4482-a5c8-fe68ec112bc2)

### Sum of null values
![DS4](https://github.com/abinayasangeetha/ODD2023-Datascience-Ex-04/assets/119393675/f0958e9d-36fe-4745-93cf-3885d67e855b)

### After removing null values
![DS5](https://github.com/abinayasangeetha/ODD2023-Datascience-Ex-04/assets/119393675/c29779d4-e3d8-4391-a59a-b65b8cc25e9f)

### Scatter plot
![DS6](https://github.com/abinayasangeetha/ODD2023-Datascience-Ex-04/assets/119393675/cd55d233-5f25-4451-9eac-1270557c5c14)

### Bar plot
![DS7](https://github.com/abinayasangeetha/ODD2023-Datascience-Ex-04/assets/119393675/a1ba9121-6cc4-4a13-93cc-c884491218dd)

![DS8](https://github.com/abinayasangeetha/ODD2023-Datascience-Ex-04/assets/119393675/1fb3fb81-f2a7-4c34-9cc5-84dc2d8a9501)


### Box plot
![DS9](https://github.com/abinayasangeetha/ODD2023-Datascience-Ex-04/assets/119393675/92fa18b4-46e9-4e75-abbf-208ea3dea94c)

### Dist plot
![DS10](https://github.com/abinayasangeetha/ODD2023-Datascience-Ex-04/assets/119393675/6582fd54-083b-482a-9670-40ce01d38e7f)

### Correlation coefficient interpretation
![DS11](https://github.com/abinayasangeetha/ODD2023-Datascience-Ex-04/assets/119393675/80d97153-1912-40ca-9a7c-875c63ae7486)

### Heat map
![DS12](https://github.com/abinayasangeetha/ODD2023-Datascience-Ex-04/assets/119393675/4204da31-bbfc-4051-842a-bd3b8e0a3cbb)

## DIABETES
### DATA FRAME FOR DIABETES
![DS13](https://github.com/abinayasangeetha/ODD2023-Datascience-Ex-04/assets/119393675/d4d5c50b-015f-4d2a-bb29-39370301a9ce)

### Data information
![DS14](https://github.com/abinayasangeetha/ODD2023-Datascience-Ex-04/assets/119393675/e267215f-0108-4655-8a4e-3e3e6117f257)

### Data describing
![DS15](https://github.com/abinayasangeetha/ODD2023-Datascience-Ex-04/assets/119393675/13ff73a9-97ea-485f-a799-45edb43d6e6a)

### Sum of null values
![DS16](https://github.com/abinayasangeetha/ODD2023-Datascience-Ex-04/assets/119393675/c1e2954b-2fe8-4e63-935f-fcf168d03e20)

### Scatter plot
![DS17](https://github.com/abinayasangeetha/ODD2023-Datascience-Ex-04/assets/119393675/7e7e1712-2305-4cb4-afcb-ea4f42e0c9a7)
![DS18](https://github.com/abinayasangeetha/ODD2023-Datascience-Ex-04/assets/119393675/bb3781f1-5fa4-4194-b16c-03ba3a662fb4)
### Bar plot
![DS19](https://github.com/abinayasangeetha/ODD2023-Datascience-Ex-04/assets/119393675/c93a6716-2d38-4268-aeae-b3fee90409fd)
![DS20](https://github.com/abinayasangeetha/ODD2023-Datascience-Ex-04/assets/119393675/10b80b0f-af9a-4d60-8284-22d682c724e3)
### Box plot
![DS21](https://github.com/abinayasangeetha/ODD2023-Datascience-Ex-04/assets/119393675/aaf4bb9d-1541-4ad0-b5ef-a389d7bd0adb)

### Dist plot
![DS22](https://github.com/abinayasangeetha/ODD2023-Datascience-Ex-04/assets/119393675/a8b71f2b-e474-4f80-a354-8e6e1aa15062)

### correlation coefficient interpretation


![DS23](https://github.com/abinayasangeetha/ODD2023-Datascience-Ex-04/assets/119393675/5b89025c-0179-4741-934c-6ef20fe8e3df)

### Heat map
![DS24](https://github.com/abinayasangeetha/ODD2023-Datascience-Ex-04/assets/119393675/71fa8088-79a1-4896-853b-cccb9a47d230)

## RESULT:
Thus we have read the given data and performed the multivariate analysis with different types of plots.
