# Goal 


## [Feature Selection](1_Feature_Selection.ipynb)

# Feature Selection Techniques 

Welcome to the feature selection module which concerns of Selection
in a large data set consisting of one or more than one features which are either redundant or irrelevant
and thus can be removed without incurring much loss of information.

## What we have learnt so far 

* What is Feature Selection
* Why Feature Selection
* Univariate Feature Selection
* Multivariate Feature Selection


## What we will learn by solving this assignment?

* How are the features important to our model.
* How to select the most significant features out of many.
* How to perform univariate feature selection.
* How to perform multivariate feature selection.
- Note : The data has been provided in the CSV format [here](House_Prices_Multivariate.csv) 

Now, let's take this forward and increase our understanding of feature selection!

This assignment is a series of simple tasks, in which we will be perfoming feature selection techniques on the house pricing data.
## [01 Plot_Corr](01_Plot_Corr)
- Plots correlation measure of numeric variables.
- Uses set_cmap to set plot to yellow & red colour 'YlOrRd'.
- Uses Subplot to figsize the size. 
- Print the columns names in X and Y axis using xticks and yticks.
## [02 Best k Features](02_Best_k_Features)
- Splits the data into predictors (features except target variable) and target variable (SalePrice).
- Uses `f_regression` model and `fit_transform` method on predictors and target
- Should return list of best features with implementation of k percentile method.
## [03 Rf_Rfe](03_Rf_Rfe)
- Uses `RandomForestClassifier()` as the model to operate upon and fits the model on X,y.
- Use `rfe.ranking_` to get 1st rank and return their name(use for loop for recursive iteration for all features).
- Gives out most significant features which are retained.
## [04 Select From Model](04_Select_From_Model)
- Splits the data into X (features except target variable) and y (SalePrice).
- Uses `RandomForestClassifier()` as the model to operate upon and fits the model on X,y.
- Use `get_support()` function to get True/False for each 
feature and return the name of the feature with values assigned as True.
## [05 Forward Selected](05_Forward_Selected)
- Start with no variables in the model.
- For all predictors not in the model, check their r2 score if they are added to the model. Choose the one
with highest r2 score.
- Continue until no new predictors can be added.
