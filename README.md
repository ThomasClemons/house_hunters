# house_hunters
This is a group project the MSU AI Bootcamp.  For this project, we worked as a group to find and analyze a dataset of our choice. The aim of our project is to identify which attributes of this dataset have the biggest effect on the sale price of homes in various neighborhoods of Ames, IA. We’ll examine relationships between various data points and the sale price. We will use this modeling  to predict the sale price of homes that we have in our Real Estate portfolio.

Team house_hunters:  Gi'Anna Cheairs, Tim Carter, Vineet Duggi, Tom Clemons 

## Getting Started

### Dependencies

- Python 3.10
- Python NumPy
- Python Matplotlib
- Jupyter Notebooks

### Installing

- Clone this repo to your environment 

### Notebooks and Data Files 

**Notebooks created for this project:** 
| **Notebook** | **Description** |
| --- | --- | 
| **Data Preparation:** | | 
| **data_preparation.ipynb** | Reads housing data file and performs inital cleansing to create clean data file  |
| **continue_data_preparation.ipynb** | Continue data file cleansing, encoding, scaling, VIF, and p-values analysis to create housing data file used for modeling |
| | |
| **Data Modeling and Predictions:** | | 
| **Regression_models_1.ipynb** | Creates CatBoost, Gradient, and Feature Importance models |
| **Vineets_Regression_models_2.ipynb** | Create KNN, Random Forest, ExtraTrees, ADABoost, and SVR models | 
| **Initial_VIF.ipynb** | Calculates VIF for numerical columns only. |
| **Lasso_Regression.ipynb** | Create Lasso Regression model. | 

**Data files created for this project:** 
| **Data File** | **Description** |
| --- | --- | 
| **data_description.txt** | Describes each data file in the housing dataset  |
| **housing_df_clean.csv** | Initial clean version of housing data file |
| **housing_df_test_clean_revised.csv** | Final clean version of housing data test file used in models |
| **housing_df_train_clean_revised.csv** | Final clean version of housing data training file used in models |
| **housing_df_y_test.csv** | housing test sale prices used in models |
| **housing_df_y_train.csv** | housing training sale prices used in models |
| **test.csv** | housing test dataset downloaded from Kaggle - Not used |
| **train.csv** | housing training dataset downloaded from Kaggle |

**Project Presentations:** 
| **Presentation** | **Description** |
| --- | --- | 
| **House_Hunter-project 2-2.ppt** | Powerpoint version of team presentation |
| **HH presentation.pdf** | PDF version of team presentation |

# Exploration and Clean up of data

- We had a long discussion and decided to focus our project on Housing.
- We decided that we were a Real Estate firm and that we had some homes on the market, but we were unsure about pricing.
- So we searched several sites, like data.world, kaggle and data.gov and we ended up finding a data set on Kaggle, with information on homes in Iowa

# Data Model Implementation
- Our team created data prep Notebook ‘data_preparation.ipynb’
    - We then narrowed data set down by going through each column using value_counts and identifying columns that weren’t needed and deleted them in the               ‘cols_to_delete’ variable. 
    - We converted nulls to "Does not have"
    - We chose these columns because they were very heavily weighted (>=90%) into 1 datapoint in the category. 

- We then created a VIF notebook 'initial_VIF' that separated out the columns that only had numerical values
    - Split and then scaled the split data. We learned that if you scale before you split the data, then you are leaking information to the test data (which  technically doesn’t exist yet), which can create a biased test set.
    - We removed the 5 columns with VIF > 10 (standard). These had too much correlation to the other data points. High values of VIF mean that the strength of  the relationship is extremely high and it can skew the data set and needs to be removed.
    - Ran linear regression and r2
    - Generated Initial VIF

- After this, we had further discussion on what additional columns could be removed from the data. 

- We also realized that we needed to label encode the string values so that we could run the VIF on the entire data set.

- We then created a new notebook, the continue_data_preparation notebook
     - We ran an additional Linear Regression and another VIF and removed all columns with a value > 10
     - We then used OLS to generate p-values to eliminate even more columns that didn't have much importance
     - Finally, we printed to 4 CSV files and used those files in our regression calculations. We read them in to the 4 variables, X_train, X_test, y_train, y_test.

# Analysis of Data

- We ran multiple regressions on the "cleaned up" data. Lasso, Ridge, Random Forest, XGBoost, CatBoost. We graphed them all and came to the conclusion that the CatBoost was the most accurate
- Finally we used "feature importances" to identify and graph which attribute of the data set had the biggest effect on the sale price. Thus, answering our objective question

## Help

- These consolidated full year files will be overlayed if you run the create analysis data file notebooks
- All survey data files are provided in the Resources folder.  You don't need to run the notebooks to create the pulse survey data files unless you make some changes to the create data file notebooks


## Authors

- Authors:  Gi'Anna Cheairs, Tim Carter, Vineet Duggi, Tom Clemons 

## Version History

- 0.1
    - Initial Release

## Acknowledgments

- Ames IA Housing Data - [https://www.kaggle.com/datasets/marcopale/housing](https://www.kaggle.com/datasets/marcopale/housing)

