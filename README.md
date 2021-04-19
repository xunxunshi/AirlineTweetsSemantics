# Predicting Airline Tweets Semantics
Like all other businesses,the airline business can have incidences of poor services, ranging from lost luggage to delayed flights. Many unhappy customers will often express their frustration by tweeting messages to specific airlines. Traditionally, trained employee personnel may be required to respond to each customer. This method is very time-consuming for the customer and the business and may result in additional costs to the business.Therefore, building a machine learning algorithm that can identify these tweets' semantics, followed by a chatbot that handles the customer complaint, will replace a slow manual helpline with a rapid, streamlined, and less expensive customer service.The project demonstrates the building of a classifier that can predict the tweet semantics into different classes: positive, negative, and neutral. A chatbot can also be implemented to respond to the negative tweets appropriately based on each different customer issue.

# Data 
* This classifier was built using the Kaggle dataset containing over 14000 instances of labelled airline tweets.
* Input feature: Tweet Texts with 14000 instances
* Output featrue: Semantics of the text with three cateogries [Positive, Negative, Neutral]

# Model Selection and Tuning 

### Preprocessing: 
*  Tweets were lemmatized 
*  Tweet incidences with less a snetimental confidence scores less than 0.5 was dropped
*  Because majority of the instances are negative, SMOTE was also applied to generate more positive and neutral instances for the ensemble method. 
### Feature Engineering: 
* Bag of Words 
* TF-IDF 
### Models Implementated: 
*   Support Vector Classifier
*   Random Forest
*   Naïve Bayes
*   Ensemble Methods with the three classifiers  (with and without SMOTE) 
### Model Building Process:
*  Training dataset (70%): used for 10 fold cross-validation (train on 90% instances test on 10% , repeated 10 times) for hyper parameter tuning 
*   - The aggregated training dataset results was used for hyper parameter selection of each model 
*  Validation Data (30%) for testing 
*   - The tuned model was tested on the validation data
*   - The final accuracy performance is 
###  Application : 
*  When airlines that recieve the tweets @ them from client, the classifier is used to determine the semantics of the tweets. All tweets identifid as negative are sent to the complaint-handling chatbot. 
* Experience our chatbot here:  https://bot.dialogflow.com/airline-problem-handling-chatbot.
# Results 

### Summary of Hyperparameters From Each Model
The table below demonstrates the optimal hyperparameters chosen for each model based on the 10 fold cross validation results. 
![image](https://user-images.githubusercontent.com/29676594/115295138-6a0d8700-a127-11eb-973e-1286ce667a6f.png)

### Summary of Test Results From Each Tuned Model 
This is the summary of the accuracies for each tuned model on the test data set.  The optimal classification algorithm was using TF-IDF with SVC, which achieved very similar results with ensemble method. Using smote actually did not improve the algorithm, and this is simply because majority of the tweets were negative semantics, so creating more positive and neutral semantics reduced errors in classifying these tweets into negative semantics, but it did also introduce lots of new errors where the negative semantics were being misclassified into positive or neutral tweets.

![image](https://user-images.githubusercontent.com/29676594/115296341-d76de780-a128-11eb-943e-0d00e6a2cc41.png)

### Bench Marking Results 
In 2019, Monika et al.  performed sentiment analysis of US Airline Tweets using LSTM/RNN and reported accuracy of approximately 75% on test data and 85% on training data  [https://ieeexplore.ieee.org/abstract/document/8971592/], which is of lower performance than this model. It’s possible that they did not fully tune the network well, but this also goes to show that using a more complex and most popular model will not always increase the performance. 

### Error Analysis 
The optimal algorithm chosen was SVC (C=1, hinge loss) with TF-IDF. 

The most common error for SVC with TF-IDF is with neutral sentiments that are misidentified as negative sentiments, as shown by the confusion matrix below. 

![image](https://user-images.githubusercontent.com/29676594/115297448-36802c00-a12a-11eb-9317-709c7dc8a685.png)

To identify these errors in depth, the list of the wrongly predicted tweets was printed out for analysis. It became more obvious that some of the tweets although were manually labelled as “neutral”, this labelling could become very subjective depending on this person.
 For instance, these are three sample tweets that were manually labelled as neutral that the machine has labelled as negative: 
-	Tweet A: “there is nothing on my USAir cc at this point, but the email stated I would be charged thanks for the reply” 
-	Tweet B:  “just disappointed with the flight booking problems process and add fees to sit together on a more crowded flight not impressed so far”
-	Tweet C:  “Is there nothing that can be done online to help I bought these as a birthday present just trying to be able to afford a change”

Tweet A is clearly a complaint, with some sarcastic and annoyance tone at the end complaining about the lack of reply. Tweet B also displays a sign of disappointing, where the client is clearly not “impressed”. Tweet C indicates that the person feels a sense of hopeless as they are asking for help. However, all three tweets did not express very strong sentiments of anger or sadness. This is when manually annotated sentiments can become subjective, as human emotions are complex, and different people may even interpret it very differently. 

Therefore, these errors may not false negative, but true positives that were mislabeled by the person annotating these texts. Furthermore, this example also highlights the difficulty with providing cohesive sentimental training data for the machine learning algorithm to learn. The complexity of the human emotion and language is complicated, and sometimes it’s hard to draw the border of simply annotating it as positive, negative and neutral. 

# Code and Resources 
* ***ML Dataset*** :  https://www.kaggle.com/crowdflower/twitter-airline-sentiment 
* ***Python***: 3.7 
* ***Packages***: Pandas, Numpy,Re,NLTK,Spacy,Scikit-Learn,Matplotlib,Seaborn



# Authors
* Airline tweet classifier : Xun Xun Shi
* Chatbot attached : Xun Xun Shi, Lasya Bhaskara, Tulika Shukla
