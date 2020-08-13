# Project 3: Web APIs & Classification

_Author: Evonne Tham_



## Problem Statement

![](https://i.ytimg.com/vi/5SyLy-0Qgnw/maxresdefault.jpg)

As the rally is nearing, everyone, whether you are a politician or a citizen, everyone starts wonder about where are we in terms of poll standing? In order to look into that to get some perspective, posts from two subreddits, r/Democrats and r/Republicans will be used to analyze.

However, post from subreddits are in natural language which computer cannot understand. And finding the right subreddit that a post belong, to measure success, can be tricky, especially if there are over a hundred thousand of active subreddits with overlapping content. This is definitely no easy task for a human. Hence Natural Language Processing (NLP) will be used to train classifiers. A classification model can then be constructed based these datasets. This model would help to pinpoint the common buzzwords used.

Ultimately, with this the model, it can help individuals such as the voters or the campaigners as they are more likely to make sound decision based or to discover compaign opportunities respectively.

## Executive Summary

1. ***“Trump rally gives Fox News largest Saturday night audience in its history”***
2. ***”That feel when the million person rally you expected has only 6,150 people”***

*Can you guess if these belong to the Democrats or Republican topic?*


Reddit is a well-known social news aggregation, web content rating, and discussion website where members submit content such as links, text posts, and images to the site. Posts are organized by subject into user-created topics called "subreddits", which cover a variety of topics that focuses on different content and have different moderation cultures, resulting in a consistent culture within each subreddit. This is exactly what an Natural Language Processing (NLP) can do. However, how well can a model score given that different subreddits can have similar syntax that overlap one another.


In order to see to do so, we have selected and scrapped the subreddit topic on Democrats and Republicans with 990 and 986 observations respectively as of 24th June 2020 with the use of Reddit API. 

One hindrance is that Reddit throttles requests to once every two seconds. Hence, a break in between requests was incorporated. Once the data was fully scraped, it was then cleaned, merged and explored. 

With the help of NLP (CountVectorizer and TfidVectorizer) to split comments up into words and convert each comment into a vector of word frequencies, which is then fitted into three classification models: Logistic Regression, Multinomial Naive Bayes and KNearest-Neighbors
With GridSearch, it is found that Multinomial Naive Bayes with TfidfVectorizer worked fairly well with an accuracy score of close to 80%, even though both subreddits were fairly similar in nature.

By classifying posts to subreddits, it could be very helpful for targeted advertising, as one could find out what topics most interest a certain user.

## Data Dictionary

|Feature|Type|Dataset|Description|
|---|---|---|---|
|id|*object*|df|Unique id of a comment|
|title|*object*|df|Title of the post |
|comment|*object*|df||
|date_created|*datetime*|df|When was post created |
|score |*int*|df|How many upvotes the comment has|
|subreddit|*int*|df|Subreddit that the comment was in. this will be the target variable|
|title_len|*int*|df|Word count of a title|


## Conclusion and Recommendation 

CountVectorizer and TfidfVectorizer from scikit-learn were used to convert the text data to numeric features. CountVectorizer achieved a better accuracy score for a baseline logistic regression model. Logistic regression, Multinomial Naive Bayes and KNearest-Neighbour models were tested. With the help of GridSearch, Multinomial Naive Bayes with TF-IDF Vectorizer performed the best where it achieved the best accuracy scores of 0.84 and 0.73 for train and test set respectively.

According to the results, out of 446 comments from the testing set, 121 comments were predicted wrongly. As these post consist of words are very generic, hence it tend to classify wrongly. 

In order to improve future research, we could collect more data through third party data storage such as Pushshift, alternatively we could harness more resources from other platforms such as twitter and facebook. On top of which, models such as Decision Tree, Random Forest with bagging or boosting, or SVM can be considered to optimize outcome. 

Ultimately, with this the model, it can help individuals such as the voters or the campaigners as they are more likely to make sound decision based or to discover compaign opportunities respectively.