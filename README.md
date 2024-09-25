## EXNO-3-DS

# AIM:
To read the given data and perform Feature Encoding and Transformation process and save the data to a file.

# ALGORITHM:
STEP 1:Read the given Data.
STEP 2:Clean the Data Set using Data Cleaning Process.
STEP 3:Apply Feature Encoding for the feature in the data set.
STEP 4:Apply Feature Transformation for the feature in the data set.
STEP 5:Save the data to the file.

# FEATURE ENCODING:
1. Ordinal Encoding
An ordinal encoding involves mapping each unique label to an integer value. This type of encoding is really only appropriate if there is a known relationship between the categories. This relationship does exist for some of the variables in our dataset, and ideally, this should be harnessed when preparing the data.
2. Label Encoding
Label encoding is a simple and straight forward approach. This converts each value in a categorical column into a numerical value. Each value in a categorical column is called Label.
3. Binary Encoding
Binary encoding converts a category into binary digits. Each binary digit creates one feature column. If there are n unique categories, then binary encoding results in the only log(base 2)ⁿ features.
4. One Hot Encoding
We use this categorical data encoding technique when the features are nominal(do not have any order). In one hot encoding, for each level of a categorical feature, we create a new variable. Each category is mapped with a binary variable containing either 0 or 1. Here, 0 represents the absence, and 1 represents the presence of that category.

# Methods Used for Data Transformation:
  # 1. FUNCTION TRANSFORMATION
• Log Transformation
• Reciprocal Transformation
• Square Root Transformation
• Square Transformation
  # 2. POWER TRANSFORMATION
• Boxcox method
• Yeojohnson method

# CODING AND OUTPUT:
```
import pandas as pd
df=pd.read_csv("/content/Encoding Data.csv")
df
```
![image](https://github.com/user-attachments/assets/3e735a88-0507-4bca-b382-9bd9322b5677)

```
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt
```
```
from sklearn.preprocessing import LabelEncoder, OrdinalEncoder
```
```
pm=['Hot','Warm','Cold']
```
```
el= OrdinalEncoder(categories = [pm])
```
```
el.fit_transform(df[["ord_2"]])
```

![image](https://github.com/user-attachments/assets/8e10dc44-682d-4cf2-916b-13b412bf70f4)

```
df['bo2']=el.fit_transform(df[["ord_2"]])

df
```

![image](https://github.com/user-attachments/assets/2d868f26-5e4b-4807-81a1-8aa85c9af317)

```
le=LabelEncoder()
dfc=df.copy()
dfc['ord_2']=le.fit_transform(dfc['ord_2'])
dfc
```

![image](https://github.com/user-attachments/assets/eed9d998-4a2c-4571-ae3d-621f183fd26c)

```
dfc=df.copy()
dfc['con_2']=le.fit_transform(dfc['ord_2'])
dfc
```

![image](https://github.com/user-attachments/assets/035f680e-dbf0-4a4d-ad50-cba1bb95ef6c)

```
from sklearn.preprocessing import OneHotEncoder
ohe=OneHotEncoder(sparse_output=False)
df=df.copy()
```
```
enc=pd.DataFrame(ohe.fit_transform(df[['nom_0']]))
enc
```

![image](https://github.com/user-attachments/assets/0de7ee6f-9baa-4e0b-a024-002c6c6f7351)

```
df2=pd.concat([df,enc],axis=1)
df2
```

![image](https://github.com/user-attachments/assets/3ac75523-8147-4da0-9dc4-f07d0e5c03dc)

```
pip install --upgrade category_encoders
```
```
from category_encoders import BinaryEncoder
```
```
import pandas as pd
df=pd.read_csv('/content/data (1).csv')

df
```

![image](https://github.com/user-attachments/assets/fbf9b8fd-1f31-4a34-a015-2bf592ef6cb3)

```
be=BinaryEncoder()
nd=be.fit_transform(df['Ord_2'])
dfb=pd.concat([df,nd],axis=1)
dfb1=df.copy()
dfb
```

![image](https://github.com/user-attachments/assets/ea9b50e2-2daf-4ad6-86d2-226e06da6ecf)

```
from category_encoders import TargetEncoder
te=TargetEncoder()
cc=df.copy()
new=te.fit_transform(X=cc["City"],y=cc["Target"])
cc=pd.concat([cc,new],axis=1)
cc
```

![image](https://github.com/user-attachments/assets/ca40d19a-5493-4707-9fb0-0879990c9cfd)


```
import numpy as np
import pandas as pd
from scipy import stats
```
```
df=pd.read_csv('/content/Data_to_Transform.csv')
df
```
```
df.skew()
```

![image](https://github.com/user-attachments/assets/df04efde-3ad9-4da2-9d0e-7e35d8ca7ac9)

```
np.log(df['Highly Negative Skew'])
```

![image](https://github.com/user-attachments/assets/43cc4e8d-5012-4b83-8d08-753c5d02951b)

```
np.sqrt(df['Highly Negative Skew'])
```
```
np.reciprocal(df['Highly Negative Skew'])
```

![image](https://github.com/user-attachments/assets/46f6e6ce-cf83-4e87-b38a-ae16b31e8060)

```
np.square(df['Highly Negative Skew'])
```


![image](https://github.com/user-attachments/assets/44d1271b-931a-4407-8ac4-e28c8248e6cb)

```
df['Highly Positive Skew_boxcox'],parameters=stats.boxcox(df['Highly Positive Skew'])

df
```

![image](https://github.com/user-attachments/assets/92ac1792-885c-4d0d-97f5-5676b0495fc9)

```
import seaborn as sns
import matplotlib.pyplot as plt
import statsmodels.api as sm
```

```
sm.qqplot(df["Moderate Negative Skew"],line='45')
plt.show()
```

![image](https://github.com/user-attachments/assets/3db7be83-450e-46d4-bcba-389cb85f6c5e)

```
sm.qqplot(np.reciprocal(df["Moderate Negative Skew"]),line='45')
plt.show()
```

![image](https://github.com/user-attachments/assets/d35ee720-cd38-4bc1-84b3-c07e29297d7e)







## RESULT:
      Thus, performing Feature Encoding and Transformation process for the given data set is completed.

       
