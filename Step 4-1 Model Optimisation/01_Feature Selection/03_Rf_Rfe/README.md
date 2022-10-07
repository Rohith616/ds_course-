# Use RandomForest RFE to eliminate one or more than one features

You can build a good model just by fewer features rather than including all of them.
Hence, the elimination of features in order to get most significant features can be achieved by using RFE.  This assignment will help you learn to create your own Recursive Feature Elimination function
and help you decide which features are irrelevant and hence can be eliminated. 

## Write a function `rf_rfe` that:
- Uses `RandomForestClassifier()` as the model to operate upon and fits the model on X,y.
- Use `rfe.ranking_` to get 1st rank and return their name(use for loop for recursive iteration for all features).
- Gives out most significant features which are retained.

Note : While using `RFE` method set `n_features_to_select` as half of the total columns or features in X.

### Parameters:

| Parameter | dtype | argument type | default value | description |
| --- | --- | --- | --- | --- | 
| df | DataFrame | compulsory |  | Input DataFrame |


### Returns:

| Return | dtype | description |
| --- | --- | --- | 
|top_features |List|List of variables which are retained|
