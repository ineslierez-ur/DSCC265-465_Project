# DSCC265-465_Project

## Links:

Google Drive link for the project: https://docs.google.com/document/d/1TgUiyAbb_-JQzR0_HA7ynGMlvlXvLO3bdSlPZEsts2M/edit?usp=sharing

Link for the data: https://www.kaggle.com/datasets/johnjdavisiv/us-counties-covid19-weather-sociohealth-data?select=us_county_sociohealth_data.csv

Overleaf link for the prospectus: https://www.overleaf.com/4998658811fkkbzhpmkqbc

Overleaf link for the report: https://www.overleaf.com/2164117668xqszsnhmshys

## Pre-Analysis:

### Exploring the data.ipynb

We explore possible data sets available and explore the data set of our choice. We plot correlation matrices.

## 1) Explanatory Analysis:

## 2) Predictive Models:

### Data_sets.ipynb

The input is the data file returned by the explanatory analysis. The outputs are 5 versions of the data: 'X_same_notnormalized.csv' is the given data without location, 'X_same_notnormalized_withlocation.csv'is the given data with location, 'X_same.csv’ is the given data without location but normalized, 'X_same_with_pcs.csv' is the given data without location but normalized and includes principal components, 'X_same_with_location.csv' is 'X_same.csv’ with location. Actually, 'X_same_with_pcs.csv’ is produced later by Prediction_Part1_data_preparation_same.ipynb notebook.

For part 1, the data sets used are: **'X_same_with_pcs.csv’, 'X_same_with_location.csv', and the raw data from Kaggle.**

For part 2, the data sets used are: **'X_same_notnormalized.csv’, and 'X_same_notnormalized_withlocation.csv'.**


## 2.1) Predictive Models Part 1:

## a) For same data:

We use the data cleaned by the explanatory analysis. So the features included are only the ones that have correlation less than 0.6 with one another. The location related columns are removed and the data is normalized. The input file name is **'X_same_with_pcs.csv'** and it is obtained by the preparing_data notebook.

### Prediction_Part1_data_preparation_same.ipynb

We prepare the data for predictive analysis by adding the features obtained by dimensionality reduction techniques of PCA, spectral embedding, and t-SNE. The output file is 'X_same_with_pcs.csv' and it becomes the input file for the rest of the analysis.

### Prediction_Part1_ElasticNet_same.ipynb

We perform ElasticNet regression with various cross validation techniques. We first try by including the dimensionality reduction vectors as features, and then, we try again without them. The best fit returned is stored in **'y_pred_same_withpcs_ElasticNet.csv'**.

### Prediction_Part1_kNN_same.ipynb

We perform k-Nearest Neighbor algorithm and tune the parameter k. The best fit returned is stored in **'y_pred_same_withpcs_kNN.csv'**.

### Prediction_Part1_NN_same.ipynb

We apply NN with 3 layers. We tune the number of nodes for the intermediate layer. We repeat it without the principal components. The best fit returned is stored in **'y_pred_same_withpcs_NN.csv'**.

## b) For same data but including location:

In our analysis, we have realized that socioeconomic features used are actually location dependent. Therefore, in order to improve our predictions and to also have better use of the socioeconomic data we have, we turn the 'fips', 'state', and 'county' columns to numerical values and include them for our prediction models. This is a repetition of the above models but this time also including the location information. We expect to improve our predictions by doing so.

### Prediction_Part1_data_preparation_same_withlocation.ipynb

The above analysis repeated on the data that includes location features. The input file is 'X_same_with_location.csv' and the output file is **'X_same_with_location.csv'**. The output file becomes the input for all the following models.

### Prediction_Part1_ElasticNet_same_withlocation.ipynb

The above analysis repeated for the data set that also contains location related features. The best fit returned is stored in **'y_pred_same_withpcs_withlocation_ElasticNet.csv'**.

### Prediction_Part1_kNN_same_withlocation.ipynb

The above analysis repeated for the data set that also contains location related features. The best fit returned is stored in **'y_pred_same_withpcs_withlocation_kNN.csv'**.

### Prediction_Part1_NN_same_withlocation.ipynb

We apply NN with 3 layers. We tune the number of nodes for the intermediate layer. We repeat it without the principal components. The best fit returned is stored in **'y_pred_same_withpcs_withlocation_NN.csv'**.

## c) For raw data:

Here, we start from the raw data on Kaggle and assume that no explanatory analysis was performed. We build prediction models without focusing on their interpretability.

### Prediction_Part1_data_preparation_pre_analysis.ipynb

While preparing the data before building accuracy-focused predictive models, we explore the data and decide to replace null values with the mean for the state or the column.

### Prediction_Part1_data_preparation.ipynb

This notebook prepares the data to be fed into the predictive models that assumes no prior knowledge or analysis about the data. The output files are the file that contains the target variable and the file that contains all the explanatory features: . We also add columnsfor the 3 principal components returned by dimensionality methods including PCA, spectral embedding, and t-SNE.

## 2.2) Predictive Models Part 2:

## a) For same data:

### Prediction_2_not_normalized_no_location.ipynb
Not normalized features from EDA, with Ridge regression and Random Forest, metrics comparison are in the slides

### prediction_2_normalized_no_location.ipynb
Normalized features from EDA, with Ridge regression and Random Forest, metrics comparison are in the slides

## b) For same data but including location:

### prediction_2_not_normalized_with_location.ipynb

Not normalized data including features from EDA and location, with Ridge regression and Random Forest, metrics comparison are in the slides
