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

# Zscore of 3

# NEWDATA USING Zscore
![Screenshot_20230325_072952](https://user-images.githubusercontent.com/121166004/227721981-c755cd30-bfa3-4466-a934-2915706f947d.png)

# OUTLIERS
![Screenshot_20230325_073010](https://user-images.githubusercontent.com/121166004/227722075-6dc3085d-800b-4a49-9fdf-de53a3e2cd94.png)

# newdata2.shape
![Screenshot_20230325_073022](https://user-images.githubusercontent.com/121166004/227722159-3ca66a16-fb87-4c2d-88c6-dacf8ef9e6e0.png)

# BOXPLOT AFTER REMOVING OUTLIERS USING Zscore
![Screenshot_20230325_073033](https://user-images.githubusercontent.com/121166004/227722210-9fe07e48-70c6-49a5-afc0-4d5e91568c56.png)

# height_weight.csv

dataset.shape 
![Screenshot_20230325_073052](https://user-images.githubusercontent.com/121166004/227726142-f5d8fb03-ecc9-451e-9dc8-485d17bc82a9.png)

# dataset.describe()
![Screenshot_20230325_073112](https://user-images.githubusercontent.com/121166004/227726179-e6059209-6a5c-4bcb-bb95-20e451d1f039.png)

# dataset.info()
![Screenshot_20230325_085138](https://user-images.githubusercontent.com/121166004/227726485-bf95110f-0284-4cde-9d28-7be0fca9a646.png)

# BOXPLOT BEFORE REMOVING OUTLIERS
![Screenshot_20230325_085153](https://user-images.githubusercontent.com/121166004/227726568-f117eb2a-1f6f-4728-b609-905b83b1cc82.png)

# HEIGHT OUTLIERS
![Screenshot_20230325_085254](https://user-images.githubusercontent.com/121166004/227726705-882aa989-e758-44b6-9f46-354571f9c152.png)

# DATASET AFTER REMOVING HEIGHT OUTLIERS
![Screenshot_20230325_085328](https://user-images.githubusercontent.com/121166004/227726741-dbd22944-5898-4f36-a4c9-d2d2e5e39238.png)

# BOXPLOT AFTER REMOVING HEIGHT OUTLIERS
![Screenshot_20230325_085339](https://user-images.githubusercontent.com/121166004/227726795-f0e62ca1-7b1c-40e4-8ff6-f595af03f3d7.png)

# WEIGHT OUTLIERS
![Screenshot_20230325_085353](https://user-images.githubusercontent.com/121166004/227726843-c306eb58-ffb8-478f-b727-9d957722a3c0.png)

# DATASET AFTER REMOVING WEIGHT OUTLIERS
![Screenshot_20230325_085405](https://user-images.githubusercontent.com/121166004/227726891-6ce265ce-ec21-4709-a706-01d6a9bfe6b9.png)

# BOXPLOT AFTER REMOVING WEIGHT OUTLIERS
![Screenshot_20230325_085419](https://user-images.githubusercontent.com/121166004/227726924-357e5fa1-0076-4099-a964-3a78a2bf0897.png)

# RESULT
The given datasets are read and outliers are detected and are removed using IQR and z-score methods.





    
