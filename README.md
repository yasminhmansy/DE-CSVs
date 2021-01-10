## Milestone 3: Twitter Sentiment Analysis Pipeline

### 1. Choosing countries to analyze
We decided that we will use **Finland** and **Central African Republic** as our happy and sad countries respectively. The reason we chose these 2 countries is because **Finland** has the highest happiness score and **Central African Republic** has the lowest happiness score. This way we can guarantee that we have chosen correctly a happy country and a sad country.

The following figure shows how we chose **Finland** and **Central African Republic**.

![alt text](https://github.com/yasminhmansy/DE-CSVs/blob/main/readme_screenshot.png)

### 2a. Creating the pipeline: *Get 20 tweets for each country*
In order to get the tweets we used the **tweepy** library. We managed to collect 20 tweets in English from both countries. However, in order to collect 20 tweets, we set the count to 200 and returned the first 20 tweets for each country. The reason we did that is because if we set the count to 20, we might get a smaller number of tweets. Finally, we created a task called *get_tweets* that grabs 20 tweets from **Finland** and **Central African Republic**.

### 2b. Creating the pipeline: *Perform sentiment analysis*
To perform sentiment analysis on the tweets, we used Python’s **Textblob** library. The library helps us evaluate the sentiment of each tweet by returning 2 values: polarity and subjectivity. Polarity represents the emotions portrayed in the sentence and ranges from -1 (negative) to 1 (positive). Subjectivity expresses some personal feelings, views, or beliefs and ranges from 0 (objective) to 1 (subjective). We analyzed each tweet separately and returned a polarity and subjectivity value for it.

### 2c. Creating the pipeline: *Average the sentiments*
The average values for the polarity and subjectivity of Finland's 20 tweets and the average values for the polarity and subjectivity of Central African Republic's 20 tweets were calculated. Then it was saved in a csv file called 'twitter_analysis' along with a timestamp to when it was calculated. The reason a csv file was chosen is because it is easier to retrieve the data using it. Finally, we made sure the *write* method used was **a (for append)** to make sure future data does not overwrite the currently saved data.

### 2d. Creating the pipeline: *Compare the results*
In order to compare the results with the happiness score in the Happiness dataset, we have to first read the previously saved csv file. The read data is then totalled for each country. As **Finland** is our happy country and **Central African Republic** is our sad country, we expect **Finland** to have a higher polarity score than **Central African Republic**. This is because as mentioned earlier, higher polarity scores represent more joyful or positive phrases.

Results were gathered from 2/1/2021 to 5/1/2021 and saved in a csv file called 'twitter_analysis':
(timestamp, country, average polarity, average subjectivity)

```sh
2021-01-02 00:00:00.613030,Finland,0.11566964285714285,0.42839285714285724
2021-01-02 00:00:00.613324,Central African Republic,0.07341964285714286,0.3185119047619048
2021-01-03 00:00:00.684335,Finland,0.14617063492063492,0.38214285714285723
2021-01-03 00:00:00.684863,Central African Republic,0.12916666666666668,0.26416666666666666
2021-01-04 00:00:00.436971,Finland,0.10431818181818182,0.2884564393939394
2021-01-04 00:00:00.437814,Central African Republic,0.006689453125,0.1675
2021-01-05 00:00:00.315664,Finland,0.10702245670995672,0.4261165223665223
2021-01-05 00:00:00.316009,Central African Republic,0.08895535714285714,0.20776785714285712
```

Then, values for each country were totalled in the last task in the dag called 'CompareResultsTask':

```sh
[2021-01-06 22:53:53,586] {logging_mixin.py:112} INFO - ----------------------------------------
[2021-01-06 22:53:53,586] {logging_mixin.py:112} INFO - Happiness Score:
[2021-01-06 22:53:53,586] {logging_mixin.py:112} INFO - Finland: 7.537799972534181
[2021-01-06 22:53:53,586] {logging_mixin.py:112} INFO - Central African Republic: 3.1342500195503225
[2021-01-06 22:53:53,586] {logging_mixin.py:112} INFO - ----------------------------------------
[2021-01-06 22:53:53,586] {logging_mixin.py:112} INFO - Total Polarity so far:
[2021-01-06 22:53:53,586] {logging_mixin.py:112} INFO - Finland: 0.4731809163059163
[2021-01-06 22:53:53,586] {logging_mixin.py:112} INFO - Central African Republic 0.29823111979166667
```

We can see overall that **Finland** (with a happiness score of 7.53 approx.) has a higher polarity than **Central African Republic** (with a happiness score of 3.13 approx.). Therefore, we can conclude that happiness score affects the polarity of people's tweets. Also, according to the results, the tweets are overall positive (polarity scores accross the 4 days are larger than zero for both countries). This shows that even countries with low happiness scores still have positive tweets.

