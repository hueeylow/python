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
hypertension_data = pd.read_csv('hypertension_dataset.csv')
```
