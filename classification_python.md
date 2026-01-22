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
<img width="517" height="406" alt="image" src="https://github.com/user-attachments/assets/57ea37f3-96dc-4547-8c92-1655b160f2ab" /> <br>
The dataset shows a near-balanced distribution, with 1,032 individuals diagnosed with hypertension compared to 953 without hypertension, giving an approximate ratio of 1.08:1. <br><br>
The next step of the analysis examines whether family history of hypertension is associated with an increased risk of developing hypertension.<br>
```
ct = pd.crosstab(
    hypertension_data['Family_History'],
    hypertension_data['Has_Hypertension']
)

# Plot stacked bar chart
ax = ct.plot(kind='bar', stacked=True, figsize=(8,6), color=['#D2B48C', 'salmon'])

# Title and labels
plt.title('Hypertension with Family History')
plt.xlabel('Family History')
plt.ylabel('Count')
plt.xticks(rotation=90, ha='right')

# Add data labels for each segment
for i, family in enumerate(ct.index):
    cumulative = 0
    for j, col in enumerate(ct.columns):
        count = ct.loc[family, col]
        ax.text(i, cumulative + count/2, str(count), ha='center', va='center', color='white', fontweight='bold')
        cumulative += count

plt.show()

```
<img width="627" height="492" alt="image" src="https://github.com/user-attachments/assets/7929ea4f-a29e-466a-9754-008abc1304d2" />
<br>
The chart shows a clear association between family history and hypertension risk. Among individuals without a family history of hypertension, most do not have hypertension (620 non-hypertension vs 380 hypertension). In contrast, individuals with a family history show a higher prevalence of hypertension, with 652 hypertension cases compared to 333 non-hypertension cases. This indicates that having a family history of hypertension is associated with a significantly increased likelihood of developing hypertension and suggests that family history is an important risk factor in this dataset. <br><br>
<b>Hypertension Risk Prediction with Logistic Regression</b>
<br><br>
Building on earlier observation, I shall use logistic regression to further analyse and predict the risk of hypertension based on relevant factors. First, identify key features (x), including family history and other patient attributes, and then define hypertension as the target variable (y). <br> <br>
<b>Identify Features and Target Variable</b><br>


```
X = hypertension_data[
    [
        'Age', 
        'Salt_Intake', 
        'Stress_Score',
        'BP_History', 
        'BMI', 
        'Medication', 
        'Family_History', 
        'Exercise_Level', 
        'Smoking_Status'
    ]
]
y = hypertension_data['Has_Hypertension'].map({'Yes': 1, 'No': 0})

# Encode Object datatypes from string to interger
X = pd.get_dummies(X,columns=['BP_History','Medication', 'Family_History', 'Exercise_Level', 'Smoking_Status'],dtype=int)
```
<br>
<b>Split and Train Data</b><br>
The data is then split into training and testing sets to ensure robust model evaluation. <br> <br>

```
from sklearn.model_selection import train_test_split

# Split the data
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Check shape of splits
print(f'Shape of X_train: {X_train.shape}')

print(f'Shape of X_test: {X_test.shape}')
```
<img width="272" height="40" alt="image" src="https://github.com/user-attachments/assets/63763546-0f0f-4bae-99e7-dc0bbc0722c2" />
<br> <br>
<b>Logistic Regression Model (Classification Algorithm)</b>
A logistic regression model is then trained on the dataset to learn how these features influence the likelihood of hypertension. 
<br>
```
from sklearn.linear_model import LogisticRegression

model = LogisticRegression(max_iter = 1000)

# Train the model
model.fit(X_train, y_train)
```
Finally, the model is used to make predictions and evaluate its performance, providing insights into which factors most strongly contribute to hypertension risk.
