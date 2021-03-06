# Tweeting Tesla<br>
#### Project 2: Tamari Bachulashvili, Aidan Dowdle, Lisa Esberger, Minyeong Han, Carlos Tacchi<br>

## Introduction<br>
Using NLP, sentiment analysis, and other features we used machine learning to determine whether<br>
Elon Musk’s tweets have an impact on Tesla’s stock price controlling for the market.  We then used<br>
these findings to develop algorithmic trading programs to trade in Tesla Stock.<br>

Some of the key questions that we wanted to answer:<br>
1.  Is there a correlation between Elon Musk’s Tweets and returns?<br>
2.  Can we predict the change in daily and weekly returns using machine learning?<br>
3.  Could investors and day traders benefit from an algorithm that tracks Tweets?<br>
4.  Which (buy, sell, hold) strategy could be the most profitable?<br>

## Data Collection/Cleaning<br>

The data collection and cleaning process was lengthy.  We pulled the Twitter data from a scrapper<br>
called Twint that pulled Elon Musk's tweet as well as engagement metrics that we thought would be<br>
valuable to use as Machine Leaning features.<br>

![elon_tweets](https://github.com/tamobee/project2/blob/main/png_file/elon_tweets.png) 

After uploading the tweets, we encountered some practical problems during the cleaning process.<br>
We had to write lengthy code to push weekend and off hour tweets and engagement into the next<br>
trading day.  Once this was accomplished, we pulled the stock data from Yahoo Finance as it<br>
incorporated stock splits in the data.  We also pulled dates on earnings announcements from<br>
Beautiful Soup as this could also be an important feature for movement in stock price.<br>

From the twitter data itself we used NLP to understand the sentiment of the tweets.  From <br>
the compound score we also created positive, negative and neutral labels.  After running <br>
frequency analysis on most common words, we manually intervened to remove non-relevant stop <br>
words for the most accurate results.<br>

![frequency_analysis](https://github.com/tamobee/project2/blob/main/png_file/frequency_analysis.png)

## Data Exploration<br>

As we looked through our data to determine our features in our model we focused on a few key ideas<br>

![twitter_engagement](https://github.com/tamobee/project2/blob/main/png_file/twitter_engagement.png)

We found there to be a correlation between engagement from other twitter users and Tesla stock movement<br>
We also found there to be a high degree of correlation between sentiment and Tesla stock movement.<br>

It is important to note that when determining our y variables for Tesla Stock, instead of using Tesla<br>
stock price change we used a daily and weekly basis.  We also considered for macro-climate economic<br> 
bias by controlling with a tech-stock based index fund (QQQ).  Our output was the difference between Tesla<br>
and QQQ on daily/weekly basis.

## Model Analysis

We used random forest regression machine learning as a way to reduce over fitting in our model so we could<br>
look at mean prediction of the individual trees as output.  Our x variables included Sentiment analysis (compound, positive, neutral, negative), <br>
engagement (retweets, replies, likes, etc), keywords<br>
(both individual keywords and keyword strength) and quarterly earning report dates were used.  After training<br>
our model we achieved a success with a MSE score on daily return for test data at .001 (train data MSE .0005).<br>
The weekly returned similar results with our test data at .002 (train data MSE .006).  Overall feature importances<br>
were skewed towards twitter engagement and compound sentiment score.

![features](https://github.com/tamobee/project2/blob/main/png_file/features.png)

## Algo Results/ Project Conclusions

We took our model results and looked at buy/sell flags for Tesla.  When running an algo that traded these flags<br>
we found that our results were not as good as buy and holding strategies for Tesla given its quick rise. <br> We had tested the 5-day and 10-day (profit of $1,021,691.88), 
10-day and 20-day ($1,840,235.96), 
20-day and 50-day ($1,386,095.99), and 50-day and 100-day ($1,914,389.90).  With Tesla’s relatively continuous upward trajectory from 2016-2020, buying and holding this position throughout all four years would have most likely yielded the greatest reward.  

We looked at four different buy and hold strategies:<br>
![features](https://github.com/tamobee/project2/blob/main/png_file/algo_results.png)



Overall, we believe we answered our questions that we set out initially.<br>

We  discovered a correlation between Elon Musk’s Tweets and changes in Tesla’s returns using sentiment analysis.<br>
Our model appeared to predict daily and weekly returns well as it achieved a mean squared error close to zero.<br>
Our algo trading exploration provided mixed results and although we felt it could not be used for day trading,<br>
it could be used to indicate timely entry points to the market.<br>


