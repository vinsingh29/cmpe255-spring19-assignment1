# Assignment 1 - Analysing Yelp Data set

The submission consists of 3 Jupyter files:

1. Assignment1_Completed_10000.ipynb - Findings when data set contains 10000 reviews.

2. Assignment1_Completed_50000.ipynb - Findings when data set contains 50000 reviews.

3. Assignment1_Completed_300000.ipynb - Findings when data set contains 300000 reviews.

4. Assignment1_Final_Notebook.ipynb - Findings when considering reviews only for businesses that are restaurant.

5. README

All the latest learning and analysis is well documented in Assignment1_Final_Notebook.ipynb book for further reference.

## Getting Started

The data set given is in Json format. Data set is comprised of review.json file containing 600000 reviews, the objective of the assignment is to classify the reviews as positive negative and neutral. Along with that predict the required data. 

For this project, I have used 4 classifiers.
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
The data is first uploaded in google drive for access in google colab. Next, converted each review text in lowercase also removed all puntutation.

1.1: To get reviews for business that are restaurant, I first read the business data into business dataframe. 

Business Data Frame: Contains of all the business id that are restaurant.
business_dataframe = df_business[df_business['categories'].str.contains('Restaurants','Restaurant', na=False)]

Next, read the reviews from review data set in to a dataframe. Once data frames are created used below logic to 
merge both data frames based on business id.

#Merging restaurants with review as per business id
df = pd.merge(df_restaurant, df_review, on = 'business_id') 

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

I followed approach of divide and conquer, first I picked up 1000, 3000, 50000, and finally complete dataset to check what amount of data maximum can be supported by google colab.

Given the limit of processing speed I could run my algorithm for maximum 32 lakh reviews. 

I am also submitting notebook that I used to reach to the result. 

### Results and Conclusion



```
I have used 4 classifiers:

1. Naive Bayes
It worked well in all the 3 scenario(when reviews: 1000,50000,300000). 
It classified postive (88%) and neutral (40%) classes very well. 
Classifier doesn't work that well for negative classes.

              precision    recall  f1-score   support

    Negative       0.48      0.17      0.25      4854
     Neutral       0.43      0.58      0.49     29942
    Positive       0.91      0.87      0.89    158490

2. Random Forest
This algorithm worked very well in all scenarios. 

              precision    recall  f1-score   support

    Negative       0.79      0.04      0.08      4854
     Neutral       0.57      0.13      0.21     29942
    Positive       0.84      0.98      0.90    158490

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


