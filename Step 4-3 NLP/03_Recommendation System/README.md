# Recommendation System

## Introduction

In today’s world, every customer is faced with multiple choices. **For example,** If I’m looking for a book to read without any specific idea of what I want, there’s a wide range of possibilities how my search might pan out. I might waste a lot of time browsing around on the internet and trawling through various sites hoping to strike gold. I might look for recommendations from other people.

But if there was a site or app which could recommend me books based on what I have read previously, that would be a massive help. Instead of wasting time on various sites, I could just log in and voila! 10 recommended books tailored to my taste.

This is what recommendation engines do and their power is being harnessed by most businesses these days. From Amazon to Netflix, Google to Goodreads, recommendation engines are one of the most widely used applications of machine learning techniques.



## What are recommendation engines?

Till recently, people generally tended to buy products recommended to them by their friends or the people they trust. This used to be the primary method of purchase when there was any doubt about the product. But with the advent of the digital age, that circle has expanded to include online sites that utilize some sort of recommendation engine.

**A recommendation engine filters the data using different algorithms and recommends the most relevant items to users. It first captures the past behavior of a customer and based on that, recommends products which the users might be likely to buy.**

If a completely new user visits an e-commerce site, that site will not have any past history of that user. So how does the site go about recommending products to the user in such a scenario? One possible solution could be to recommend the best selling products, i.e. the products which are high in demand. Another possible solution could be to recommend the products which would bring the maximum profit to the business.

If we can recommend a few items to a customer based on their needs and interests, it will create a positive impact on the user experience and lead to frequent visits. Hence, businesses nowadays are building smart and intelligent recommendation engines by studying the past behavior of their users.

Now that we have an intuition of recommendation engines, let’s now look at how they work.


## How does a recommendation engine work?

Before we deep dive into this topic, first we’ll think of how we can recommend items to users:

- We can recommend items to a user which are most popular among all the users
- We can divide the users into multiple segments based on their preferences (user features) and recommend items to them based on the segment they belong to

Both of the above methods have their drawbacks. In the first case, the most popular items would be the same for each user so everybody will see the same recommendations. While in the second case, as the number of users increases, the number of features will also increase. So classifying the users into various segments will be a very difficult task.

The main problem here is that we are unable to tailor recommendations based on the specific interest of the users. It’s like Amazon is recommending you buy a laptop just because it’s been bought by the majority of the shoppers. But thankfully, Amazon (or any other big firm) does not recommend products using the above mentioned approach. They use some personalized methods which help them in recommending products more accurately.

Let’s now focus on how a recommendation engine works by going through the following steps.


###  Data collection
This is the first and most crucial step for building a recommendation engine. The data can be collected by two means: explicitly and implicitly. Explicit data is information that is provided intentionally, i.e. input from the users such as movie ratings. Implicit data is information that is not provided intentionally but gathered from available data streams like search history, clicks, order history, etc.

![img](https://i.imgur.com/4uCzvtp.png)

In the above image, Netflix is collecting the data explicitly in the form of ratings given by user to different movies.

![img](https://i.imgur.com/RbnghIJ.png)

Here the order history of a user is recorded by Amazon which is an example of implicit mode of data collection.


###  Data storage

The amount of data dictates how good the recommendations of the model can get. For example, in a movie recommendation system, the more ratings users give to movies, the better the recommendations get for other users. The type of data plays an important role in deciding the type of storage that has to be used. This type of storage could include a standard SQL database, a NoSQL database or some kind of object storage.

 

###  Filtering the data

After collecting and storing the data, we have to filter it so as to extract the relevant information required to make the final recommendations.

![img](https://i.imgur.com/FiowNEA.png)

There are various algorithms that help us make the filtering process easier. In the next section, we will go through each algorithm in detail.

### Content based filtering
This algorithm recommends products which are similar to the ones that a user has liked in the past.

![img](https://i.imgur.com/8mDqrPM.png)

**For example,** if a person has liked the movie “Inception”, then this algorithm will recommend movies that fall under the same genre. But how does the algorithm understand which genre to pick and recommend movies from?

**Consider the example of Netflix.** They save all the information related to each user in a vector form. This vector contains the past behavior of the user, i.e. the movies liked/disliked by the user and the ratings given by them. This vector is known as the **profile vector**. All the information related to movies is stored in another vector called the **item vector**. Item vector contains the details of each movie, like genre, cast, director, etc.

The content-based filtering algorithm finds the cosine of the angle between the profile vector and item vector, i.e. **cosine similarity**. Suppose A is the profile vector and B is the item vector, then the similarity between them can be calculated as:

![img](https://i.imgur.com/SnoSJFz.png)

Based on the cosine value, which ranges between -1 to 1, the movies are arranged in descending order and one of the two below approaches is used for recommendations:

- **Top-n approach:** where the top n movies are recommended (Here n can be decided by the business)
- **Rating scale approach:** Where a threshold is set and all the movies above that threshold are recommended<br>

Other methods that can be used to calculate the similarity are:

- **Euclidean Distance:** Similar items will lie in close proximity to each other if plotted in n-dimensional space. So, we can calculate the distance between items and based on that distance, recommend items to the user. The formula for the euclidean distance is given by:

![img](https://i.imgur.com/LvUmcDu.png)

- **Pearson’s Correlation:** It tells us how much two items are correlated. Higher the correlation, more will be the similarity. Pearson’s correlation can be calculated using the following formula:

![img](https://i.imgur.com/Ar9t6s4.png)

A major drawback of this algorithm is that it is limited to recommending items that are of the same type. It will never recommend products which the user has not bought or liked in the past. So if a user has watched or liked only action movies in the past, the system will recommend only action movies. It’s a very narrow way of building an engine.

To improve on this type of system, we need an algorithm that can recommend items not just based on the content, but the behavior of users as well.

### Collaborative filtering

Let us understand this with an example. If person A likes 3 movies, say Interstellar, Inception and Predestination, and person B likes Inception, Predestination and The Prestige, then they have almost similar interests. We can say with some certainty that A should like The Prestige and B should like Interstellar. The collaborative filtering algorithm uses “User Behavior” for recommending items. This is one of the most commonly used algorithms in the industry as it is not dependent on any additional information. There are different types of collaborating filtering techniques and we shall look at them in detail below.

![img](https://i.imgur.com/irW1zTF.png)

**User-User collaborative filtering**

This algorithm first finds the similarity score between users. Based on this similarity score, it then picks out the most similar users and recommends products which these similar users have liked or bought previously.

![img](https://i.imgur.com/eekPGMp.png)

<br>

In terms of movies example, this algorithm finds the similarity between each user based on the ratings they have previously given to different movies. The prediction of an item for a user u is calculated by computing the weighted sum of the user ratings given by other users to an item i.

<img src="https://i.imgur.com/7yMWr4n.png" width="800" class = "left" > <br>

Now, we have the ratings for users in profile vector and based on that we have to predict the ratings for other users. Following steps are followed to do so:

1. For predictions we need the similarity between the user u and v. We can make use of Pearson correlation.
2. First we find the items rated by both the users and based on the ratings, correlation between the users is calculated.
3. The predictions can be calculated using the similarity values. This algorithm, first of all calculates the similarity between each user and then based on each similarity calculates the predictions. Users having higher correlation will tend to be similar.
4. Based on these prediction values, recommendations are made. Let us understand it with an example:


Consider the user-movie rating matrix:
<br>

<img src="https://i.imgur.com/xJLfump.png" width="500" class = "left" > <br>

Here we have a user movie rating matrix. To understand this in a more practical manner, let’s find the similarity between users (A, C) and (B, C) in the above table. Common movies rated by A and C are movies x2 and x4 and by B and C are movies x2, x4 and x5.

<img src="https://i.imgur.com/oD6uDkZ.png" width="650" class = "left" > <br>


The correlation between user A and C is more than the correlation between B and C. Hence users A and C have more similarity and the movies liked by user A will be recommended to user C and vice versa.

This algorithm is quite time consuming as it involves calculating the similarity for each user and then calculating prediction for each similarity score. One way of handling this problem is to select only a few users (neighbors) instead of all to make predictions, i.e. instead of making predictions for all similarity values, we choose only few similarity values. There are various ways to select the neighbors:

- Select a threshold similarity and choose all the users above that value
- Randomly select the users
- Arrange the neighbors in descending order of their similarity value and choose top-N users
- Use clustering for choosing neighbors


This algorithm is useful when the number of users is less. Its not effective when there are a large number of users as it will take a lot of time to compute the similarity between all user pairs. This leads us to item-item collaborative filtering, which is effective when the number of users is more than the items being recommended.

 

**Item-Item collaborative filtering**

In this algorithm, we compute the similarity between each pair of items.

<img src="https://i.imgur.com/c2H33bX.png" width="800" hight = "600" class = "left" > <br>

So in our case we will find the similarity between each movie pair and based on that, we will recommend similar movies which are liked by the users in the past. This algorithm works similar to user-user collaborative filtering with just a little change – instead of taking the weighted sum of ratings of “user-neighbors”, we take the weighted sum of ratings of “item-neighbors”. The prediction is given by:

<img src="https://i.imgur.com/L3wsIGq.png" width="750" hight = "600" class = "left" > <br>

Now, as we have the similarity between each movie and the ratings, predictions are made and based on those predictions, similar movies are recommended. Let us understand it with an example.
<br>

<img src="https://i.imgur.com/Drm72NN.png" width="400" hight = "600" class = "left" > <br>


Here the mean item rating is the average of all the ratings given to a particular item (compare it with the table we saw in user-user filtering). Instead of finding the user-user similarity as we saw earlier, we find the item-item similarity.

To do this, first we need to find such users who have rated those items and based on the ratings, similarity between the items is calculated. Let us find the similarity between movies (x1, x4) and (x1, x5). Common users who have rated movies x1 and x4 are A and B while the users who have rated movies x1 and x5 are also A and B.

<img src="https://i.imgur.com/SCdVimi.png" width="500" hight = "600" class = "left" > <br>

The similarity between movie x1 and x4 is more than the similarity between movie x1 and x5. So based on these similarity values, if any user searches for movie x1, they will be recommended movie x4 and vice versa. Before going further and implementing these concepts, there is a question which we must know the answer to – what will happen if a new user or a new item is added in the dataset? It is called a **Cold Start**. There can be two types of cold start:

1. **Visitor Cold Start**
2. **Product Cold Start**

**Visitor Cold Start** means that a new user is introduced in the dataset. Since there is no history of that user, the system does not know the preferences of that user. It becomes harder to recommend products to that user. So, how can we solve this problem? One basic approach could be to apply a popularity based strategy, i.e. recommend the most popular products. These can be determined by what has been popular recently overall or regionally. Once we know the preferences of the user, recommending products will be easier.

On the other hand, **Product Cold Start** means that a new product is launched in the market or added to the system. User action is most important to determine the value of any product. More the interaction a product receives, the easier it is for our model to recommend that product to the right user. We can make use of Content based filtering to solve this problem. The system first uses the content of the new product for recommendations and then eventually the user actions on that product.

Now let’s solidify our understanding of these concepts using a case study in Python. Get your machines ready because this is going to be fun!


