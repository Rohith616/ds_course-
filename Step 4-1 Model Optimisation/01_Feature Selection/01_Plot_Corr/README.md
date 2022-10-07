# Plot a correlogram for all numeric variables

Correlation gives us the idea about how the are the features related to the target variable
and gives us the idea which variables would have significant impact on target variable.

## Write a function `plot_corr` that:
- Plots correlation measure of numeric variables.
- Uses set_cmap to set plot to yellow & red colour 'YlOrRd'.
- Uses Subplot to figsize the size. 
- Print the columns names in X and Y axis using xticks and yticks.

### Parameters:

| Parameter | dtype | argument type | default value | description |
| --- | --- | --- | --- | --- | 
| df | DataFrame | compulsory |  | Input DataFrame |
| size| Integer | optional | 11 | Input size of the graph  |


### Returns:

None
