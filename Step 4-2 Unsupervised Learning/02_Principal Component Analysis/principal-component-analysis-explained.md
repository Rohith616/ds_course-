# Dimension of Data

- The set of features is called the *dimension* of the data 

- We humans live in 3-dimensions
    - so naturally our imagination is limited to 3D
    
- But, the same is not the case for our world of datasets
    - in some cases it may go up to a million

![Multi-Dimensional Cubes](https://user-images.githubusercontent.com/66381316/88981513-c273ce80-d2e3-11ea-82ee-f4a4e702c147.png)

### High Dimensional Data 

- High Dimensional Data means that the number of dimensions is staggeringly high

- With high dimensional data, the number of features can exceed the number of observations

### Example of High Dimension Data

##### *microarrays*
- Microarrays, which measure gene expression, can contain tens of hundreds of samples
    - Each sample can contain tens of thousands of genes
    - One person (i.e. one observation) has millions of possible gene combinations

##### *other high dimension data*
- Other areas where features exceed observations include 
    - finance, 
    - high resolution imaging, and 
    - website analysis (e.g. advertising, crawling, or ranking)

# Problems presented by High Dimensionality Data

- Consider a machine learning scenario with a lot of variables

- Working with a lot of variables can present problems
    - Do you understand the relationships between each variable? 
    - Do you have so many variables that you are in danger of over-fitting your model to your data or 
    - You might be violating assumptions of whichever modeling tactic you’re using?

- At a higher dimension, things don’t quite work the same as the lower space; For example
    - A random point in a unit square has about 0.4% chance to be located less than 0.001 from border
    - Its highly unlikely a point to be located along any extreme point
    - But for a 10,000 dimensional hypercube there is 99.99% probability for a point to lie near border 
    - Average distance between two random points in a unit square is around 0.52 where as for a 1,000,000 dimensional hypercube,it will be more than 400.
    - Now,here comes the question,how can to points be so far when they are in the same unit hypercube. 
    - This means for higher dimension things are going to be very sparse: i.e most training instances may lie very far to each other.

- Also, training of the model becomes really slow, making it harder to find a solution

- Also, it is tough to visualize data with a lot of dimensions

### Curse of Dimensionality

- The curse of dimensionality usually refers to what happens when you add more and more variables to a multivariate model
    - At a higher dimension things don’t quite work the same as the lower space
    - The more dimensions you add to a data set, the more difficult it becomes to predict certain quantities 

- You would think that more is better
    - However, when it comes to adding variables, the opposite is true
    - Each added variable results in an exponential decrease in predictive power

- The statistical curse of dimensionality refers to a related fact:
    - a required sample size n will grow exponentially with data that has d dimensions
    - in simple terms, adding more dimensions could mean that the sample size you need quickly become unmanageable


# Dimensionality Reduction

- You might ask the question, “How do I take all of the variables I’ve collected and focus on only a few of them?” 
    - In technical terms, you want to “reduce the dimension of your feature space.” 

- By reducing the dimension of your feature space, you have fewer relationships between variables to consider and you are less likely to over-fit your model
    - This doesn’t immediately mean that over-fitting, etc. are no longer concerns — but we’re moving in the right direction

- Reduction of dimensionality means to simplify understanding of data, either numerically or visually
    - Data integrity is maintained. 

- To reduce dimensionality, you could combine related data into groups using a tool like multidimensional scaling to identify similarities in data. 
    - You could also use clustering to group items together

- There are many ways to achieve dimensionality reduction, 
    - but most of these techniques fall into one of two classes:
        - "Feature Elimination"
        - "Feature Extraction"

### "Feature Elimination"

- Feature elimination is what it sounds like: 
    - we reduce the feature space by eliminating features
- Advantages of feature elimination methods include simplicity and maintaining interpretability of your variables
- As a disadvantage, though, you gain no information from those variables you’ve dropped
    - Feature extraction, however, doesn’t run into this problem

### "Feature Extraction"

- Say we have ten independent variables
    - we create ten “new” independent variables, where each “new” independent variable is a combination of each of the ten “old” independent variables
    - we create these new independent variables in a specific way and order these new variables by how well they predict our dependent variable
- We keep as many of the new independent variables as we want, but we drop the “least important ones.” 
    - Because we ordered the new variables by how well they predict our dependent variable, we know which variable is the most important and least important
- Also, since, these new independent variables are combinations of our old ones, we’re still keeping the most valuable parts of our old variables, even when we drop one or more of these “new” variables

# Principle Component Analysis (PCA)

- Principal Component Analysis is a technique for Feature Extraction 
    - so it combines our input variables in a specific way, 
    - then, we can drop the “least important” variables while still retaining the most valuable parts of all of the variables
- As an added benefit, each of the “new” variables after PCA are all independent of one another
- This is a benefit because the assumptions of a linear model require our independent variables to be independent of one another.

### When PCA? 


If the answer for all three of the questions below is yes, then use PCA:

1. Do you want to reduce the number of variables, but aren’t able to identify variables to completely remove from consideration?
2. Do you want to ensure your variables are independent of one another?
3. Are you comfortable making your independent variables less interpretable?

### How PCA Works?

- PCA is an unsupervised learning algorithm used mostly as a data preprocessing step before applying it into any model.

- In real world, training instances are not generally spread uniformly across all the dimensions
    - Most of the instances actually lie close to each other
    - So information from dimensions that matter can be extracted

- To decrease the dimension of our dataset
    - Our training set is projected onto a lower-dimensional hyperplane
    - Projected in such a way that most of the information of our data is contained by our algorithm

- Redundant features are eliminated 

![Dimensionality in DataSets](https://user-images.githubusercontent.com/66381316/89219972-6912e480-d5ee-11ea-87fe-8087cc439d1b.gif)

- In the above diagram, we can see maximum variance or maximum data is retained by the PCA 1st dimension axis
- Here PCA 2nd dimension refers to the axis that preserves 2nd highest amount of variance
    - It is orthogonal to the first PCA

### Number of Dimensions

- While projecting the data into hyperplane, how should we choose number of principal component axis? 
    - It is advisable to choose number of dimensions such that it adds up to a sufficiently large portion of the variance (>90%)
- In `scikit` learn we have a parameter `svd_solver` which can be set to full 
    - Thereby the `n_components` can be set as a value in between `0` to `1`
    - This n_components refers to the amount of variance we want to contain
    - For example,if `n_components=0.9` then it means we want to keep 90% of variance while projecting it to a lower dimension.

- Let's look at a chart of PCA analysis, which explains how much variance is covered with increasing number of features considered

![pca-three](https://user-images.githubusercontent.com/66381316/89224179-aa5ac280-d5f5-11ea-8fb5-7a16b1125363.png)

- Here we can see with just 9–10 features/dimensions we can achieve around 99% of variance
    - Hence we can eliminate the other redundant features


### Intuitive Procedure for PCA

- Following is some intuitive context for the math behind PCA 
    - We are going to calculate a matrix that summarizes how our variables all relate to one another
    - We’ll then break this matrix down into two separate components: direction and magnitude.
    - We can then understand the “directions” of our data and its “magnitude” (or how “important” each direction is). 
    
    
##### Example in 2D 

- Let's look at a 2-dimensional dataset, i.e. two features 
    - the two features are distributed across x-axis and y-axis

![pca-four](https://user-images.githubusercontent.com/66381316/89234514-ca947c80-d609-11ea-8c5c-29e36286cf32.png)

- There are two main directions in this data: 
    - the “red direction” and 
    - the “green direction” 
    
- In this case, the “red direction” is the more important one.
    - Given how the dots are arranged, 
        - can you see why the “red direction” looks more important than the “green direction?”

- What would fitting a line of best fit to this data look like?

- We will transform our original data to align with these important directions (which are combinations of our original variables)

- The image below is the same exact data as above, but transformed so that the x- and y-axes are now the “red direction” and “green direction”
    - The x-axis is the Principal Component 1 of the transformed data 
    - The x-axis is the Principal Component 2 of the transformed data 

![pca-five](https://user-images.githubusercontent.com/66381316/89234881-a08f8a00-d60a-11ea-8dbb-6f71b247b342.png)

- What would the line of best fit look like here?

- The visual example here is two-dimensional (and thus we have two "principal components")

- think about a case where our data has more dimensions. By identifying which “directions” are most “important,” we can compress or project our data into a smaller space by dropping the “directions” that are the “least important” 

- By projecting our data into a smaller space, we’re reducing the dimensionality of our feature space
    - But because we’ve transformed our data in these different “directions,” we’ve made sure to keep all original variables in our model

##### Example in 3D

- With three dimensions, PCA is more useful, because it's hard to see through a cloud of data.
- In the example below, the original data are plotted in 3D, but you can project the data into 2D through a transformation no different than finding a camera angle: rotate the axes to find the best angle. 
    - The PCA transformation ensures that the horizontal axis PC1 has the most variation, the vertical axis PC2 the second-most, and a third axis PC3 the least 
    - Obviously, PC3 is the one we drop
- [Example - Principal Component Analysis Explained Visually](https://setosa.io/ev/principal-component-analysis/)

##### Core Intuition

- While PCA is a very technical method relying on in-depth linear algebra algorithms, 
    - it’s a relatively intuitive method when you think about it

- First, the covariance matrix (ZᵀZ) is a matrix that contains estimates of how every variable in Z (matrix of variables) relates to every other variable in Z (matrix of variables)
    - Understanding how one variable is associated with another is quite powerful

- Second, eigenvalues and eigenvectors are important. 
    - Eigenvectors represent directions. 
    - Think of plotting your data on a multidimensional scatterplot. 
    - Then one can think of an individual eigenvector as a particular “direction” in your scatterplot of data. 
    - Eigenvalues represent magnitude, or importance. Bigger eigenvalues correlate with more important directions.

- Finally, we make an assumption that more variability in a particular direction correlates with explaining the behavior of the dependent variable.
    - Lots of variability usually indicates signal, whereas little variability usually indicates noise. 
    - Thus, the more variability there is in a particular direction is, theoretically, indicative of something important we want to detect. 
    - The [setosa.io](setosa.io) PCA applet is a great way to play around with data and convince yourself why it makes sense

- Thus, PCA is a method that brings together:
    - A measure of how each variable is associated with one another (Covariance matrix)
    - The directions in which our data are dispersed (Eigenvectors)
    - The relative importance of these different directions (Eigenvalues)

- PCA combines our predictors and allows us to drop the eigenvectors that are relatively unimportant

### PCA Mathematics for the inclined

- Mathematically, the process of obtaining principle components from a raw dataset can be simplified in six parts :
    1. Take the whole dataset consisting of *d+1* dimensions and ignore the labels such that our new dataset becomes d dimensional
    2. Compute the mean for every dimension of the whole dataset
    3. Compute the covariance matrix of the whole dataset
    4. Compute eigenvectors and the corresponding eigenvalues
    5. Sort the eigenvectors by decreasing eigenvalues and choose *k* eigenvectors with the largest eigenvalues to form a *d × k* dimensional matrix *W*
    6. Use this *d × k* eigenvector matrix to transform the samples onto the new subspace


# Application of PCA

- Encoding data in a way that is not identifiable
    - where the information privacy needs to be maintained
- Example of use of PCA in Data Masking - [Lizuna: The Use of Principal Component Analysis to Mask Sensitive Data in Machine Learning](https://medium.com/lizuna/beacon-the-use-of-principal-components-analysis-to-mask-sensitive-data-in-machine-learning-7904b01445d0)

***

# Additional Reading

- [Eigenvalue](https://mathworld.wolfram.com/Eigenvalue.html#:~:text=Entries%20%3E%20Interactive%20Demonstrations%20%3E-,Eigenvalue,Marcus%20and%20Minc%201988%2C%20p.)
- [Eigenvectors and Eigenvalues — All you need to know](https://towardsdatascience.com/eigenvectors-and-eigenvalues-all-you-need-to-know-df92780c591f)
- [Dimensionality & High Dimensional Data: Definition, Examples, Curse of](https://www.statisticshowto.com/dimensionality/)
- [Curse Of Dimensionality and PCA](https://medium.com/@adityamohanty/curse-of-dimensionality-and-pca-f90f1258a7f2)
- [A One-Stop Shop for Principal Component Analysis](https://towardsdatascience.com/a-one-stop-shop-for-principal-component-analysis-5582fb7e0a9c)
- [Principal Component Analysis 4 Dummies: Eigenvectors, Eigenvalues and Dimension Reduction](https://georgemdallas.wordpress.com/2013/10/30/principal-component-analysis-4-dummies-eigenvectors-eigenvalues-and-dimension-reduction/)
- [PCA Playground](https://setosa.io/ev/principal-component-analysis/)