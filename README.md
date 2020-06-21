# Tweet Sentiment Classification
> The task is to predict the sentiment of Tweets about four technology companies, Apple, Microsoft, Google, and Twitter.
There are three different level of sentiments (Positive, Negative and Neutral). A classifier will be trained to predict the level of sentiments.

## Data pre-processing steps

Here are my steps for data pre-processing:

1.	Change all the words to lower case
2.	Apply Stemming and Lemmatization for each tweet
3.	Remove the stop words on each tweet
4.	Summarize the top 30 frequency words:
[('http', 1086), ('apple', 823), ('google', 738), ('microsoft', 727), ('twitter', 555), ('android', 368), ('rt', 346), ('iphone', 184), ('new', 181), ('nexus', 150), ('samsung', 136), ('sandwich', 135), ('ice', 135), ('cream', 134), ('ice cream', 134), ('cream sandwich', 130), ('phone', 121), ('windows', 109), ('galaxy', 104), ('just', 103), ('galaxy nexus', 101), ('ics', 90), ('like', 89), ('android google', 88), ('facebook', 88), ('siri', 87), ('google android', 82), ('ballmer', 80), ('app', 80), ('steve', 74)]
5.	Remove the followings words. They are about the product and brand names. I assume they are not relevant with the sentiment level.
["http:", "apple", "google", "microsoft", "twitter", "android", "iphone", "samsung", "windows", "galaxy","nexus","sandwich","ice cream","sandwich","facebook","siri"]
6.	Encode the sentiment level to [0 ,1, 2], which represent to [negative, neutral, positive].
7.	Create top 25 words list per each sentiment level for 8f -8g additional features.
8.	Build the additional features for training. Here is the list:  
    a.	Word Count: The number of words of each tweet  
    b.	Stop words percentage: The percentage of stop words in each tweet  
    c.	Non-stop words percentage: The percentage of non-stop words in each tweet  
    d.	Is Contain URL: 1 represent URL exists in tweet, otherwise 0  
    e.	Punctuation percentage: The percentage of punctuation in each tweet  
    f.	Positive words percentage: The percentage of positive words in each tweet  
    g.	Negative words percentage: The percentage of negative words in each tweet  
    h.	Neutral words percentage: The percentage of neutral words in each tweet  

9.	Apply CountVectorizer and Tfid-transformer on each tweet before classification.


## Classifiers

Here are the classifiers I used to do model training. Each is do cross validation to select the best parameters:  

A.	Logistic Regression  
B.	K-NN (3)  
C.	SVM  
D.	Random Forest Classifier  
E.	AdaBoost Classifier (Decision Tree)  
F.	Gradient Boost Classifier (Decision Tree)  
G.	Bagging Classifier (Decision Tree)  
H.	Bagging Classifier (SVM)  

## Result
| Classifiers | Test Set Accuracy  (From Kaggle Submission) |
| --- | --- |
| Logistic Regression | 0.7763 |
| K-NN (3) | 0.7185 |
| SVM | 0.7899 |
| Random Forest | 0.7354 |
| AdaBoost | 0.7296 |
| Gradient Boost | 0.7315 |
| Bagging (Decision Tree) | 0.7471 |
| Bagging (SVM) | 0.7802 |
