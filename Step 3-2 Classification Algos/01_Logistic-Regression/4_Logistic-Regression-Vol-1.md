# Logistic Regression 

Logistic Regression is one of the most used Machine Learning algorithms for binary classification. 

It is a simple Algorithm that you can use as a performance baseline, it is easy to implement and it will do well enough in many tasks. 

Therefore every Machine Learning engineer should be familiar with its concepts. The building block concepts of Logistic Regression can also be helpful in deep learning while building neural networks. In this post, you will learn what Logistic Regression is, how it works, what are advantages and disadvantages and much more.

![img](https://user-images.githubusercontent.com/67789350/88439679-7cbd8e80-ce29-11ea-9fbe-128e7e3550aa.png)

# Linear Regression VS Logistic Regression?

Logistic regression is an alternative method to use other than the simpler Linear Regression. 

Linear regression tries to predict the data by finding a linear – straight line – equation to model or predict future data points. 

Logistic regression does not look at the *relationship between the two variables as a straight line*. Instead, Logistic regression uses the natural logarithm function to find the relationship between the variables and uses test data to find the coefficients. 

The function can then predict the future results using these coefficients in the logistic equation !

![img](https://user-images.githubusercontent.com/67789350/88441509-f310bf80-ce2e-11ea-98da-12526fcc3803.png)

<br>

***

<br>

# What is the Sigmoid Function?

It is a mathematical function having a characteristic that can take any real value and map it to between 0 to 1 shaped like the letter “S”. The sigmoid function also called a logistic function.

Y = 1 / 1+e⁻ᶻ

![img](https://user-images.githubusercontent.com/67789350/89324007-35929180-d6a4-11ea-9b46-50b1a28416eb.png) <br>
So, if the value of z goes to positive infinity then the predicted value of y will become 1 and if it goes to negative infinity then the predicted value of y will become 0. And if the outcome of the sigmoid function is more than 0.5 then we classify that label as class 1 or positive class and if it is less than 0.5 than we can classify it to negative class or label as class 0.

For a more in-dept mathematical derivation of the logistic regression model ,you can check out our derivation from [here !](https://github.com/Tech-i-s/data-science-course-wiki/blob/development/machine-learning/logistic-regression/logistic-regression-derivation.md)

# How to use Logistic Regression in Machine Learning?

This is the logistic function: <br>
![img](https://user-images.githubusercontent.com/67789350/88441592-25222180-ce2f-11ea-9269-71dc605c02bf.png)

This is the equation for Logistic Regression equation:<br>
![img](https://user-images.githubusercontent.com/67789350/88441614-38cd8800-ce2f-11ea-8b06-853ec1631808.png)

Where y is the predicted output, B0 is the intercept, and B1 is the coefficient for a single value of X !

For better clarity, you can imagine that the points in logistic regression can be clearly defined into one or more graphical areas : <br>
![img](https://user-images.githubusercontent.com/67789350/88441671-76321580-ce2f-11ea-9d0b-e4a4a074cf55.png)
