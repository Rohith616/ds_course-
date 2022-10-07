# Use SelectFromModel to eliminate one or more than one features

In this assignment we will try to implement the one of the multivariate methods of
feature selection.

## Write a function `select_from_model` that:
- Splits the data into X (features except target variable) and y (SalePrice).
- Uses `RandomForestClassifier()` as the model to operate upon and fits the model on X,y.
- Use `get_support()` function to get True/False for each 
feature and return the name of the feature with values assigned as True.

Note : The seed should be set as 9.


## Parameters:

| Parameter | dtype | argument type | default value | description |
| --- | --- | --- | --- | --- | 
| df | DataFrame | compulsory |  | Input DataFrame |



#### Returns:

| Return | dtype | description |
| --- | --- | --- | 
|feature_name |List|List of variables which are retained|
