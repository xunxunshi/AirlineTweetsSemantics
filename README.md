# AirlineTweetsSemantics
Like all other businesses,the airline business can have incidences of poor services, ranging from lost luggage to delayed flights. Many unhappy customers will often express their frustration by tweeting messages to specific airlines. Traditionally, trained employee personnel may be required to respond to each customer. This method is very time-consuming for the customer and the business and may result in additional costs to the business.Therefore, building a machine learning algorithm that can identify these tweets' semantics, followed by a chatbot that handles the customer complaint, will replace a slow manual helpline with a rapid, streamlined, and less expensive customer service.The project demonstrates the building of a classifier that can predict the tweet semantics into different classes: positive, negative, and neutral. A chatbot can also be implemented to respond to the negative tweets appropriately based on each different customer issue.

* This classifier is built on the Kaggle dataset containing over 14000 instances of labelled airline tweets.
* Implemented different feature engineering of BOW/TF-IDF with other supervised ML algorithms such as Random Forest, SVC and NV, and ensemble methods. 
* Because majority of the instances are negative, SMOTE was also applied to generate more positive and neutral instances for the ensemble method. 
* Our training dataset was divided into 70% for cross-validation training (hyper parameter tuning), 30% for tuning. The 10-fold cross validation was implemented for the grid search.
* For final application: when airlines that recieve the tweets @ them from client, the classifier is used to determine the semantics of the tweets. All tweets identifid as negative are sent to the complaint-handling chatbot. 
* Experience our chatbot here:  https://bot.dialogflow.com/airline-problem-handling-chatbot. 

# Code and Resources 
* ***ML Dataset*** :  https://www.kaggle.com/crowdflower/twitter-airline-sentiment 
* ***Python***: 3.7 
* ***Packages***: Pandas, Numpy,Re,NLTK,Spacy,Scikit-Learn,Matplotlib,Seaborn
* 
