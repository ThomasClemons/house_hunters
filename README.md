# house_hunters

# Eploration and Clean up of data

We had a long discussion and decided to focus our project on Housing.
We decided that we were a Real Estate firm and that we had some homes on the market, but we were unsure about pricing.
So we searched several sites, like data.world, kaggle and data.gov and we ended up finding a data set on Kaggle, with information on homes in Iowa

# Data Model Implementation
Our team created data prep Notebook (Thomas’s Notebook) ‘data_preparation.ipynb’
    - We then narrowed data set down by going through each column using value_counts and identifying columns that weren’t needed and deleted them in the               ‘cols_to_delete’ variable. 
    - We converted nulls to "Does not have"
    - We chose these columns because they were very heavily weighted (>=90%) into 1 datapoint in the category. 

We then created a VIF notebook (Gi’Anna’s Notebook) 'initial_VIF' that separated out the columns that only had numerical values
    - Split and then scaled the split data. We learned that if you scale before you split the data, then you are leaking information to the test data (which             technically doesn’t exist yet), which can create a biased test set.
    - We removed the 5 columns with VIF > 10 (standard). These had too much correlation to the other data points. High values of VIF mean that the strength of         the relationship is extremely high and it can skew the data set and needs to be removed.
    - Ran linear regression and r2
    - Generated Initial VIF

After this, we had further discussion on what additional columns could be removed from the data. 

We also realized that we needed to label encode the string values so that we could run the VIF on the entire data set.

We then created a new notebook, the continue_data_preparation notebook
     - We ran an additional Linear Regression and another VIF and removed all columns with a value > 10
     - We then used OLS to generate p-values to eliminate even more columns that didn't have much importance
     - Finally, we printed to 4 CSV files and used those files in our regression calculations. We read them in to the 4 variables, X_train, X_test, y_train,              y_test.

# Analysis of Data

We ran multiple regressions on the "cleaned up" data. Lasso, Ridge, Random Forest, XGBoost, CatBoost. We graphed them all and came to the conclusion that the CatBoost was the most accurate

Finally we used "feature importances" to identify and graph which attribute of the data set had the biggest effect on the sale price. Thus, answering our objective question