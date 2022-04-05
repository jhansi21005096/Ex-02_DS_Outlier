# Ex-02_DS_Outlier
# AIM
To detect and remove the outliers in the given data set and save the final data.
# Explanation
Outlier is a data object that deviates significantly from the rest of the data objects and behaves in a different manner. They can be caused by measurement or execution errors. The analysis of outlier data is referred to as outlier analysis or outlier mining. The box plot is a useful graphical display for describing the behavior of the data in the middle as well as at the ends of the distributions. The box plot uses the median and the lower and upper quartiles (defined as the 25th and 75th percentiles). If the lower quartile is Q1 and the upper quartile is Q3, then the difference (Q3 - Q1) is called the interquartile range or IQ.

# ALGORITHM
### STEP 1 :
Import the required packages(pandas,numpy,scipy)

### STEP 2 :
Read the given csv file

### STEP 3 :
Convert the file into a dataframe and get information of the data.
### STEP 4 :
Remove the non numerical data columns using drop() method.
### step5  : 
 Detect the outliers in the data set using z scores method.
 ### Step6  :  
 Remove the outliers by z scores and list manupilation or by using Interquartile Range(IQR)
 ### Step7  :  
 Check if the outliersare removed from data set using graphical methods.
### Step8  :  
Save the final data set into the file.
# CODE
```
import pandas as pd
df = pd.read_csv('weight.csv')
df.sample(10)
```
```
df.drop("Gender",axis=1)
```
```
df.boxplot()
```
```
import pandas as pd
df=pd.read_csv("weight.csv")
df.drop("Gender",axis=1)
df.drop("Gender",axis=1,inplace=True)
df
df.boxplot()
```
```
from scipy import stats
import numpy as np
z=np.abs(stats.zscore(df))
z
```
```
df1=df.copy()
df1=df1[(z<3).all(axis=1)]
df1
```
```
df1.boxplot()
```
```
df2=df.copy()
q1=df2.quantile(0.25)
q3=df2.quantile(0.75)
IQR=q3-q1
df2_new=df2[((df2>=q1-1.5*IQR)&(df2<=q3+1.5*IQR)).all(axis=1)]
df2_new.boxplot()
df2_new
```
# OUPUT
![output](output1.png)
![output](output2.png)
![output](output3.png)
![output](output4.png)
![output](output5.png)
![output](output6.png)
![output](output7.png)
![output](output8.png)
