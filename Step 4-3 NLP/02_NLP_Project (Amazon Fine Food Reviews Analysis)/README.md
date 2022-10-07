# Amazon Fine Food Reviews Analysis


Data Source: https://www.kaggle.com/snap/amazon-fine-food-reviews


<h4> Objective:</h4>
Given a review, determine whether the review is positive or negative.

<h4><li>How to determine if a review is positive or negative?</li></h4>
We could use the Score/Rating. A rating of 4 or 5 could be cosnidered a positive review. A review of 1 or 2 could be considered negative. A review of 3 is nuetral and ignored. This is an approximate and proxy way of determining the polarity (positivity/negativity) of a review.


<h1>Dataset</h1><br>
This dataset consists of reviews of fine foods from amazon. The data span a period of more than 10 years, including all ~500,000 reviews up to October 2012. Reviews include product and user information, ratings, and a plain text review. It also includes reviews from all other Amazon categories.

<h4>Attribute Information:</h4>

There are a total of 10 columns in total in the Amazon Fine Food review dataset.

- Id :  Row Id
- ProductId : Unique identifier for the product.
- UserId : Unique identifier for the user.
- ProfileName : Profile Name of the User.
- HelpfulnessNumerator : Number of users who found the review            helpful.
- HelpfulnessDenominator : Number of users who indicated whether they found the review helpful or not.
- Score : Rating between 1 and 5.
- Time : Timestamp for the review.
- Summary : Brief summary of the review.
- Text : Text of the review.
