# Ex-03EDA

## AIM
To perform EDA on the given data set. 

# Explanation
The primary aim with exploratory analysis is to examine the data for distribution, outliers and 
anomalies to direct specific testing of your hypothesis.
 

# ALGORITHM
### STEP 1
Import the required packages.

### STEP 2
Read the csv file and convert into DataFrame.

### STEP 3
Perform Data Cleaning on the DataSet.

### STEP 4
Detect and Remove the Outliers from the Dataset.

### STEP 5
Perform Exploratory Data Analysis on the data.



# CODE
```
import pandas as pd
import numpy as np
import seaborn as sns
df=pd.read_csv("titanic_dataset.csv")
df.info()
df.head()
df.isnull().sum()
df.drop("Cabin",axis=1,inplace=True)
df.info()
df.isnull().sum()
df["Age"]=df["Age"].fillna(df["Age"].median())
df.boxplot()
df.isnull().sum()
df["Embarked"]=df["Embarked"].fillna(df["Embarked"].mode()[0])
df.isnull().sum()
df.boxplot()
Q1 = df.quantile(0.25)
Q3 = df.quantile(0.75)
IQR = Q3 - Q1
print(IQR)
df_out = df[~((df < (Q1 - 1.5 * IQR)) |(df > (Q3 + 1.5 * IQR))).any(axis=1)]
print(df_out.shape)
df_out.boxplot()
df_out.info()
df["Embarked"].value_counts()
df_out["Embarked"].value_counts()
df["Pclass"].value_counts()
df_out["Pclass"].value_counts()
df["Survived"].value_counts()
df_out["Survived"].value_counts()
df["Sex"].value_counts()
df_out["Sex"].value_counts()
df["SibSp"].value_counts()
df_out["SibSp"].value_counts()
sns.countplot(x="Survived",data=df_out)
sns.countplot(x="Pclass",data=df_out)
sns.countplot(x="Sex",data=df_out)
sns.countplot(x="Embarked",data=df_out)
sns.countplot(x="SibSp",data=df_out)
df_out.info()
sns.displot(df_out["Fare"])
sns.displot(df_out["Age"])
sns.countplot(x="Pclass",hue="Survived",data=df_out)
sns.countplot(x="Sex",hue="Survived",data=df_out)
sns.countplot(x="SibSp",hue="Sex",data=df_out)
sns.countplot(x="Embarked",hue="Pclass",data=df_out)
sns.countplot(x="Survived",hue="Embarked",data=df_out)
sns.displot(df_out[df_out["Survived"]==0]["Age"])
sns.displot(df_out[df_out["Survived"]==1]["Age"])
sns.displot(df_out[df_out["SibSp"]==0]["Embarked"])
sns.displot(df_out[df_out["SibSp"]==1]["Embarked"])
pd.crosstab(df_out["Pclass"],df_out["Survived"])
pd.crosstab(df_out["Sex"],df_out["Survived"])
pd.crosstab(df_out["Pclass"],df_out["Sex"])
pd.crosstab(df_out["Sex"],df_out["Embarked"])
df.corr()
df_out.corr()
sns.heatmap(df.corr(),annot=True)
sns.heatmap(df_out.corr(),annot=True)
```
# OUPUT

![output](.//1.PNG)
![output](.//2.PNG)
![output](.//3.PNG)
![output](.//4.PNG)
![output](.//5.PNG)
![output](.//6.PNG)
![output](.//7.PNG)
![output](.//8.PNG)
![output](.//9.PNG)
![output](.//10.PNG)
![output](.//11.PNG)
![output](.//12.PNG)
![output](.//13.PNG)
![output](.//14.PNG)
![output](.//15.PNG)
![output](.//16.PNG)
![output](.//17.PNG)














# Result
Data cleaning and Outlier removal has been carried out in the given DataFrame.EDA is sucessfully performed in the given dataset.