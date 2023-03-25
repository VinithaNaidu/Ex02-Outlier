# Ex02-Outlier

You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR 

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following
    
    (i) Using IQR detect weight outliers and print them

    (ii) Using IQR, detect height outliers and print them
   
 # ALGORITHM :
 
 ### STEP 01
 
 Read the given Data.

### STEP 02

Get the information about the data.

### STEP 03

Detect the Outliers using IQR method and Z score.

### STEP 04

Remove the outliers.

### STEP 05

Plot the datas using Box Plot.

# PROGRAM:

```

DEVELOPED BY: D. VINITHA NAIDU, REGISTER NUMBER: 212222230175
import pandas as pd
df=pd.read_csv("/content/bhp.csv")
df.head()
df.describe()
df.info()
df.shape

import seaborn as sns
sns.boxplot(x="price_per_sqft",data=df)

### removing ouliers of bhp.csv file using IQR
Q1=df['price_per_sqft'].quantile(0.25)
Q3=df['price_per_sqft'].quantile(0.75)
IQR=Q3-Q1
lower=Q1-1.5*IQR
upper=Q3+1.5*IQR
newdata=df[(df['price_per_sqft']>=lower) & (df['price_per_sqft']<=upper)] 
print(newdata)   #new dataframe.
outliers=df[(df['price_per_sqft']<lower) | (df['price_per_sqft']>upper)]
print(outliers)
newdata.shape
sns.boxplot(x="price_per_sqft",data=newdata)


### removing ouliers of bhp.csv file using Zscore of 3

from scipy import stats
import numpy as np
z_score=np.abs(stats.zscore(df['price_per_sqft']))
newdata2=df[(z_score<3)]
print(newdata2)
outlier2=df[(z_score>=3)]
print(outlier2)
newdata2.shape
sns.boxplot(x="price_per_sqft",data=newdata2)

import pandas as pd
dataset=pd.read_csv("/content/height_weight.csv")
dataset.shape
dataset.describe()
dataset.info()
import seaborn as sns
sns.boxplot(x='height',data=dataset)

### Using IQR detect height outliers and print them( height_weight.csv)

Q1_height=dataset['height'].quantile(0.25)
Q3_height=dataset['height'].quantile(0.75)
IQR_HEIGHT=Q3_height-Q1_height
l_height=Q1_height-1.5*IQR_HEIGHT
u_height=Q3_height+1.5*IQR_HEIGHT
outliers_height=dataset[(dataset['height']<l_height) | (dataset['height']>u_height)]
print(outliers_height)
newdata_height=dataset[(dataset['height']>=l_height) & (dataset['height']<=u_height)]
print(newdata_height)
sns.boxplot(x='height',data=newdata_height)


### Using IQR, detect weight outliers and print them( height_weight.csv)

Q1_weight=dataset['weight'].quantile(0.25)
Q3_weight=dataset['weight'].quantile(0.75)
IQR_WEIGHT=Q3_weight-Q1_weight
l_weight=Q1_weight-1.5*IQR_WEIGHT
u_weight=Q3_weight+1.5*IQR_WEIGHT
outliers_weight=dataset[(dataset['weight']<l_weight) | (dataset['weight']>u_weight)]
print(outliers_weight)
newdata_weight=dataset[(dataset['weight']>=l_weight) & (dataset['weight']<=u_weight)]
print(newdata_weight)
sns.boxplot(x='weight',data=newdata_weight)
 
 ```
 
 
### OUTPUT

bhp.csv IQR METHOD

# df.head()
![Screenshot_20230325_071151](https://user-images.githubusercontent.com/121166004/227720988-a91fe1d9-62fd-4c15-a4d8-add5dcd035f4.png)

# df.describe()
![Screenshot_20230325_071205](https://user-images.githubusercontent.com/121166004/227721034-8a6bca8d-0eaa-48d0-b87c-ed320b17f247.png)

# df.info()
![Screenshot_20230325_071205](https://user-images.githubusercontent.com/121166004/227721100-3bc5f656-36b7-4716-b2a9-ed812473b403.png)

# df.shape()
![Screenshot_20230325_071821](https://user-images.githubusercontent.com/121166004/227721166-1cb8fb19-25bf-4c4b-a5d3-b09e6d65de94.png)

# BOXPLOT BEFORE REMOVING OUTLIERS
![Screenshot_20230325_071249](https://user-images.githubusercontent.com/121166004/227721205-12d39159-80d1-4446-be28-bbf20a4b20fb.png)

# NEWDATA USING IQR
![Screenshot_20230325_071302](https://user-images.githubusercontent.com/121166004/227721295-8b1267fa-a6f0-408f-b4bc-68bd3b9ccbdf.png)

# OUTLIERS
![Screenshot_20230325_071313](https://user-images.githubusercontent.com/121166004/227721386-78925cfa-be94-4d65-937b-97a79bb2a549.png)

# newdata.shape
![Screenshot_20230325_072458](https://user-images.githubusercontent.com/121166004/227721469-866bc5de-855d-4a8d-84f4-e4b3308dc8e3.png)

# BOXPLOT AFTER REMOVING OUTLIERS USING IQR
![Screenshot_20230325_071328](https://user-images.githubusercontent.com/121166004/227721534-b62f0359-5faa-4fbc-acd2-29fd71a9d960.png)

# 





    
