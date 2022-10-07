<br>
<img src="https://i.imgur.com/sELrCVY.png" width="500" height="300"> <br>
<br>

# K-Nearest Neighbour (KNN) Algorithm

K-Nearest Neighbour is one of the simplest Machine Learning algorithms based on Supervised Learning technique.It stores all the available data and classifies a new data point based on the similarity. This means when new data appears then it can be easily classified into a well suite category by using K-NN algorithm. It can be used for Regression as well as for Classification but mostly it is used for the Classification problems.


<img src="https://i.imgur.com/tyDhcjc.png" width="550" height="450">

## How does K-NN work?

The K-NN working can be explained on the basis of the below algorithm:

- Step-1: Select the number K of the neighbors
- Step-2: Calculate the Euclidean distance of K number of neighbors
- Step-3: Take the K nearest neighbors as per the calculated Euclidean distance or Manhattan distance.
- Step-4: Among these k neighbors, count the number of the data points in each category.
- Step-5: Assign the new data points to that category for which the number of the neighbor is maximum.
- Step-6: Our model is ready.

<img src="https://i.imgur.com/OgvPvxI.png" width="950" height="700">

<img src="https://i.imgur.com/BEDq7oj.png" width="850" height="500">

### Advantages of KNN Algorithm:
- It is simple to implement.
- It is robust to the noisy training data
- It can be more effective if the training data is large.
- There are only two parameters required to implement KNN i.e. the value of K and the distance function (e.g. Euclidean or Manhattan etc.)
- It is lazy learning algorithm and therefore requires no training prior to making real time predictions. This makes the KNN algorithm much faster than other algorithms that require training e.g SVM, linear regression, etc.


### Disadvantages of KNN Algorithm:
- Always needs to determine the value of K which may be complex some time.
- The computation cost is high because of calculating the distance between the data points for all the training samples.
- The KNN algorithm doesn't work well with categorical features since it is difficult to find the distance between dimensions with categorical features.

***
## Resources
- Video: [K-Nearest Neighbour Algorithm](https://www.youtube.com/watch?v=HVXime0nQeI&list=PLblh5JKOoLUICTaGLRoHQDuF_7q2GfuJF&index=35) (5 minutes)
