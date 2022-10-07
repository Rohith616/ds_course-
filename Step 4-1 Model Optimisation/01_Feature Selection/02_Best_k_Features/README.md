# Find most informative features with incorporation of k percentile method.

That's quite an impressive streak you have achieved.

Now let's look at most important features.Since you have learned the technique of selecting `k best features` in lecture.
Here, by doing this assignment you can learn how to implement techniques such as `k percentile` feature selection
which would give you most important features falling in k-th percentile.


## Write a function `percentile_k_features` that:
- Splits the data into predictors (features except target variable) and target variable (SalePrice).
- Uses `f_regression` model and `fit_transform` method on predictors and target
- Should return list of best features with implementation of k percentile method.


### Parameters:

| Parameter | dtype | argument type | default value | description |
| --- | --- | --- | --- | --- | 
| df | DataFrame | compulsory |  | Input DataFrame |
| k| integer | Optional | 20 | number as int for number of best features falling under k-th percentile |




### Returns:

| Return | dtype | description |
| --- | --- | --- | 
|list |List|List of important features falling under k-th percentile|

