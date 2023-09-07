# Predictive Analysis on Housing Pricing using Python Learning Model
In this demo, Miami Housing dataset was downloaded from Kaggle to perform predicitive analysis on housing prices using existing values. 
<br>
<br>
(1) Import Python Libraries <br>
<img src="https://github.com/hueeylow/python/blob/main/01_import_lib_csv.gif">
<br>
<br>
(2) Well-cleansed dataset with no present null values; a total of 13,932 records, 17 columns.
<img src="https://github.com/hueeylow/python/blob/main/02_check_null_viewshape.gif" width="635">
<img src="https://github.com/hueeylow/python/blob/main/04_check_missing_values.gif">
<br>
<br>
(3) Using Data.head ( ) function to show top dataset
<br>
<img src="https://github.com/hueeylow/python/blob/main/03_view_head_dataset.gif">
<br>
<br>
(4) Using Describe function to view on min/max values, total records etc.
<img src="https://github.com/hueeylow/python/blob/main/05_describe_corr.gif">

(5) Plotting heatmap to understand how values influence the decision
<img src="https://github.com/hueeylow/python/blob/main/06_heatmap.gif">
<br><br>
(6) Linear Regression - Train dataset to perform predicitive analysis<br>
<br>
<img src="https://github.com/hueeylow/python/blob/main/07_linear_regression.gif">
<br>
(7) To split target variable (Sales Price) and independent variables. 80% for training data, 20% for testing data
<img src="https://github.com/hueeylow/python/blob/main/07_split data.gif"><br>

<img src="https://github.com/hueeylow/python/blob/main/08_coeff.gif">
<br>
(8) Train the data to read reference values. Results shown train data accuracy is around ~70%  <br>
<img src="https://github.com/hueeylow/python/blob/main/09_train_data.gif">
<br>
(9) Checking of Normality Error <br>
<img src="https://github.com/hueeylow/python/blob/main/10_normality_error.gif"><br>
(10) Checking Residual. Normal distribution, hence is acceptable
<img src="https://github.com/hueeylow/python/blob/main/11_residuals.gif">
<br>
Evaluate results. Both test and train accuracy scores are ~90%.
<img src="https://github.com/hueeylow/python/blob/main/12_predict_test_data_evaluation.gif">
<br>
<a href="https://github.com/hueeylow"> < Back to main page </a>
