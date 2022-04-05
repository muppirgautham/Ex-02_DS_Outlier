# Ex-02_DS_Outlier
### AIM :
To detect and remove the outliers in the given data set and save the final data.
### EXPLANATION :
Outlier is a data object that deviates significantly from the rest of the data objects and behaves in a different manner. They can be caused by measurement or execution errors. The analysis of outlier data is referred to as outlier analysis or outlier mining. The box plot is a useful graphical display for describing the behavior of the data in the middle as well as at the ends of the distributions. The box plot uses the median and the lower and upper quartiles (defined as the 25th and 75th percentiles). If the lower quartile is Q1 and the upper quartile is Q3, then the difference (Q3 - Q1) is called the interquartile range or IQ.
### ALGORITHM :
## Step 1
Import the required packages(pandas,numpy,scipy)
## Step 2
Read the given csv file
## Step 3
Convert the file into a dataframe and get information of the data.
## Step 4
Remove the non numerical data columns using drop() method.
## Step 5
Detect the outliers in the data set using z scores method.
## Step 6
Remove the outliers by z scores and list manupilation or by using Interquartile Range(IQR)
## Step 7
Check if the outliersare removed from data set using graphical methods.
## Step 8
Save the final data set into the file.
### PROGRAM :
```
Developed by: GAUTHAM M
Register number:212221230027

import pandas as pd
df=pd.read_csv('weight.csv')
df

#removing non numerical columns
df=df.drop("Gender",axis=1)
print('After removing Non numeric columns:')
df

#graph to display outliers
df.boxplot()

#calculating z scores to detect outliers
import numpy as np
from scipy import stats
z=np.abs(stats.zscore(df))
print(z)

#removing outliers from weight
df1=df.copy()
df1=df1[(z<3).all(axis=1)]
df1

#checking if outliers are removed through graph
df1.boxplot()

#removing outliers from height
df2=df.copy()
q1=df2.quantile(0.25)
q3=df2.quantile(0.75)
IQR=q3-q1
df_new=df2[((df2>=q1-1.5*IQR)&(df2<=q3+1.5*IQR)).all(axis=1)]
df_new

#checking if outliers are removed through graph
df_new.boxplot()

#final dataset
df_new

#saving data   file
df.to_csv('weight.csv', index=False)
```
### OUTPUT :
## Initial data set:
![image](https://user-images.githubusercontent.com/94810884/161677254-a5dc7472-a96c-406a-8857-77bfb41ca014.png)

## Data set after removing non numerical sets:
![image](https://user-images.githubusercontent.com/94810884/161677314-102e4773-6b13-4a5b-977d-755c95e9c658.png)

## Graph displaying initial dataset with outliers:
![image](https://user-images.githubusercontent.com/94810884/161677377-e5d52176-3736-4585-b84d-ebb054acfe24.png)

## Z scores to detect outliers:
![image](https://user-images.githubusercontent.com/94810884/161677422-fcf9730c-1dac-44dc-9183-667fac0ec0f1.png)

## Data set after removing outliers in weight using z scores and list manipulation:
![image](https://user-images.githubusercontent.com/94810884/161677479-77e40187-f0bf-40c9-ab12-bc67516c7d77.png)

## Graph after removing outliers in weight:
![image](https://user-images.githubusercontent.com/94810884/161677562-c7e351e5-c2f3-4b8c-be63-243996a3550f.png)

## Data set after removing outliers in height using Interquartile Range(IQR):
![image](https://user-images.githubusercontent.com/94810884/161677608-1b83af73-726c-45a9-901b-280805be2d6a.png)

## Final graph after removing all outliers:
![image](https://user-images.githubusercontent.com/94810884/161780611-215ddfd3-4ec9-4d54-a01b-0d8b943a1bf5.png)

## Final data set:
![image](https://user-images.githubusercontent.com/94810884/161780749-f891371b-629a-4f9b-93f7-d8b8ccc4a24e.png)

### RESULT:
Thus the outliers are detected and removed in the given file and the final data set is saved into the file.




