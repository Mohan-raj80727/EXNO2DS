# EXNO2DS
# NAME : MOHAN RAJ.S
# REGISTER NO: 212224100036
# AIM:
      To perform Exploratory Data Analysis on the given data set.
      
# EXPLANATION:
  The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
  
# ALGORITHM:
STEP 1: Import the required packages to perform Data Cleansing,Removing Outliers and Exploratory Data Analysis.

STEP 2: Replace the null value using any one of the method from mode,median and mean based on the dataset available.

STEP 3: Use boxplot method to analyze the outliers of the given dataset.

STEP 4: Remove the outliers using Inter Quantile Range method.

STEP 5: Use Countplot method to analyze in a graphical method for categorical data.

STEP 6: Use displot method to represent the univariate distribution of data.

STEP 7: Use cross tabulation method to quantitatively analyze the relationship between multiple variables.

STEP 8: Use heatmap method of representation to show relationships between two variables, one plotted on each axis.

## CODING AND OUTPUT
~~~
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
mohan=pd.read_csv("/content/titanic_dataset.csv")
mohan
~~~
![Screenshot 2025-03-29 105534](https://github.com/user-attachments/assets/1c26c591-5be9-42f3-a577-e3dd788ea641)
~~~
mohan.info()
~~~
![Screenshot 2025-03-29 105808](https://github.com/user-attachments/assets/530d1eaa-887b-4732-9941-f693f9ce94ea)
~~~
mohan.shape
~~~
![Screenshot 2025-03-29 105953](https://github.com/user-attachments/assets/0a21de9c-84f2-45b1-8485-bcc574941f73)
~~~
mohan.set_index("PassengerId",inplace=True)
mohan.describe()
~~~
![Screenshot 2025-03-29 110136](https://github.com/user-attachments/assets/2187267b-0506-40fa-beac-8021bbd10cd5)
~~~
mohan.shape
~~~
![Screenshot 2025-03-29 110235](https://github.com/user-attachments/assets/de2e8764-652c-4c43-9aa2-be71379d8e44)
# Categorical data analysis
~~~
mohan.nunique()
~~~
![Screenshot 2025-03-29 110325](https://github.com/user-attachments/assets/c1b5ab95-5ed7-47ab-9c2e-ad0bfabef88c)
~~~
mohan["Survived"].value_counts()
~~~
![Screenshot 2025-03-29 110418](https://github.com/user-attachments/assets/c9bad0e0-b117-4532-b90a-7cfdfe1bfd2a)
~~~
per=(mohan["Survived"].value_counts()/mohan.shape[0]*100).round(2)
per
~~~
![Screenshot 2025-03-29 110550](https://github.com/user-attachments/assets/1f80a502-b247-4a65-8702-a33c67d1bba7)
~~~
sns.countplot(data=mohan,x="Survived" ,color="green")
~~~
![Screenshot 2025-03-29 110651](https://github.com/user-attachments/assets/f09c4042-7968-4c01-8579-b2bd01ced584)
~~~
mohan
~~~
![Screenshot 2025-03-29 110942](https://github.com/user-attachments/assets/da7abb79-bea0-4db9-9c1d-35166496aaec)
~~~
mohan.Pclass.unique()
~~~
![Screenshot 2025-03-29 111251](https://github.com/user-attachments/assets/3fcd4be8-a5af-41da-9a9c-c35b936c793f)
~~~
mohan.rename(columns={'Sex':'Gender'},inplace=True)
mohan
~~~
![Screenshot 2025-03-29 111408](https://github.com/user-attachments/assets/1231dc83-b9a7-44ee-baee-d0e8108db258)
# Bivariate Analysis
~~~
sns.catplot(x="Gender",col="Survived",kind="count",data=mohan,height=5,aspect=.7)
~~~
![Screenshot 2025-03-29 111534](https://github.com/user-attachments/assets/56454c77-8650-40fe-a087-7d6eae8ed59f)
~~~
sns.catplot(x="Survived",hue="Gender",data=mohan,kind="count")
~~~
![Screenshot 2025-03-29 111727](https://github.com/user-attachments/assets/f26958e5-7d34-49f2-b33c-e20e11272f0e)
~~~
mohan.boxplot(column="Age",by="Survived")
~~~
![image](https://github.com/user-attachments/assets/6d873eb8-e8c8-4fe2-80ee-2a25d55156ed)
~~~
sns.scatterplot(x=mohan["Age"],y=mohan["Fare"])
~~~
![image](https://github.com/user-attachments/assets/5ef3f089-0038-4d08-91ca-9f6b9b8bf826)
~~~
sns.jointplot(x="Age",y="Fare",data=mohan)
~~~
![image](https://github.com/user-attachments/assets/1b9f2f3d-1c03-4f00-95ed-58c38ffb3668)
# Multivariate Analysis
~~~
fig,ax1=plt.subplots(figsize=(8,5))
plt=sns.boxplot(ax=ax1,x='Pclass',y='Age',hue='Gender',data=mohan)
~~~
![image](https://github.com/user-attachments/assets/f0dc520f-f5ef-43ef-8a71-60a3e06d3957)
~~~
sns.catplot(data=mohan,col="Survived",x="Gender",hue="Pclass",kind="count")
~~~
![image](https://github.com/user-attachments/assets/0214ce53-efad-4a16-bc64-710623c07f5e)
# Co-relation
~~~
numerical_mohan = mohan.select_dtypes(include=np.number)
corr = numerical_mohan.corr()
sns.heatmap(corr, annot=True)
~~~
![image](https://github.com/user-attachments/assets/9b646e4f-11fe-41c7-9bfa-98460fe1d024)
~~~
sns.pairplot(mohan)
~~~
![image](https://github.com/user-attachments/assets/09c8a89e-80ff-414e-989e-c4322527a28e)

# RESULT:
We have performed Exploratory Data Analysis on the given data set successfully.
