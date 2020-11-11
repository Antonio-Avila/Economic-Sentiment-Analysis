# Economic Sentiment Analysis



**_Intro:_** When this project was initially started, there was a lot of speculation about another possible recession. It had been nearly 12 years since the Great Recession of 2008 and the United States stock markets had been (and to a lesser extent continue) enduring long bull run. Many market and economic experts began warning of a looming bubble and coupled with an escalating trade war with China, the voices of the concerned began getting louder and louder.
Little did we know at the time, a virus outbreak was occurring in the relatively unknown Chinese city of Wuhan, a virus outbreak would be the catalyst to the recession and would change the lives of people around the world.
*Goal:* The goal of this project was to see how financial news organizations were reporting at the time and determine the sentiment of the articles they were publishing about the state of the economy.

## Methodology
The goal of the project is fairly simple: use news articles from reputable financial news sources and classify the articles as having a positive or negative sentiment to gauge whether experts expected the economy to continue growing or enter a recession. Unfortunately, it was not as simple an it initially seemed due to having to deal with paywalls for articles from NYT and the Economist, for example. To get around this issue, I opted to analyze their tweets. This seemed like a reasonable compromise since most news organizations tend to post the headline of their articles along with a link to the full article. Although using the articles in their entirety would have been preferable, I believe the headlines should suffice since any news organization worth its salt would write a headline that is representative of and accurate summarizes the article. Moreover, since sentiment analysis is typically performed on a labelled set, I had to generate sentiment labels for each tweet so the model could learn from. Since labeling 50k+ tweets can be very time consuming, I had to come up with an approach to quickly label each tweet as giving a positive, neutral, or negative sentiment, other than painstakingly reading each tweet and labeling manually.

- Gather tweets from financial-focused news organizations' twitter accounts, such as NYTimes Business, MarketWatch, WSJ, Reuters, FOXBusiness, and several others.
- Cleaned the tweets to exclude superfluous text will only serve to add noise
  - examples include links, mentions of other twitter users, hashtags, etc
-  Used Spacy to lemmatize and save the part of speech (for later use) the cleaned text
- Used 2 lexicons, Afinn and SentiWordNet, to score the sentiment of the tweets and took the sign of the score to use as the target/response variable
  -- simple scoring using the lexicons made the problem a little more complex since each tweet had varying lengths, there wasn't an obvious way to standardize the score. By taking the sign, it help me simplify the tweet to say whether it was positive if > 0, negative if < 0, or neutral if = 0.
- Next step is to convert the text into some form of numerical representation to feed into the model
  - to find the best approach, I tried using a few different methods: Doc2Vec, Word2Vec, and TF-IDF
- The final steps in the process were modeling and tuning the modeling.
  - like in previous steps, I tried a variety of models to find the optimal model.
  - some models fitted were neural networks (deep and recurrent), naive-bayes classifier, and logistic regression.

## Things left to explore
There were still a few avenues that I felt could be further explored. I would have liked to have been able to gather tweets from a few more sources and separate them based on their political leanings to determine how "conservative" vs "liberal" leaning news organizations reported on the economy and if their sentiments changed as countries inevitably faced the prospect of shutting down due to COVID-19.
