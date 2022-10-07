<br>
<img src="https://i.imgur.com/OlUcdKm.png" width="550" height="250"> <br>

<br>

## Naïve Bayes Classifier Algorithm

- Naïve Bayes algorithm is a supervised learning algorithm, which is based on <b>Bayes theorem</b> and used for solving classification problems.
- It is mainly used in text classification that includes a high-dimensional training dataset.
- Naïve Bayes Classifier is one of the simple and most effective Classification algorithms which helps in building the fast machine learning models that can make quick predictions.
- <b> It is a probabilistic classifier, which means it predicts on the basis of the probability of an object.</b>
- Some popular examples of Naïve Bayes Algorithm are <b>spam filtration, Sentimental analysis, and classifying articles.</b>

## Why is it called Naïve Bayes?
The Naïve Bayes algorithm is comprised of two words Naïve and Bayes, Which can be described as:

- <b>Naïve:</b> It is called Naïve because it assumes that the occurrence of a certain feature is independent of the occurrence of other features. Such as if the fruit is identified on the bases of color, shape, and taste, then red, spherical, and sweet fruit is recognized as an apple. Hence each feature individually contributes to identify that it is an apple without depending on each other.


- <b>Bayes:</b>. It is called Bayes because it depends on the principle of Bayes' Theorem.

## Bayes' Theorem:
Bayes' theorem is also known as <b>Bayes' Rule</b> or <b>Bayes' law</b>, which is used to determine the probability of a hypothesis with prior knowledge. It depends on the conditional probability.

The formula for Bayes' theorem is given as:

<img src="https://i.imgur.com/MAc0hIG.png" width="500" height="300">

#### Where,

- P(c|x) is the posterior probability of class (c, target) given predictor (x, attributes).
- P(c) is the prior probability of class.
- P(x|c) is the likelihood which is the probability of predictor given class.
- P(x) is the prior probability of predictor.

### How Naive Bayes algorithm works?
Let’s understand it using an example. Below I have a training data set of weather and corresponding target variable **‘Play’** (suggesting possibilities of playing). Now, we need to classify whether players will play or not based on weather condition. 
<br>

**Let’s follow the below steps to perform it.**



**Step 1:** Convert the data set into a frequency table

**Step 2:** Create Likelihood table by finding the probabilities like Overcast probability = 0.29 and probability of playing is 0.64.

<img src="https://i.imgur.com/pgtc1WT.png" >

**Step 3:** Now, use Naive Bayesian equation to calculate the posterior probability for each class. The class with the highest posterior probability is the outcome of prediction.

**Problem:** If the weather is sunny, then the Player should play or not?

We can solve it using above discussed method of posterior probability.

**P(No | Sunny) = P(Sunny | No) * P(No) /P(Sunny)**

Here we have <BR>
P(Sunny | NO) = 2/5 = 0.4<br>
P(No) = 0.36 <br>
P(Sunny) = 0.36 <br>
So, **P(No | Sunny)** = 0.4 * 0.36 / 0.36 = 0.40

**P(Yes | Sunny) = P( Sunny | Yes) * P(Yes) / P(Sunny)**

Here we have <BR>
P(Sunny | Yes) = 3/9 = 0.33,<br> P(Sunny) = 5/14 = 0.36,<br> P( Yes)= 9/14 = 0.64<br>
So, **P(Yes | Sunny)** = 0.33 * 0.64 / 0.36 = 0.60

So as we can see from the above calculation that **P(Yes | Sunny)  > P(No | Sunny)**

**Hence on a Sunny day, Player can play the game.**

Naive Bayes uses a similar method to predict the probability of different class based on various attributes. This algorithm is mostly used in text classification and with problems having multiple classes.

## Advantages of Naïve Bayes Classifier:
- Naïve Bayes is one of the fast and easy ML algorithms to predict a class of datasets.
- It can be used for Binary as well as Multi-class Classifications.
- It performs well in Multi-class predictions as compared to the other Algorithms.
- It is the most popular choice for text classification problems.


## Disadvantages of Naïve Bayes Classifier:
- Naive Bayes assumes that all features are independent or unrelated, so it cannot learn the relationship between features.

## Applications of Naïve Bayes Classifier:
- It is used for Credit Scoring.
- It is used in medical data classification.
- It can be used in real-time predictions because Naïve Bayes Classifier is an eager learner.
- It is used in Text classification such as Spam filtering and Sentiment analysis.


## Types of Naïve Bayes Model:
There are three types of Naive Bayes Model, which are given below:

- <b>Gaussian:</b> The Gaussian model assumes that features follow a normal distribution. This means if predictors take continuous values instead of discrete, then the model assumes that these values are sampled from the Gaussian distribution.


- <b>Multinomial:</b> The Multinomial Naïve Bayes classifier is used when the data is multinomial distributed. It is primarily used for document classification problems, it means a particular document belongs to which category such as Sports, Politics, education, etc.
The classifier uses the frequency of words for the predictors.



- <b>Bernoulli:</b> The Bernoulli classifier works similar to the Multinomial classifier, but the predictor variables are the independent Booleans variables. Such as if a particular word is present or not in a document. This model is also famous for document classification tasks.

<br>

***
## Resources

- [10 minutes to Gaussian Naive Bayes](https://www.youtube.com/watch?v=H3EjCKtlVog&list=PLblh5JKOoLUICTaGLRoHQDuF_7q2GfuJF&index=37) 
- [Scikit-learn Documentation](https://scikit-learn.org/stable/modules/naive_bayes.html)
