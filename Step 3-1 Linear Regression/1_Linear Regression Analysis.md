# Linear Regression Analysis
***

## [Introduction to Regression Analysis](HousePricePrediction1.ipynb)

Regression analysis is a **statistical technique** for investigating and **modeling the relationship between variables**. Relation between variables where changes in some variables may “explain” or possibly “cause” changes in other variables. Explanatory variables are termed the **independent variables** and the variables to be explained are termed the **dependent** variables.

Regression model estimates the nature of the relationship between the **independent** and **dependent** variables.

- Change in dependent variables that results from changes in independent variables, i.e. size of the relationship.
- Strength of the relationship.
- Statistical significance of the relationship.


### Examples

- Dependent variable is employment income while independent variables might be hours of work, education, occupation, sex, age, region, years of experience, unionization status, etc.

- Price of a product and quantity produced or sold:
  
    - If Price affected by quantity offered for sale. Dependent variable is price while independent variable is quantity sold.


# Linear Regression 

Linear regression shows the **linear relationship** between the  **independent variable (X-axis)** and the  **dependent variable (Y-axis)**, hence called **linear regression**.

Mathematical equation for Linear regression:

 $$y = a_0 + a_1*x_1 + a_2*x_2 + a_3*x_3 +.........+ a_n*x_n$$
 
**where**, 
- $a_0, a_1, a_2,......., a_n$ are linear coefficients.
- $x_1, x_2, x_3,......., x_n$ are independent variables (predictor variables).
- y is dependent variable (target variable).

The knowledge of the model depends on the knowledge of the parameters $a_0, a_1, a_2,......., a_n$.

<br>

The relationship between variables in the linear regression model can be explained using the below image. 

<img src="https://i.imgur.com/mZfNu9S.png" width="450" height="300"> <br>  

Here we are predicting the salary of an employee on the basis of the year of experience.

<br>

#### Types of Relationships

<img src="https://i.imgur.com/I4fQLbo.png" width="850" height="400"> <br> 



***

### Types of Linear Regression
Linear regression can be further divided into two types of the algorithm:

- **Simple Linear Regression:**<br>
If a single independent variable is used to predict the value of a numerical dependent variable, then such a Linear Regression algorithm is called Simple Linear Regression.

- **Multiple Linear regression:**<br>
If more than one independent variable is used to predict the value of a numerical dependent variable, then such a Linear Regression algorithm is called Multiple Linear Regression.
<br>

### Linear Regression Line

A linear line showing the relationship between the dependent and independent variables is called a **regression line**. A regression line can show two types of relationship:

- **Positive Linear Relationship:** <br>
If the dependent variable increases on the Y-axis and independent variable increases on X-axis, then such a relationship is termed as a Positive linear relationship.
<img src="https://i.imgur.com/9JTmoPc.png"  >

- **Negative Linear Relationship:** <br>
If the dependent variable decreases on the Y-axis and independent variable increases on the X-axis, then such a relationship is called a negative linear relationship.
<img src="https://i.imgur.com/uiD4O0D.png"  >

***


## Simple Linear Regression 

- Only one independent variable, X.
- Relationship between X and Y is described by a linear function.
- Changes in Y are assumed to be caused by changes in X.
- Dependent variable must be a continuous/real value.
<br>

### Simple Linear Regression Model 

The Simple Linear Regression model can be represented using the below equation:

<img src="https://i.imgur.com/sqJUIU9.png" width="550" > 


The Geometrical Visualization of the parameters are given as below:

<img src="https://i.imgur.com/oLqqW9B.png" width="550" > 

To create a model, we must "learn" the values of these coeffients. And once we have the value of these coefficients, we can use the model to predict.
<br>

### Simple Linear Regression Equation (Prediction Line)


<img src="https://i.imgur.com/gCs7Z4K.png" width="550" > 
						
<br>

### Best fit line:

The **best fit line** has to be calculated that minimizes the sum of squared residuals (or "sum of squared errors").
					
<img src="https://i.imgur.com/ZfSjiAS.png" width="500" > 
<img src="https://i.imgur.com/hNTy5ab.png" width="500" > 

<br>

### Visualizing regression line fitting

Suppose Linear Regression Model is:
$$ y = m*x+c$$ <br>
Then the values of m and c are updated at each iteration to get the optimal solution.

<img src="https://miro.medium.com/max/576/1*CjTBNFUEI_IokEOXJ00zKw.gif" width="500" >		

<br>
    
### The Gradient Descent Algorithm

Gradient descent is an iterative optimization algorithm to find the minimum of a function. Here that function is our Loss Function.

<br>

#### Understanding Gradient Descent
<br>
<img src="https://i.imgur.com/flKZ3p3.png" width="400" class="center"> 
<br>

### Estimating ("Learning") Model Coefficients

					
<img src="https://i.imgur.com/I34k2Oc.png" width="1050" height="850" class="center"> <br>
***

<br><br>


# MULTIPLE LINEAR REGRESSION


A regression model that involves more than one independent variable is called a **multiple regression model**.<br>

<b>Example:</b>
	
- Predict <b>co2emission</b> vs <b>EngineSize</b> and <b>Cylinders</b> of all cars.
    - independent variable (x): EngineSize, Cylinders, etc.
    - Dependent variable (y): co2emission.
    
## Simple vs Multiple Linear Regression<br>

<img src="https://i.imgur.com/syMhoRT.png" width="450" class="left"> <br>

The simple linear regression model can be represented graphically as a best-fit line between the data points, while the multiple linear regression model can be represented as a plane (in 2-dimensions) or a hyperplane (in higher dimensions).

<br>

<img src="https://i.imgur.com/kMmvOhW.png" width="500" class="left"> <br>

# Assumptions of Regression

- The regression model is linear in terms of coefficients and error term.
- The mean of the residuals is zero.
- The error terms are not correlated with each other, i.e. given an error value; we cannot predict the next error value.
- The independent variables(x) are uncorrelated with the residual term, also termed as **exogeneity**. This, in layman term, generalises that in no way should the error term be predicted given the value of independent variables.
- The error terms have a constant variance, i.e. **homoscedasticity**.
- **No Multicollinearity,** i.e. no independent variables should be correlated with each other or affect one another. If there is multicollinearity, the precision of prediction by the model decreases.
- The error terms are normally distributed.

***

# Overfitting and Underfitting in Machine Learning
Overfitting and Underfitting are the two main problems that occur in machine learning and degrade the performance of the machine learning models.

The main goal of each machine learning model is to **generalize well**. Here **generalization** defines the ability of an ML model to provide a suitable output by adapting the given set of unknown input. It means after providing training on the dataset, it can produce reliable and accurate output. Hence, the underfitting and overfitting are the two terms that need to be checked for the performance of the model and whether the model is generalizing well or not.

Before understanding the overfitting and underfitting, let's understand some basic term that will help to understand this topic well:

- **Bias:** Bias is a prediction error that is introduced in the model due to simplifying assumptions made when using machine learning algorithms. It refers to the amount of error in prediction. It practice this occurs when the variables are to few or the number of observations are to few. It can also happen if a simple model is used to fit a complex pattern. The performance of the model will be poor across training and test sets.

- **Variance:** If the machine learning model performs very well with the training set but does not perform as well on external test sets, the model has learnt patterns unique to the training set and doesn't generalise well. This the problem of variance in machine learning. This often happens because the model is to complex. In this case complexity of the model has to be reduced so it generalises well and performs better on test sets as well.

## Underfitting
Underfitting occurs when our machine learning model is not able to capture the underlying pattern present in the data.

In the case of underfitting, the model is not able to learn enough from the training data, and hence the parameters estimates have low accuracy and produces unreliable predictions.

An underfitted model has high bias and low variance.

**Example:** We can understand the underfitting using below output of the linear regression model:

<img src="https://i.imgur.com/ApdxV24.png" width="400" height="300" class="center">


## Overfitting
Overfitting occurs when our machine learning model tries to cover all the data points or more than the required data points present in the given dataset. Because of this, the model starts caching noise and inaccurate values present in the dataset, and all these factors reduce the efficiency and accuracy of the model. The overfitted model has **low bias** and **high variance**.

**Example:** The concept of the overfitting can be understood by the below graph of the linear regression output:

<img src="https://i.imgur.com/R0eXt4m.png" width="400" height="300" class="center">

## How to avoid the Overfitting in Model
Both overfitting and underfitting cause the degraded performance of the machine learning model. But the main cause is overfitting, so there are some ways by which we can reduce the occurrence of overfitting in our model.

- Cross-Validation
- Training with more data
- Removing features
- Regularization
- Ensembling.


# Bias Variance Tradeoff

If the algorithm is too simple, it will have high bias and low variance and thus will perform poorly across datasets. If algorithm's fit is too complex then it may have high variance and not perform well with unseen data. Bias and variance are always inverse to one another. High bias implies low variance and vice versa. Both are not good for model performance. A good model fits the data well and is also generalisable to unseen data. The final purpose of a model is to be used for real world predictions. Bias and variance are always in a tug of war. The ideal model would have low bias and low variance. But this is often hard to achieve. This problem is know as te bias variance trade-off. It is called a trade-off beacause increasing one reduces the other. achieving the right balance is often difficult in practice.

The error to complexity graph to show trade-off is given as –
<br>

<img src="https://i.imgur.com/hCXlADt.png" width="700" height="400" class="center">

This is referred to as the best point chosen for the training of the algorithm which gives low error in training as well as testing data.
***
# Regularization 
When we use regression models to train some data, there is a good chance that the model will overfit the given training data set. Regularization is a technique used to reduce the complexity of the model by shrinking the weightage of features to avoid overfitting.

To regularize the model, a Shrinkage penalty is added to the cost function.

Let’s see different types of regularizations in regression:<br>
There are two main regularization techniques, namely Ridge Regression and Lasso Regression. They both differ in the way they assign a penalty to the coefficients.

### LASSO (L1 Regularization)
LASSO regression penalizes the model based on the sum of magnitude of the coefficients. The regularization term is given by

<img src="https://i.imgur.com/48EKUba.png" class="center">

Where, λ is the shrinkage factor.

and hence the formula for loss after regularization is: 

<img src="https://i.imgur.com/Zo1jJhh.png"  class="center"> <br>

### Ridge Regression (L2 Regularization)
Ridge regression penalizes the model based on the sum of squares of magnitude of the coefficients. The regularization term is given by

<img src="https://i.imgur.com/kBThYn4.png" class="center">

Where, λ is the shrinkage factor.

and hence the formula for loss after regularization is:

<img src="https://i.imgur.com/3LSzqoj.png"  class="center"> <br>

<img src="https://i.imgur.com/1SU0fUo.png" width="850" height="170" class="center">

<img src="https://i.imgur.com/AJJTFpH.png" width="450" height="400" class="center">

The red ellipse represents the cost function of the model, whereas the square (left side) represents the Lasso regression and the circle (right side) represents the Ridge regression.

### Summary of Ridge and Lasso regularisation
- Ridge regression shrinks the coefficients for those predictors which contribute very less in the model but have huge weights, very close to zero. But it never makes them exactly zero.
- There are greater range of λ values to choose from in case of ridge regression as all the variables are still retained in the model. Thus, the final model will still contain all those predictors, though with less weights. 
- This doesn’t help in interpreting the model very well. This is where Lasso regression differs with Ridge regression. 
- In Lasso, the L1 penalty does reduce some coefficients exactly to zero when we use a sufficiently large tuning parameter λ.
- The tuning parameter for lasso regression is typically kept between (0,1). 
- Lasso regression drops features if the λ value is too high. So, in addition to regularizing, lasso also performs feature selection.
