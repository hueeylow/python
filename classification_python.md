<h1>Classification Prediction with Machine Learning</h1>
<p>Classification is a fundamental machine learning technique used to categorise data into predefined classes based on learned patterns. In the context of disease detection, classification models analyse medical data—such as clinical measurements, symptoms, or diagnostic indicators—to predict whether a patient belongs to a healthy or diseased group. By learning from historical labeled data, these models can support early diagnosis, improve decision-making, and reduce human error. In this project illustration, I will use Hypertension Dataset from Kaggle, to demonstrate how machine learning classification algorithms can be applied to detect Hypertension.</p>
<br>
<b>Import Libraries and Load Data</b><br>

```
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
%matplotlib inline

from sklearn.model_selection import train_test_split
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import (
    accuracy_score,
    precision_score,
    recall_score,
    f1_score,
)
```

```
hypertension_data = pd.read_csv('hypertension_dataset.csv')
```
<b>Preview Dataset, Structures, Check for Null Values</b><br>
<img width="522" height="632" alt="image" src="https://github.com/user-attachments/assets/284bc40c-bc6f-4831-8c5f-9b54cce456d9" />
<br>
<img width="521" height="222" alt="image" src="https://github.com/user-attachments/assets/3f8c45fa-2b21-4572-91d4-74d5a9f55db1" />
<br>The Medication column contained 799 null values. To ensure data completeness and consistency, these missing values will be imputed.<br><br>
<b>Data Cleansing - Impute Null data fields</b><br>
<img width="537" height="256" alt="image" src="https://github.com/user-attachments/assets/40fd3254-77b7-4631-b57b-d5974e296d83" />
<br>
<p>After data imputation, let's analyse the dataset for stats on patients with Hypertension</p>

```
# Analyze the class distribution
class_counts = hypertension_data['Has_Hypertension'].value_counts()
print("Class Distribution:")
print(class_counts)
```
<img width="622" height="82" alt="image" src="https://github.com/user-attachments/assets/711416e4-86fe-4147-934d-269548eec039" />

```
# Visualize the class distribution
plt.bar(class_counts.index, class_counts.values, color='skyblue')
plt.xlabel('Has_Hypertension')  # Set x-axis label
plt.ylabel('Count')  # Set y-axis label
plt.title('Class Distribution')
plt.show()
```
<img width="517" height="406" alt="image" src="https://github.com/user-attachments/assets/57ea37f3-96dc-4547-8c92-1655b160f2ab" />
