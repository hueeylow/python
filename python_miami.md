# Predictive Analysis on Housing Prices using Python Learning Model
<br>
In this project demo, Miami Housing Prices dataset (obtained from Kaggle) will be used to perform predicitive analysis on housing prices based on historical values. 
<br> <br>
<b>(1) Import Python Libraries and .csv data file<br><br> </b>
The necessary libraries to be imported are: <br> 

- Pandas  (For dataframes)<br>
- Numpy (To perform math computations)<br> 
- Scikit-Learn (For regression modelling)<br>
- MatPlotlib (For plotting charts)<br>
- Seaborn (For visualization on top of MatPlotlib) <br>
<img src="https://github.com/hueeylow/python/blob/main/01_Import_Lib_CSV.gif" width="635">
<br>
<b> (2) Assess Data Quality </b><br>  <br>
  It is manadatory good practice to assess the data quality before using. Typically data cleaning is applied to fix wrong data, removing duplicates, data in wrong format and empty cells. The dataset used in this demo does not required any further action of data cleaning. I will show steps on data-cleaning in next post. Let's now proceed for data exploration. <br><br>
<img src="https://github.com/hueeylow/python/blob/main/02_CheckNull.gif" width="635">
<img src="https://github.com/hueeylow/python/blob/main/03_CheckMissingValue.gif" width="635">

<b> (3) Using Describe( ) function to view min/max value & total records of each attribute in the dataset</b><br> <br> 
This function is called to return descriptions that I am interested to know - min/max value, total records of each attribute in the dataset.<br><br>
<img src="https://github.com/hueeylow/python/blob/main/04_CheckMissingValue.gif">
<br>

<b> (4) Scatterplot to show correlation between Sales Price and Floor Area</b><br>  <br>
The scatterplot explains that coordinate points shifting to the right would mean increasing floor area tend to have higher asking price.<br><br>
<img src="https://github.com/hueeylow/python/blob/main/05_TotalLvgArea_SalesPrice.gif">
<br>

<b> (5) Histogram Overview of all Variables </b><br>  <br>
<img src="https://github.com/hueeylow/python/blob/main/06_Histogram1.gif">
<img src="https://github.com/hueeylow/python/blob/main/06_Histogram2.gif">

<br>

<b> (6) To split target variable and independent variables </b><br> 

Sales Price is set as target variable to predict future housing price using rest of the dataset. I used train/test/split method by importing scikit-learn library to aid in dividing features data (X_data) and target data (y_data), and subsequently put them into train and test variables. In this demo, 80% of data will be used to train model for predictive analysis; 20% of data will used as test data.<br> <br> 
<img src="https://github.com/hueeylow/python/blob/main/07_Split_Data.gif" width>

<br>

<b> (7) Train the model using Linear Regression </b><br>  <br>
Liner regression method uses relationship between data-points to form a straight line through, and at such it predict the future values.
<br><br>
<img src="https://github.com/hueeylow/python/blob/main/08_LinearRegression.gif">

<img src="https://github.com/hueeylow/python/blob/main/09_PredictionModel_Output.gif ">
<br>
<b> (8) Heatmap plot of prediction model </b><br>  <br>
Prediction values in the heatmap explains that variables are correlated either -1.0 or +1.0. Closer to 1.0 shows strong positive relationship and vice-versa for -1.0. As the target variable here is sales price, values closer to 1.0 would mean the attribute has high selling price. For example, houses located near to Miami central Business District and Subcenter has the highest selling price. Houses located near the ocean or rail line has lower selling price due to limited amentities and facilities around.<br>
<br>
<img src="https://github.com/hueeylow/python/blob/main/10_Heatmap_PredictionModel.gif">
<br>
<b> (9) Scatterplot of Sales Price vs Floor Area </b><br>  <br>
Scattered data points in red are the most pricey due to bigger floor area and located near to CBD and Subcenters.
<img src="https://github.com/hueeylow/python/blob/main/11_Scatterplot_Sales_Prc.gif">
<img src="https://github.com/hueeylow/python/blob/main/12_Scatterplot_Sales_Prc_Map.gif">

<br>
<b> (10) Checking for Normality Errors </b><br>  <br>
Most of data points fall along straight diagonal line of 45 degrees, thus is assumed that the data is normally distributed.
<img src="https://github.com/hueeylow/python/blob/main/13_Checking_Normality_Errors.gif">

<br>
<b> (11) Checking for Residual </b><br> 
<br>
It is observed that distrbution is normal and evenly spreaded with a bell-shaped peakm and is symmetric around the mean. The mean, median and mode here are equal.<br><br>
<img src="https://github.com/hueeylow/python/blob/main/14_Checking_Residual_1.gif">

<img src="https://github.com/hueeylow/python/blob/main/14_Checking_Residual_2.gif">

<br>
<b> (12) Evaluate the Prediction Model </b><br>
<br>
Four error metrics were used to evaluate the performance of the linear regression model, to show how well the predictive data fit the regresion model: <br>
(1) Root Mean Squared Error (RMSE) <br>
(2) Mean Squared Error (MSE)  <br>
(3) Mean Absolute Error (MAE) <br>
(4) R-Squared (R²) <br>
<br>
From the below computed metrics, it can be concluded that the prediction data is of 70% close fit to the regression model.
<img src="https://github.com/hueeylow/python/blob/main/15_Check_Alogrithm.gif">
<br>

<a href="https://github.com/hueeylow"> < Back to main page </a>
