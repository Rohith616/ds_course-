# Mathematical Derivation of the Logistic regressive Model 

Logistic regression can be binary (binomial), multinomial or ordinal.

Binomial logistic regression involves an outcome with only two possible categories.

- Binomial logistic regression involves an outcome with only two possible categories.
- Multinomial logistic regression is a natural extension of the binomial logistic regression and involves an outcome with three or more possible categories.
- Ordinal is just multinomial logistic regression whereby the categories are ordered.<br>
With that said a full discussion of logistic regression cannot fit in a single Quora answer. Thus I will only focus on the simplified version of binomial logistic regression and naturally extend it to multinomial logistic regression.

We will only focus on the simplified version of binomial logistic regression and naturally extend it to multinomial logistic regression.

![img](https://user-images.githubusercontent.com/67789350/89313780-931fe180-d696-11ea-8d6e-659f54294a1e.png)

---

# Getting Started !

The outcome in binomial logistic regression can be a 0 or a 1. The idea is then to estimate the probability of an outcome being a 1 or a 0. Given that the probability of the outcome being a 1 is given by p then the probability of it not occurring is given by 1-p. This can be seen as a special case of Binomial distribution called the Bernoulli distribution.

The idea in logistic regression is to cast the problem in form of generalized linear regression model !

## 𝑦̂ =𝛽0+𝛽1𝑥1+…+𝛽𝑛𝑥𝑛

where <span style="font-size:larger;">𝑦̂</span>=predicted value,  <span style="font-size:larger;"> 𝑥</span> = independent variables and the <span style="font-size:larger;">𝛽</span>  are coefficients to be learnt.

This can be compactly expressed in vector form:

## 𝑤𝑇 = [𝛽0,𝛽1,…,𝛽𝑛] 

## 𝑥𝑇 = [1,𝑥1,…,𝑥𝑛]

Then

## 𝑦̂ = 𝑤ᵀ𝑥

But this is linear regression stuff so we need to find a way to cast the logistic regression problem in a manner whereby at least the expression above can be used. Thus if we compute the odds of the outcome as:

## 𝑜𝑑𝑑𝑠(𝑝)= p/1-p

This now varies continuously linear and thus we can do the following:

## 𝑙𝑜𝑔𝑖𝑡(𝑝)= 𝑦̂ =𝑤ᵀ𝑥

Thus the logit function acts like a link between logistic regression and linear regression and thus it is called a link function.

After we estimate the weights  𝑤  we can take the inverse of logit to get the probability p as given below:

## 𝑙𝑜𝑔𝑖𝑡(𝑝)=𝑙𝑜𝑔(𝑝/1−𝑝)

Taking the natural exponential on both sides gives:

## 𝑒ˡᵒᵍᶦᵗ⁽ᵖ⁾=𝑝/1−𝑝

Then adding 1 on both sides gives:

## 𝑒^𝑦̂+1=((𝑝/1−𝑝) + 1)

## 𝑒^𝑦̂ +1= 1/1−𝑝

Changing subject of formula to 1-p gives:

## 1−𝑝 = 1 / 𝑒^𝑦̂ + 1

Then subtracting 1 from both sides to give:

## −𝑝 = ((1/𝑒^𝑦̂ +1) − 1)

Multiply by -1 on both sides to get:

## 𝑝 = (1 − (1 / 𝑒𝑦̂ +1))

## 𝑝 = 𝑒^𝑦̂ / 𝑒^𝑦̂ + 1

Then divide the numerator and denominator by  𝑒^𝑦̂   to get:

## 𝑝 = 1 / 1+𝑒^−𝑦̂ 

Looks familiar?

_Of course it is a logistic (sigmoid) function._

From this point we can cast logistic regression in form of a single layered neural network (NN) with a sigmoid activation function. Which means we can estimate the weight parameters using the usual stochastic gradient descent (SGD) by minimizing the cross-entropy loss function given by:

## 𝑙(𝑝,𝑦)=−𝑦𝑙𝑜𝑔(𝑝)−(1−𝑦)𝑙𝑜𝑔(1−𝑝)

Where  <br>
## 𝑦∈[0,1]

The multinomial logistic regression can then be just about adding more sigmoid neurons in the layer. And instead of using the logistic function we can use the softmax as the activation function to keep the output as a probability distribution. The loss in the multinomial logistic regression case with a softmax becomes the log likelihood loss.

---

Thus for simplicity you need to look at logistic regression from the modern formulation of standard ML techniques such as regularization and loss function optimization using gradient decent optimization methods.

Once you derive the logistic function as above, it becomes necessary to treat the rest of the logistic regression problem as just a single layered NN with sigmoid activation functions. That way we can solve the whole logistic regression problem by standard gradient descent algorithms.

## Few reference reads : 

- [Generalized linear model](https://en.m.wikipedia.org/wiki/Generalized_linear_model?wprov=sfla1)
- [Automatic differentiation](https://en.m.wikipedia.org/wiki/Automatic_differentiation?wprov=sfla1)
- [Numerical differentiation](https://en.m.wikipedia.org/wiki/Numerical_differentiation?wprov=sfla1)



 

