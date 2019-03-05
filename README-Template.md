# Assignment 1 - Analysing Yelp Data set

One Paragraph of project description goes here

## Getting Started

The data set given is in Json format. Data set is comprised of review.json file containing 600000 reviews, the object of the assignment is to classify the reviews as positive
negative and neutral. Along with that predict the required data. For this project, I have used 4 classifiers.
1. Naive Byes
2. Random Forest
3. Knn
4. SVM

### Prerequisites

The data set is huge to be handled by my system so I have google colab for doing all processing and analysis. Uploaded all required data set in google drive.

## Methodology 
Data being huge, it became very difficult at first to set the environment. To come with a algorithm that will label each review in the data set I have performed following steps:


```
Step1 . Data Preprocessing and environment setup
	The data is first uploaded in google drive for access in google colab. 
	Next, converted each review text in lowercase also removed all puntutation.

Step2 . Created list of Positive,Negative and Neutral keywords after through analysis of data. 

Step3 . Created an algorithm to classify each review in the data set
	For each review in the data set, tokenized the words, next for each word algorithm matches it with the list of keywords. To keep track of the words, used 3 counters.
	pos = 0
    neg = 0
    neu = 0

    If the encountered word is positive, pos++, if negative, neg++ and if neutral neu++. 
    Once all the counters are updated for a review the counters are compared, out 3 whichever counter is highest accordingly the sentiment are assigned to a given review. 
    This algorithm actually finds the score for each review and assignment sentiment as per the score of the counter

Step4 . Append predicted sentiment of the review in the dataframe that will be later used by classifier

Step5 . Set up classifiers

Step6 . Find scores for all classifiers

Step7 . Predict the reviews from the classifier and check with star rating if it's classified or misclassified.


```

## Running the tests

I followed approach of divide and conquer, first I picked up 1000, 3000, 50000, and finally 300000 to check what amount of data maximum can be supported by google colab.
Given the limit of processing speed I could run my algorithm for maximum 300000 reviews. When considering 600000 reviews even google colab couldnt support me with processing power. Thus I am submitting my analysis that I got for maximum 300000 reviews. I am also submitting notebook that I used to reach to the result. These books are run on 1000,50000 and 300000 reviews.

### Results and Conclusion



```
I have used 4 classifiers:
1. Naive Bayes
   It worked well in all the 3 scenario(when reviews: 1000,50000,300000). It classified postive (88%) and neutral (40%) classes very well. But din't work well for negtive classes.

                precision    recall  f1-score   support

    Negative      0.08      0.01      0.02       380
    Neutral       0.40      0.46      0.42      2374
    Positive      0.88      0.88      0.88     12246

2. Random Forest
   This algorithm worked very well in all scenarios (when reviews: 1000,50000,300000). 

   				precision   recall  f1-score   support

    Negative      0.83      0.05      0.10       380
    Neutral       0.58      0.14      0.23      2374
    Positive      0.83      0.98      0.90     12246

3. Knn 
   This algorithm performed well when considering more than 50000 but less than 300000 reviews. 

4. SVM
   This algorithm performed worst out of all above.

Conclusion:
   Random forest did well in all scenarios compared to all above algorithms.

```

## Authors

* **Vinit Singh** 


## Acknowledgments

* Thanks Prof. Sithu Aung for all your guidance.


