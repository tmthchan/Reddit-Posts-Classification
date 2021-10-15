
# Project 3: Classifying Subreddit Posts using NLP  

## Executive Summary
Reddit is one of the most under utilized social media marketing platforms with 330 million monthly active users. AutoModerator is a site-wide moderation tool that can be set up and customized in any subreddit to assist in moderating that community. Natural Language Processing (NLP) is a field in machine learning with the ability of a computer to understand, analyze, manipulate, and potentially generate human language. As part of the Development Team in Reddit, we have been tasked to develop a NLP model to classify posts in subreddits correctly. The overall model will consist of two parts, a vectorizer to convert the individual words in each subreddit post to numeric values and a classification model that develops the classification algorithm using the train dataset and predicts the classification outcome of each subreddit post. Using Pushshift's API, 5100 posts from each subreddit, r/stocks and r/CryptoCurrency were extracted. However, after removing the posts with no body text, the number was reduced to 1700 posts for each subreddit. The clean dataset was vectorized using 3 methods, count vectorization, 2gram vectorization and TF-IDF vectorization to convert the text into numeric values. However, only the dataset from count vectorization and TF-IDF vectorization were used to train and evaluate the classification models. When evaluating the 4 model combinations, TF-IDF vectorization together with Logistic Regression produced the best results. The model had an accuracy score of 0.961 and recall score of 0.973. The accuracy score implies that 96.1% of posts in both subreddits are classified correctly. The recall score implies that 97.3% of posts in r/stocks are correctly classified. The two metrics highlighted above ensure that every post in the subreddit is of high relevance and users will have access to more useful content. This will maintain a strong engagement with the community of reddit users and advertisers will be more willing to spend on campaigns to reach out to this group.

## 1. Introduction
Reddit is one of the most under utilized social media marketing platforms with 330 million monthly active users.[1] Reddit boasts a large, highly engaged audience base. Ranked third behind Facebook and Instagram for monthly active social media users, Reddit also offers a higher retention rate than other platforms. [2] Reddit generated more than $100 million in total ad revenue in 2019 and that figure was expected to rise over 70% for 2020. [3] 

AutoModerator is a site-wide moderation tool that can be set up and customized in any subreddit to assist in moderating that community. It can handle many of the sometimes repetitive tasks done by moderators. The moderation tool can send a modmail to alert about potential issues, reply to posts with helpful comments like pointing users to subreddit rules or wiki, remove or flair posts by domain or keyword, require all comments to include the word “cat,” and take many, many other actions automatically.[4]

Natural Language Processing (NLP) is a field in machine learning with the ability of a computer to understand, analyze, manipulate, and potentially generate human language. Two classification models used in this project are Naive Bayes algorithm and Logistic Regression. The Naive Bayes algorithm uses the probability of observing predictor values, given an outcome, to estimate what is really of interest: the probability of observing outcome Y = i (0 or 1), given a set of predictor values. Logistic regression is analogous to multiple linear regression, except the outcome is binary. Various  transformations are employed to convert the problem to one in which a linear model can be fit. Unlike K Nearest Neighbor (KNN) and Naive Bayes, logistic regression is a structured model approach rather than a data-centric approach.[5]

## 2. Problem Statement
As part of the Development Team in Reddit, we have been tasked to develop a NLP model to classify posts in subreddits correctly. The two subreddits selected for this project are r/stocks and r/CryptoCurrency. Both subreddits have about 3 million members each. These two subreddits were chosen to develop the NLP model as they contain a large volume of text data due to the frequent contributions of their respective communities.

The overall model will consist of two parts, a vectorizer to convert the individual words in each subreddit post to numeric values and a classification model that develops the classification algorithm using the train dataset and predicts the classification outcome of each subreddit post.

The three vectorizers to be studied are count vectorizer, ngram-vectorizer and TF-IDF vectorizer. While the two classification models, Naive Bayes and Logistic Regression, will be used to classify the subreddit posts. The models will be evaluated using the accuracy and recall scores. 

Accuracy is the percentage of cases classified correctly. When looking at classifying subreddit posts, this metric measures the proportion of posts in both subreddits that are classified correctly. Recall (or Sensitivity) is the percentage of all 1s that are correctly classified as 1s. In this case, the posts in r/stocks are assigned to class 1 and the posts in r/CryptoCurrency are assigned to class 0. Therefore, recall measures the proportion of posts in r/stocks that are classified correctly. This ensures that posts meant for r/stocks are not wrongly excluded. The closer the accuracy and recall scores are to 1, the better the model performance.

The accuracy and recall scores will be compared across the different model combinations. In addition, we will use the null accuracy as a baseline to determine the level of improvement that our proposed model will provide.

This model will improve the current Auto Moderator Tool to assist human moderators in maintaining high quality content in their subreddits. The content quality of subreddit posts is important as it contributes to high user engagement as users will return to discover and share highly relevant content. This helps to grow the community of reddit users and increases the traffic volume to the platform. 

Overall, developing an effective NLP model to classify reddit posts will have a big impact on attracting businesses to use reddit as an advertising platform and generate more business revenue through advertising. 


## 3. Data Dictionary
|Feature|Type|Dataset|Description|
|---|---|---|---|
|**subreddit**|*object*|data|This shows the subreddit that a post belongs to.| 
|**selftext**|*object*|data|This is the body of text in the subreddit post.| 
|**title**|*object*|data|This is the title of the subreddit post.|
|**created_utc**|*int64*|data|This is the date and time in UTC format that the post was posted on the subreddit.|
|**posttext**|*object*|data|This is combination of all the text in the title and body of each post.|

## 4. Summary of Analysis
Using Pushshift's API, 5100 posts from each subreddit, r/stocks and r/CryptoCurrency were extracted. However, after removing the posts with no body text, the number was reduced to 1700 posts for each subreddit. Before vectorization, the body text and titles were combined into a new column. The combined text was cleaned using several steps. The first step was to remove punctuations, followed by tokenizing the words, then removing the stop words before lemmatizing the remaining text. Lemmatization was chosen over stemming as accuracy was prioritized over speed in this model. 

The clean dataset was vectorized using 3 methods, count vectorization, 2gram vectorization and TF-IDF vectorization to convert the text into numeric values. However, only the dataset from count vectorization and TF-IDF vectorization were used to train and evaluate the classification models. The 2gram vectorization was useful in discovering common word pairs that appeared in each subreddit. The two classification models studied were Naive Bayes and Logistic Regression. As there are three Naive Bayes models, Bernoulli Naive Bayes, Multinomial Naive Bayes and Gaussian Naive Bayes, all three models were evaluated. Multinomial Naive Bayes displayed the highest accuracy scores for both vectorization methods. 

When evaluating the 4 model combinations, TF-IDF vectorization together with Logistic Regression produced the best results. The model had an accuracy score of 0.961 and recall score of 0.973. The accuracy score implies that 96.1% of posts in both subreddits are classified correctly. The recall score implies that 97.3% of posts in r/stocks are correctly classified. 

## 5. Conclusions and Recommendations
The two metrics highlighted above ensure that every post in the subreddit is of high relevance and users will have access to more useful content. This will maintain a strong engagement with the community of reddit users and advertisers will be more willing to spend on campaigns to reach out to this group. At the same time, being able to incorporate this model into the auto moderator tool will help reddit moderators reduce the effort needed to filter out irrelevant content. That way, they could divert more focus to growing their subreddits and engaging with users. This NLP model can be used on other subreddits to improve the quality and relevance of their content.

Moving forward, posts that are wrongly classified under a subreddit can be forwarded to the moderators for review. Together with the word pairs that are discovered through the analysis, the moderators can use their experience and judgement to decide if the posts should be reclassified. In addition, we can use other classification methods like Adaptive Boosting to build a model that is able to learn from misclassified posts to improve the model performance.

## 6. References
1. Foundation Team,  January 07, 2021, Reddit Statistics For 2021 (Demographics, Usage & Traffic Data), https://foundationinc.co/lab/reddit-statistics/

2. Paula Thompson, February 5, 2020, Reddit Advertising: Is it Worth it and How to Get Started, https://www.effectivespend.com/blog/get-started-reddit-advertising/#Reddit-Demo

3. Sahil Patel, Dececember 1, 2020, Reddit Claims 52 Million Daily Users, Revealing a Key Figure for Social-Media Platforms, https://www.wsj.com/articles/reddit-claims-52-million-daily-users-revealing-a-key-figure-for-social-media-platforms-11606822200

4. Reddit Help, 2021, AutoModerator, https://mods.reddithelp.com/hc/en-us/articles/360002561632-AutoModerator

5. Peter Bruce, Andrew Bruce, and Peter Gedeck, 2020, Practical Statistics for Data Scientists, O’Reilly Media, Inc., Sebastopol, CA, pp. 220.

