# Ensemble Learning: Bagging& Boosting
### Introduction to Ensemble Learning
Ensemble models in machine learning combine the decisions from multiple models to improve the overall performance. This can be achieved in various ways, which we will learn in this article.
![Fig1:Emsemble learning](https://www.kdnuggets.com/wp-content/uploads/ensemble-framework-packt.jpg)
>Let's take one example:
Take the classic tale of six blind men and the elephant. Each person grabs a different part of the elephant. As a result each comes up with very different descriptions for the elephant. In isolation none of the descriptions are accurate, but put together they do describe an elephant. Even though every description was true in some sense, with some discussion they could have come to some consensus about what an elephant was. This would have yielded a much more accurate description. This more or less describes the process of ensemble learning. 

The main principle behind the ensemble learning is that a group of weak learners come together to form a strong learner, thus increasing the accuracy of the model. When we try to predict the target variable using any machine learning technique, the main causes of difference in actual and predicted values are noise, variance, and bias. Ensemble helps to reduce these factors (except noise, which is irreducible error).
![](https://miro.medium.com/max/2400/1*c9LGSmLiFdM5EcehnsfqrA.png)
Depending on the model and how it fits the data we may have the problem of either bias or variance. In other words the model either under-fits or over-fits the training data. This means that the model does not generalise well and does not pick up the general pattern. Training error and generalization error has gap which is represent as Generalization gap, which is show’s that model is under-fit or over-fit. Ensemble learning helps in reducing the generalisation gap. Bagging helps models with high variance generalise better and boosting helps models with high bias extract more information from the data. 
> Note: Ensemble learning increases the computational complexity compared to individual classifiers which can help us to implement a strong predictive model.
### Types of Ensemble Learningb
The two most popular ensemble techniques
- 1)Bagging(Parallel Ensemble Technique)
- 2)Boosting(Sequential Ensemble learning)

Additionally we will also have a look at an overview of stacking. It is not in as much use as the bagging and boosting algorithms in practice but worth a mention.

### (1)Bagging(Bootstrap Aggregation):
Bagging which is also known as **Bootstrap Aggregation**. It works on the principle of majority voting. The idea behind bagging is combining the results of multiple models to get a generalized result. This works in two parts -

> Bootstrapping is a sampling technique in which we create subsets of observations from the original dataset, with replacement. The combined size of the subsets is the less than or equal to that of the original set.
> The idea here is that since each sample is different and independent of each other, the same model on each sample will lead to variable performance.

#### Process:
- Multiple sub samples are created from the original dataset, selecting observations with replacement. These samples are selected at random.
- A base model is fit to each of these samples. Each individual model is a weak learner, i.e., the performance of each model is just a little above 50%.
- The models run in parallel and are independent of each other.
- The individual predictions are aggregated(Voting or averaging etc.)
- The final result is then used as prediction. It is a simple majority in case of a classification problem. In case of a regression, it is the averaged prediction. 
- It reduces the variance in model performance and generalises well.
![](https://miro.medium.com/max/850/1*_pfQ7Xf-BAwfQXtaBbNTEg.png)

The only parameters when bagging decision trees is the number of samples and hence the number of trees to include. This can be chosen by increasing the number of trees on run after run until the accuracy begins to stop showing improvement. Very large numbers of models may take a long time to fit, but will not over fit the training data.
###### Algorithms: Random Forest, Bagged Decision Trees, Extra Trees
#### 1.1.Random Forest:
Random Forest is an ensemble machine learning algorithm that follows the Bagging technique on decision trees.
The base estimators in random forest are decision trees. It randomly selects a set of features which are used to decide the best split at each node of the decision tree.
Looking at it step-by-step, this is what a random forest model does:
- Random subsets are created from the original dataset (bootstrapping).
- At each node in the decision tree, only a random set of features are considered to decide the best split.
- A decision tree model is fitted on each of the subsets.
- The final prediction is calculated by averaging the predictions from all decision trees.
> Note: The decision trees in random forest can be built on a subset of data and features. Particularly, the sklearn model of random forest uses all features for decision tree and a subset of features are randomly selected for splitting at each node.
##### Parameters

- n_estimators:
    - It defines the number of decision trees to be created in a random forest.
    - Generally, a higher number makes the predictions stronger and more stable, but a very large number can result in higher training time.
- criterion:
    - It defines the splitting criteria to be used.
    - The criteria maybe be gini impurity or entropy to measure the quality of a split.
- max_features :
    - It defines the maximum number of features allowed for the split in each decision tree.
    - Increasing max features usually improve performance but a very high number can decrease the diversity of each tree.
- max_depth:
    - Random forest has multiple decision trees. This parameter defines the maximum depth of the trees.
- min_samples_split:
    - Used to define the minimum number of samples required in a leaf node before a split is attempted.
    - If the number of samples is less than the required number, the node is not split.
- min_samples_leaf:
    - This defines the minimum number of samples required to be at a leaf node.
    - Smaller leaf size makes the model more prone to capturing noise in train data.
- max_leaf_nodes:
    - This parameter specifies the maximum number of leaf nodes for each tree.
    - The tree stops splitting when the number of leaf nodes becomes equal to the max leaf node.
- n_jobs:
    - This indicates the number of jobs to run in parallel.
    - Set value to -1 if you want it to run on all cores in the system.
- random_state:
    - This parameter is used to define the random selection.
    - It is used for comparison between various models.


### (2)Boosting:
Boosting is a sequential ensemble method. Here each base learner successively improves on previous learners by correcting the errors of the previous model. The succeeding models are dependent on the previous model. The general working of boosting algorithms can be summarised in the following steps: 
1. A subset is created from the original dataset.
2. Initially, all data points are given equal weights.
3. A base model is created on this subset.
4. This model is used to make predictions on the whole dataset.
5. Errors are calculated using the actual values and predicted values.
6. The observations which are incorrectly predicted, are given higher weights (higher attention to observations having prediction error).
7. Another model is created and predictions. Go back to step 5 and continue till desired accuracy is achieved or if model fails to show further improvement.

Thus we can see that multiple models are created, each correcting the errors of the previous model (weak learner). The final model (strong learner) is the weighted mean of all the models (weak learners). Thus, the boosting algorithm combines a number of weak learners to form a strong learner. The individual models would not perform well on the entire dataset, but they work well for some part of the dataset. Thus, each model actually boosts the performance of the ensemble.
![boosting](https://miro.medium.com/max/2936/1*jbncjeM4CfpobEnDO0ZTjw.png)
###### Algorithm: Adaboost, Stochastic Gradient Boosting, XGBoost
> Note: Weak machine learning models only ever give results that are marginally better than pure chance. Other models are much stronger learners, and with the correct training, data can become highly accurate.
#### Popular Boosting Algorithms:
> 2.1. AdaBoost
2.2. Gradient Boosting
2.3. XgBoost
#### 2.1.AdaBoost:
Adaptive boosting or AdaBoost is one of the simplest boosting algorithms. Usually, decision trees are used for modelling. Multiple sequential models are created, each correcting the errors from the last model. AdaBoost assigns weights to the observations which are incorrectly predicted and the subsequent model works to predict these values correctly.

Below are the steps for performing the AdaBoost algorithm:

- Initially, all observations in the dataset are given equal weights.
- A model is built on a subset of data.
- Using this model, predictions are made on the whole dataset.
- Errors are calculated by comparing the predictions and actual values.
- While creating the next model, higher weights are given to the data points which were predicted incorrectly.
- Weights can be determined using the error value. For instance, higher the error more is the weight assigned to the observation.
- This process is repeated until the error function does not change, or the maximum limit of the number of estimators is reached.
##### Parameters:
- base_estimators:
    - It helps to specify the type of base estimator(ML algorithm), that is, the machine learning algorithm to be used as base learner.
- n_estimators:
    - It defines the number of base estimators(Weak Learners).
    - The default value is 10, but we should keep a higher value to get better performance.
- learning_rate:
    - This parameter controls the contribution of the estimators(Weak Learners) in the final combination.
    - There is a trade-off between learning_rate and n_estimators.
- max_depth:
    - Defines the maximum depth of the individual estimator.
    - Tune this parameter for best performance.
- n_jobs
    - Specifies the number of processors it is allowed to use.
    - Set value to -1 for maximum processors allowed.
- random_state :
    - An integer value to specify the random data split.
    - A definite value of random_state will always produce same results if given with same parameters and training data.

We can also tune the parameters of base learners to optimize its performance.
#### 2.2Gradient Boosting:
Gradient Boosting is another ensemble machine learning algorithm that works for both regression and classification problems. It uses the boosting technique, combining a number of weak learners to form a strong learner. Regression trees used as a base learner, each subsequent tree in series is built on the errors calculated by the previous tree.

In Python Sklearn library, we use Gradient Boosting Regression Tree or GBRT. It is a generalization of boosting to arbitrary differentiable loss functions. It can be used for both regression and classification problems.

We will use a simple example to understand the Gradient boosting algorithm. We have to predict the age of a group of people using the below data:

![Gradient_image](https://user-images.githubusercontent.com/71091881/106216464-2c205700-61f9-11eb-9d7c-3b13bfb35506.png)

- (1)The mean age is assumed to be the predicted value for all observations in the dataset.
- (2)The errors are calculated using this mean prediction and actual values of age.

![Gradient_image_2](https://user-images.githubusercontent.com/71091881/106216496-44907180-61f9-11eb-8e7e-19ebfba8b291.png)

- (3)A tree model is created using the errors calculated above as target variable. Our objective is to find the best split to minimize the error.
- (4)The predictions by this model are combined with the predictions 1.

![Gradient_image_3](https://user-images.githubusercontent.com/71091881/106216538-5bcf5f00-61f9-11eb-9e01-f1e7bdda8cae.png)

- (5)This value calculated above is the new prediction.
- (6)New errors are calculated using this predicted value and actual value.

![Gradient_image_4](https://user-images.githubusercontent.com/71091881/106216550-6558c700-61f9-11eb-8392-35acf31338cb.png)

- (7)Steps 2 to 6 are repeated till the maximum number of iterations is reached (or error function does not change).
##### Parameters

- min_samples_split
    - Defines the minimum number of samples (or observations) which are required in a node to be considered for splitting.
    - Used to control over-fitting. Higher values prevent a model from learning relations which might be highly specific to the particular sample selected for a tree.
- min_samples_leaf
    - Defines the minimum samples required in a terminal or leaf node.
    - Generally, lower values should be chosen for imbalanced class problems because the regions in which the minority class will be in the majority will be very small.
- min_weight_fraction_leaf
    - Similar to min_samples_leaf but defined as a fraction of the total number of observations instead of an integer.
- max_depth
    - The maximum depth of a tree.
    - Used to control over-fitting as higher depth will allow the model to learn relations very specific to a particular sample.
- max_leaf_nodes
    - The maximum number of terminal nodes or leaves in a tree.
    - Can be defined in place of max_depth. Since binary trees are created, a depth of ‘n’ would produce a maximum of 2^n leaves.
    - If this is defined, the gradient model will ignore max_depth.
- max_features
    - The number of features to consider while searching for the best split. These will be randomly selected.
    - As a thumb-rule, the square root of the total number of features works great but we should check up to 30-40% of the total number of features.
    - Higher values can lead to over-fitting but it generally depends on a case to case scenario.
#### 2.3.XGBoost:
XGBoost (extreme Gradient Boosting) is an advanced implementation of the gradient boosting algorithm. XGBoost has proved to be a highly effective ML algorithm. XGBoost has high predictive power and is almost 10 times faster than the other gradient boosting techniques. It also includes a variety of regularization which reduces over fitting and improves overall performance. Hence it is also known as ‘regularized boosting‘ technique.

Let us see how XGBoost is comparatively better than other techniques:

- (1) Regularization:
    - Standard GBM implementation has no regularisation like XGBoost.
    - Thus XGBoost also helps to reduce over fitting.
- (2) Parallel Processing:
    - XGBoost implements parallel processing and is faster than GBM .
    - XGBoost also supports implementation on Hadoop.
- (3) High Flexibility:
    - XGBoost allows users to define custom optimization objectives and evaluation criteria adding a whole new dimension to the model.
- (4) Handling Missing Values:
    - XGBoost has an in-built routine to handle missing values.
- (5) Tree Pruning:
    - XGBoost makes splits up to the max_depth specified and then starts pruning the tree backwards and removes splits beyond which there is no positive gain.
- (6) Built-in Cross-Validation:
    - XGBoost allows a user to run a cross-validation at each iteration of the boosting process and thus it is easy to get the exact optimum number of boosting iterations in a single run.
##### Parameters

- nthread
    - This is used for parallel processing and the number of cores in the system should be entered..
    - If you wish to run on all cores, do not input this value. The algorithm will detect it automatically.
- eta
    - Analogous to learning rate in Gradient Boosting algorithm.
    - Makes the model more robust by shrinking the weights on each step.
- min_child_weight
    - Defines the minimum sum of weights of all observations required in a child.
    - Used to control over-fitting. Higher values prevent a model from learning relations which might be highly specific to the particular sample selected for a tree.
- max_depth
    - It is used to define the maximum depth.
    - Higher depth will allow the model to learn relations very specific to a particular sample.
- max_leaf_nodes
    - The maximum number of terminal nodes or leaves in a tree.
    - Can be defined in place of max_depth. Since binary trees are created, a depth of ‘n’ would produce a maximum of 2^n leaves.
    - If this is defined, GBM will ignore max_depth.
- gamma
    - A node is split only when the resulting split gives a positive reduction in the loss function. Gamma specifies the minimum loss reduction required to make a split.
    - Makes the algorithm conservative. The values can vary depending on the loss function and should be tuned.
- subsample
    - Same as the sub sample of GBM. Denotes the fraction of observations to be randomly sampled for each tree.
    - Lower values make the algorithm more conservative and prevent over fitting but values that are too small might lead to under-fitting.
- colsample_bytree
    - It is similar to max_features in GBM.
    - Denotes the fraction of columns to be randomly sampled for each tree.

### (3)Stacking:
Stacking is a way of combining multiple models, that introduces the concept of a meta learner. It is less widely used than bagging and boosting. Unlike bagging and boosting, stacking may be (and normally is) used to combine models of different types. The procedure is as follows:
- (1)The training set is split into n parts.
- (2)A base model(model-1) is fitted on (n-1) parts and predictions are made for the nth part of the training set. This is done for each part of the training set.
- (3)The base model is then fitted on the whole training dataset.
- (4)Using this model, predictions are made on the test set.
- (5)Steps 2 to 4 are repeated for another base model(model-2) resulting in another set of predictions for the training set and test set.
- (6)The predictions from the training set are used as features to build a new model.
- (7)This model is used to make final predictions on the test prediction set.
- ###### Algorithm: Voting Classifier
![Stacking](https://media.geeksforgeeks.org/wp-content/uploads/20190515104518/stacking.png)
