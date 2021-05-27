# Tweet Relevance Analysis through Hashtags

## Process to follow for running the code:

1. Upload the notebook file on colab and run the complete file to train all the model and check the accuracy on test data. 

2. You can also use the pickle file of trained model and can directly use it to classify hijacked or unhijacked on test dataset. 

## Dataset:
link: https://drive.google.com/file/d/1FJiIl7QDe1K6U2gqZ_jdO3_8edHnO6TD/view?usp=sharing

## About Dataset 
We used the Twitter API to collect the tweets corre- sponding to the hashtags which are trending. For that, we had to apply for a Twitter’s developer account which usu- ally takes weeks to be approved. We were asked about the project and about how we were going to use the collected data, once we replied to them about the details of our work, we got access to the public tweets. The tweets obtained had a lot of information along with the text, such as username of uploader, his/her followers and friends count, tweet time of
 uploading, retweet information, location of tweet if available and many more. These tweets were used to create the data- set. Another challenge we faced was that there could only be 100 tweets extracted through the API. The tweets were manually annotated into categories of whether the tweet is hijacked or not. Our initial goal was to collect 10,000 tweets and annotate them to create out dataset. Since tweets can be subjective and it depends on the person whether he/she considers it to be hijacked or not, we followed a majority voting approach. Each of the tweet has been manually read and classified by each and every team member. Out of 5, if more than 2 members need to agree to classify a tweet hi- jacked. This way we removed opinionated bias. Moreover, there were numerous hashtags and their respective popular- ity’s were very dynamic. Ultimately we were able to create a dataset of 9470 samples.
The tweets were collected using Twitter API as men- tioned above and the tweets were retrieved as JSON objects and stored as .csv file. As some tweets had a few columns values as NaN or missing values, when these tweets were stored into a csv file, their column orders were skewed. For example: the User column entry actually got shifted to Geo coordinates columns. This had to be resolved by running a script to iterate over all the columns of the tweet to find the corresponding shifted values. Moreover, since the tweets were collected in batches over a duration of 4-5 days be- cause of the rate limit of twitter API, their format differed a bit. So the script for filtering out the relevant attributes for each batch of tweets varied a little. In the final dataset, we had just the columns named label, full-text, created at, screen name, followers count, friends count, retweets count, favorites count. The rest of the features were not relevant to our goal.

## Introduction
A difficult problem for Twitter is to flag hijacked tweets from accounts with lesser interaction Spread of malicious and spam content through links is easily possible because external web documents are outside the scope of the Twitter ecosystem to process. Many sensitive topics and important topics like mental health get diverted. JusticeforSSR and FarmersProtest were hijacked for personal agenda by certain people/parties. This dis- course has promoted the spread of fake news/manipulated media, bullying, trolling, and slut-shaming among many other problems. Some trending hashtags are just used in the tweets to get better visibility for promoting irrelevant events.

Twitter is one of the most active and open platforms for sharing information and opinions on any subject matter.
Since the onset of hashtags, online communication has become trend-driven. It has also helped in making the content on the platform somewhat structured. People can choose to follow any trend popular at any location in the world. Hashtags drive people’s attention and affect their opinions, help them find people with similar interests, or even build 2. an audience for marketing. Brands, political parties, and other organizations try to leverage hashtag promotions for campaigns and endorsements. But often relevant and mean- ingful twitter trends are targeted through spam and other content under the same hashtag pushed by a legitimate user. This is termed as Hashtag Hijacking. Spammers, tweet farms and bots try to bypass twitter restrictions and guide- lines making people more exposed to privacy and security issues, fake news, etc. and users are always at a risk of being targeted for trolling and cyberbullying.

In this project, we tried to classify legitimate and hijacked tweets/trends by analysing and evaluating text corpus and common spam account attributes under popular hashtags using NLP and machine learning techniques. We curated our own dataset for tweets using Twitter Search and Streaming API for both historical and real-time data.  We further introduced a new attribute of scoring popular user sentiment and evaluating all the tweets under a particular hashtag/campaign to improve upon existing methods. We use tfidf-vectorizer, Count-vectorizer and tweet information(User's friends, followers, retweet count, and favorites count) to train the ML models, and from their output we vote out the best results. We train the following ML models with the above mentioned data: K - nearest neighbour, Support Vector Machine, logistic regression, XG boosting classifier, Gradient boosting, Ada-boost classifier, Random forest classifier, Extra Tree Classifier, Neural Network, Gaussian naive bayes, Multinomial naive bayes classfier. 

## Methodology

The tweets were collected using Twitter API as men- tioned above and the tweets were retrieved as JSON objects and stored as .csv file. After the creation of the dataset of sufficient size, we proceed with dataset cleaning and using NLP techniques like tokenization, stop-words removal, and stemming/ lemmati- zation. Techniques like tf-idf, ranking algorithms, and vec- tor space models are used for scoring words.

We then applied various techniques on the obtained posts or tweets and obtain the sentiment, retweets/reposts, likes, uploader, uploader’s data (like followers, following, verified or not), related hashtags (their relative scores), and the tf-idf score of the post. The Machine Learning models we used are K - nearest neighbour, Support Vector Machine, lo- gistic regression, XG boosting classifier, Gradient boosting, Ada-boost classifier, Random forest classifier, Extra Tree Classifier, Neural Network, Gaussian naive bayes, Multino- mial naive bayes classifier. We let all the ML models run through the dataset we prepared, which contains a detailed examination of the posts and annotated classes (hijacked or not). After which we used the obtained weights to vali- date the rest of the dataset which will ultimately return us an accuracy, recall, F1- score, precision measure, and their macro-average and weighted average.

## Results

After the whole dataset was created and the models were trained, we obtained an accuracy of 95.0% with multinomial naive bayes.
we have up-sampled it to remove class imbalance, which contains a detailed examination of the posts and annotated classes( hi- jacked or not). The obtained weights were used to validate the rest of the dataset which ultimately returned us an accu- racy and precision measure. We then used all these model and applied voting classifiers on these classifiers to obtain the best generalised model to avoid overfitting and saved this model and other individual best models using pickle for future use. The best model is MLP which gave us accuracy of 97.1
After calculating the cumulative score of all the above 30 models by the voting classifier, we obtain the following statistics:
* Accuracy: 0.981
* Precision: 0.98
* Recall : 0.98
* F1-score: 0.98
* Support : 4472

## Conclusion

We trained K - nearest neighbour, Support Vector Ma- chine, logistic regression, XG boosting classifier, Gradient boosting, Ada-boost classifier, Random forest classifier, Ex- tra Tree Classifier, Neural Network, Gaussian naive bayes, and Multinomial naive bayes classifier for the Twitter user’s and tweet’s data, Text of the tweet by transforming it to the word count vectors and tf-idf vectors. After running those models on the testing set, the best outcome obtained was an accuracy of 0.98, using SVM classifier which was trained us- ing the tf-idf vectors of the text of tweets. After combining the results obtained from the models we obtain an accuracy of 0.981 which means the post voting results are better and are used instead of any single method. All this was done on a dataset collected, annotated and compiled manually by the group members.
