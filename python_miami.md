# Predictive Analysis on Housing Price using Python Learning Model

<br>
In this demo, Miami Housing dataset was downloaded from Kaggle to perform predicitive analysis on housing prices using existing values. Below is a walkthrough on approach taken to show data relations; training data to generate predictive analysis and testing of results accuracy rate.
<br>
<br>
(1) Import Python Libraries <br>
<img src="https://github.com/hueeylow/python/blob/main/01_import_lib_csv.gif">
<br>
(2) Well-cleansed dataset with no present null values; a total of 13,932 records, 17 columns.
<img src="https://github.com/hueeylow/python/blob/main/02_check_null_viewshape.gif" width="635">
<img src="https://github.com/hueeylow/python/blob/main/04_check_missing_values.gif">
<br>
(3) Using Data.head ( ) function to show top dataset
<br>
<img src="https://github.com/hueeylow/python/blob/main/03_view_head_dataset.gif">
<br>
(4) Using Describe function to view on min/max values, total records etc.
<img src="https://github.com/hueeylow/python/blob/main/05_describe_corr.gif">
<br>
(5) Heatmap plot on correlation between variables
<br>
<br>
<b>Analysis </b><br>
Correlation ranges from -1.0 to 1.0. Values nearer to zero shows that there is no linear trend between the two attributes. Attributes with values close to 1.0 shows strong and positive correlations, likewise for close to -1 shows weak correlations. For instance, total living area vs sale price has 0.7 value, thus is also logical to denote that the bigger living area are more pricer. Houses in central and subcenters regions are pricer than those in railway and ocean regions. <br>
<br>
<img src="https://github.com/hueeylow/python/blob/main/06_heatmap_1.gif">
<br>
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
<img src="https://github.com/hueeylow/python/blob/main/10_normality_error.gif"><br> <br>
(10) Checking Residual <br> There is symmetry pattern observed in the histogram chart that indicate a normal distribution.
<img src="https://github.com/hueeylow/python/blob/main/11_residuals.gif">
<br>
(11) Evaluated results. Both test and train data accuracy scores ~90%.
<img src="https://github.com/hueeylow/python/blob/main/12_predict_test_data_evaluation.gif">
<br>
<a href="https://github.com/hueeylow"> < Back to main page </a>
