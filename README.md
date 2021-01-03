# DE-CSVs
CSVs for Data Engineering

## Milestone 3: Twitter Sentiment Analysis Pipeline

### 1. Choosing countries to analyze
We decided that we will use **Finland** and **Central African Republic** as our happy and sad countries respectively. The reason we chose these 2 countries is because **Finland** has the highest happiness score and **Central African Republic** has the lowest happiness score. This way we can guarantee that we have chosen correctly a happy country and a sad country.

The following figure shows how we chose **Finland** and **Central African Republic**.

![alt text](https://github.com/yasminhmansy/DE-CSVs/blob/main/readme_screenshot.png)

### 2a. Creating the pipeline: *Get 20 tweets for each country*
In order to get the tweets we used the **tweepy** library. We managed to collect 20 tweets in English from both countries. However, in order to collect 20 tweets, we set the count to 200 and returned the first 20 tweets for each country. The reason we did that is because if we set the count to 20, we might get a smaller number of tweets. Finally, we created a task called *get_tweets* that grabs 20 tweets from **Finland** and **Central African Republic**.

The figure below shows a screen shot of the *get_tweets* task.
![alt text](https://github.com/yasminhmansy/DE-CSVs/blob/main/Picture1.png)

### 2b. Creating the pipeline: *Perform sentiment analysis*
To perform sentiment analysis on the tweets, we used Python’s Textblob library. 
