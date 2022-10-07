# <u>**Model Selection(Cross-Validation) & Hyperparameter Tuning**</u>
--
![](https://i.pinimg.com/originals/ca/6e/12/ca6e12c8584d9ede619807d86ea7fba0.jpg)
## 1.Introduction:
The goal of supervised learning is to learn from past patterns in the data in order to enable us to make predictions. Data always has variability in it. Some of it can be attributed to the independent variables and is explainable depending on the model specification. The other part is often random variation that may occur due to various reasons. The key part here is that this random variation cannot be explained by the model. This kind of variation is also not something consistent across datasets.

A model trained on one dataset need not perform well on new external test data. On other test sets it may perform better if the random variation is in favour of the model. We need a model that can generalise well such that the true pattern in the population is captured by the model. This requires tuning the model with the right hyperparameter values. For this we use cross validation techniques.

The main questions we want to answer are simple ones:
- How accurate is my model?
- Does the model perform well on data that was not used for training? 

The next step depends on whether only one model or several models need to be evaluated.

#### 1.1.Data Splitting:
Training a single model is quite straightforward. We split the data into two datasets:

1. Training data for the model fitting
2. Testing data for estimating the model’s accuracy

If we had several models to test, the data should be split into two a **training** set of around 70% and equal halves for **validation** and **testing**.
***(Validation data set for the Cross-Validation that we will discuss in this section.)***

Say for example, several similar models are created with changes in specific hyperparameters for each model. This is to gauge the impact on the each model. Every single model will show different accuracy scores.

Let’s assume more specifically that there are exactly 20 models, each one is characterized by having different hyperparameters compared to all other models.

At this point, we trained 20 models on the same training data. Each model will provide its very own accuracy, some will do good, others won’t. The question now is, how can we choose the best model and how can we estimate the “true” accuracy of the model?

## 2.Model Selection(By Cross-Validation):

### 2.1.Choose the right model:
As we currently look at 20 models that are only aware of the training data, we validate them all on the validation data set. Through this step, we are provided with accuracy scores for each model based on their performance on the validation data. We simply choose the one with the highest score.

Cross validation is a technique used to identify how well our model performed.<br>
There is always a need to test the accuracy of our model to verify that our model is well trained with data without any overfitting and underfitting. This process of validation is performed only after training the model with the training data.<br>
##### First, let us understand the terms overfitting and underfitting.<br>

### 2.2.Overfitting:
Overfitting happens when a model learns the detail and noise in the training data to the extent that it negatively impacts the performance of the model on new data. This means that the noise or random fluctuations in the training data is picked up and learned as concepts by the model. The fitted line will go exactly through almost every point in the graph and this may fail to make predictions on our test data.

Specifically, overfitting occurs if the model or algorithm shows low bias but high variance.  Overfitting is often a result of an excessively complicated model, and it can be prevented by fitting multiple models and using validation or cross-validation to compare their predictive accuracies on test data.<br>
![Overfitting , underfitting & robust/good fitting](https://miro.medium.com/max/1125/1*_7OPgojau8hkiPUiHoGK_w.png)

### 2.3.Underfitting:
Underfitting means our model doesn’t fit well with the data and occurs when a statistical model or machine learning algorithm cannot adequately capture the underlying structure/trend of the data.<br>
An underfitted machine learning model is not a suitable model and will be obvious as it will have poor performance on the training data.<br>
Specifically, underfitting occurs if the model or algorithm shows low variance but high bias.  Underfitting is often a result of an excessively simple model.<br>
Underfitting is often not discussed as it is easy to detect with a good performance metric. The remedy is to move on and try alternate machine learning algorithms. Nevertheless, it does provide a good contrast to the problem of overfitting.<br>

### 2.4.Cross-Validation:
Cross validation is a technique which gives our model the opportunity to train on multiple train-test splits. This gives us a better indication of how well our model will perform on unseen data. 
Cross validation is about validating the model, not estimating or improving the accuracy/performance.
<br>
We cannot assume that the performance based on the validation set is the true accuracy. Why? Recall short monologue about random and explainable effects. The best model (in terms of highest accuracy) may be good, but it may also have (significantly) benefited from random patterns in the split dataset.

Basically Cross Validation is a technique which involves reserving a particular sample of a dataset on which we do not train the model. Later, we test our model on this sample before finalizing it.

Here are the steps involved in cross validation:

- We reserve a sample data set
- Train the model using the remaining part of the dataset
- Use the reserve sample of the test (validation) set for cross validation. 

This will help you in gauging the effectiveness of our model’s performance. If our model delivers a positive result on validation data, go ahead with the current model.<br>

**There are several types of Cross-Validation(CV) Techniques:**

- Leave p-out cross-validation
- Leave one-out cross-validation
- Holdout cross-validation
- k-fold cross-validation
- Time Series cross-validation
- Nested croos-validation etc.

**Here, we will learn about Holdout cross-validation & k-fold cross validation.**
### 2.5.Holdout cross validation:

This is the “simplest kind of cross-validation”. This method is often classified as a type of “simple validation, rather than a simple or degenerate form of cross-validation”. In this method, we randomly divide our data into two: Training and Test/Validation set i.e. a hold-out set. We then train the model on the training dataset and evaluate the model on the Test/Validation dataset. The model evaluation techniques used on the validation dataset to compute the error depends on the kind of problem we are working with such as MSE being used for Regression problems while various metrics providing with the misclassification rate helping in finding the error for classification problems. Typically the training dataset is bigger than the hold-out dataset. Typical ratios used for splitting the data set include 60:40, 80:20 etc. This method is only used when we only have one model to evaluate and no hyper-parameters to tune.<br>
![Holdout cross validation](https://datavedas.com/wp-content/uploads/2018/04/image001.jpg)
The limitation of such a method is that the error found in the test dataset can highly depend on the observations included in the train and test dataset. Also if the train or test dataset are not able to represent the actual complete data then the results from the test sets can be skewed. This method is not effective for comparing multiple models and tuning their hyperparameters which leads us to another very popular form of the hold-out method which includes the splitting of data into not two, but multiple separate sets.

### 2.6.k-fold cross validation:
In case of k-fold corss validation, we randomly divide the dataset into k equal sized parts where we leave out one part as the test set and fit the model on using all the other combined k-1 parts as training data. We then evaluate the model on the part that is the test set. This process is repeated k times so each part is used as testing set. The results from each fold are then combined and averaged to come up with the final error.<br>

For example, if we choose the value of k to be 5 then we will have 5 iterations wherein each iteration, the whole dataset will be divided into 5 equal parts and model will be trained on 4 parts and evaluated on the fifth part. The same will be done in other iterations also with the exception of the testing set which will be belonging to a different part. This way we are able to reduce the bias and variance in a way that the model doesn’t overfit or underfit(**that means we can handle both random and real effects on data**).
![k-fold cross-validation](https://miro.medium.com/max/2736/1*rgba1BIOUys7wQcXcL4U5A.png)
If we have more than one model, for example, have 3 models to validate: Logistic Regression, Decision Trees and KNN, then the above step will run separately for each of these models. Thus, we will have 3 × 5 iterations and we will give 3 generalization error values to choose from.
![k-fold_cross_validation](https://datavedas.com/wp-content/uploads/2018/04/image005.jpg)
As mentioned earlier, we want to use the validation techniques not only to find the best model but also to optimize the hyper-parameters. We can understand this with an example.

E.g.- We are dealing with a binary classification problem. We have three models KNN, Decision Trees and Support Vector Machines and we want to know the best model for our data made up of 10,000 samples. We also need to tune hyperparameters(**We will learn about hyperparameter tuning in the next topic**) such as K for KNN, C for Support Vector Machines and Depth of Trees for Decision Trees. <br>

Let us start with KNN where we have the hyperparameter K with possible values of 3, 4 and 5. We begin by setting the value of K (hyperparameter) at 3. We perform k-Fold cross-validation with k=5 and split the data into 5 folds. Then we perform 5 iterations wherein each iteration, we train the KNN model (with hyperparameter K being 3) on the combined k-1 parts and evaluate the model on the remaining fold. We do this step for four more times so that each fold has been once considered as the test set. All the results(generalization errors) produced from these 5 iterations are then averaged and we get the result for the value of hyperparameter K=3. We then repeat the whole process with the value of hyperparameter K being 4 and then again with K being 5.<br>

***Note: Do not confuse K with k, K is the hyperparameter of KNN, while k stand for the value of k in the k-fold cross-validation.***<br>
We then compare these 3 results and chose the best value of K for KNN. As we have two more models, we perform all the above-mentioned steps for each value of their hyper-parameter. Thus, if we have to choose from C=1,2, and 3 (SVM), K=3, 4 and 5(KNN) and Depth of Trees= 6,7 and 8 (Decision Trees) then we will have 9 generalization error values and we will select the one that provides us with the minimum error. This way we not only select the best hyperparameter and model but also evaluate the best model.<br>

However, this method has a potential problem. As we are using the same test set to optimize the parameters as well as evaluate the selected model, we make the model vulnerable to overfitting as our model evaluation can be biased and show “artificial good results”. Thus, the test set used to select the hyperparameters and model cannot be used to evaluate the final model. This leads us to use the nested cross-validation.

### 2.7.Nested K-Fold Cross Validation:
We discussed in Holdout Cross Validation, that splitting the data into train and test is not sufficient and splitting data into train, validation and test is more effective in order to produce more unbiased results. Nested cross-validation uses this concept. It uses a series of train, validation and test splits. In nested cross-validation, we have an inner k-fold cross-validation that is equivalent to the train-validation partition which performs the task of optimizing the hyperparameters and selecting the best model and we also have an outer k-fold cross validation which is equivalent to the validation-test partition and evaluates the model selected during the inner k-fold cross-validation.
![nested k-fold cross-validation-1](https://i.stack.imgur.com/vh1sZ.png)
![Nested k-fold cross-validation-2](https://ndownloader.figshare.com/files/14447486/preview/14447486/preview.jpg)
## 3.Hyperparameter Tuning:
Hyperparameters are hugely important in getting good performance with models. In order to understand this process, we first need to understand the difference between a model parameter and a model hyperparameter.<br>

**Model parameters** are internal to the model whose values can be estimated from the data and we are often trying to estimate them as best as possible They are estimated by optimization algorithms(Gradient Descent).<br>

**Hyperparameters** are external to our model and cannot be directly learned from the regular training process. These parameters express “higher-level” properties of the model such as its complexity or how fast it should learn.They are estimated by hyperparameter tuning.<br>
**Hyperparameters are model-specific properties that are ‘fixed’ before you even train and test your model on data.**<br>

The process for finding the right hyperparameters is still somewhat of a dark art, and it currently involves either random search or grid search across Cartesian products of sets of hyperparameters.<br>

#### ***(Here we will discuss about two popular methods( Grid search and random search)***)
### 3.1.Grid Search:
Grid search is arguably the most basic hyperparameter tuning method. GridSearch takes a dictionary of all of the different hyperparameters that you want to test, and then feeds all of the possible combinations through the model for you and evaluating each model and then reports back to you which one had the highest accuracy.

**For example**, we would define a list of values in dictionary to try for two random forest's hyperparameter (***n\_estimators and max\_depth***) and a grid search would build a model for each possible combination.

Performing grid search over the defined hyperparameter space 

```
n_estimators = [10, 50, 100, 200]
max_depth = [3, 10, 20, 40]
```

would yield the following models.

```
RandomForestClassifier(n_estimators=10, max_depth=3)
RandomForestClassifier(n_estimators=10, max_depth=10)
RandomForestClassifier(n_estimators=10, max_depth=20)
RandomForestClassifier(n_estimators=10, max_depth=40)

RandomForestClassifier(n_estimators=50, max_depth=3)
RandomForestClassifier(n_estimators=50, max_depth=10)
RandomForestClassifier(n_estimators=50, max_depth=20)
RandomForestClassifier(n_estimators=50, max_depth=40)

RandomForestClassifier(n_estimators=100, max_depth=3)
RandomForestClassifier(n_estimators=100, max_depth=10)
RandomForestClassifier(n_estimators=100, max_depth=20)
RandomForestClassifier(n_estimators=100, max_depth=40)

RandomForestClassifier(n_estimators=200, max_depth=3)
RandomForestClassifier(n_estimators=200, max_depth=10)
RandomForestClassifier(n_estimators=200, max_depth=20)
RandomForestClassifier(n_estimators=200, max_depth=40)
```
The main disadvantage of the grid search is, "Each model would be fit to the training data and evaluated on the validation data. As you can see, this is an exhaustive sampling of the hyperparameter space and can be quite inefficient." But the time complexity for this is less with respect to other hyperparameter tuning methods.
### 3.2.Random Search:
Random search differs from grid search in that we longer provide a discrete set of values to explore for each hyperparameter; rather, we provide a statistical distribution for each hyperparameter from which values may be randomly sampled.

One of the main theoretical backings to motivate the use of random search in place of grid search is the fact that for most cases, hyperparameters are not equally important.

> A Gaussian process analysis of the function from hyper-parameters to validation set performance reveals that for most data sets only a few of the hyper-parameters really matter, but that different hyper-parameters are important on different data sets. This phenomenon makes grid search a poor choice for configuring algorithms for new data sets. - [Bergstra, 2012](https://jmlr.csail.mit.edu/papers/volume13/bergstra12a/bergstra12a.pdf)

We'll define a sampling distribution for each hyperparameter.

```
from scipy.stats import expon as sp_expon
from scipy.stats import randint as sp_randint

n_estimators = sp_expon(scale=100)
max_depth = sp_randint(1, 40)
```
We can also define how many iterations we'd like to build when searching for the optimal model. For each iteration, the hyperparameter values of the model will be set by sampling the defined distributions above. The time complexity for the random search method will depends on the total number of iterations & it is greater than grid search method.<br>

In the following example, we're searching over a hyperparameter space where the one hyperparameter has significantly more influence on optimizing the model score - the distributions shown on each axis represent the model's score. In each case, we're evaluating nine different models. The grid search strategy blatantly misses the optimal model and spends redundant time exploring the unimportant parameter. During this grid search, we isolated each hyperparameter and searched for the best possible value while holding all other hyperparameters constant. For cases where the hyperparameter being studied has little effect on the resulting model score, this results in wasted effort. Conversely, the random search has much improved exploratory power and can focus on finding the optimal value for the important hyperparameter.

![](https://i.stack.imgur.com/cIDuR.png)<br>
As you can see, this search method works best under the assumption that not all hyperparameters are equally important. While this isn't always the case, the assumption holds true for most datasets. 
