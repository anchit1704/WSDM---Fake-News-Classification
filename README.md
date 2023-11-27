# WSDM-Fake-News-Classification
In this project I design a feature engineering based solution for the WSDM Fake News Classification Challenge on Kaggle.

## Problem Description

Given the title of a fake news article A and the title of a coming news article B, classify B into one of the three categories - 
agreed: B talks about the same fake news as A, disagreed: B refutes the fake news in A, unrelated: B is unrelated to A.

For detailed description visit the competition website link [here](https://www.kaggle.com/competitions/fake-news-pair-classification-challenge).

## Dataset

**train.csv** - training data contains 320,767 news pairs in both Chinese and English. This file provides the only data you can use to finish the task. Using external data is not allowed.

**test.csv** - testing data contains 80,126 news pairs in both Chinese and English. The approximately 25% of the testing data is set to be public and is used to calculate your accuracy shown on the leading board. The remaining 75% private data is used to calculate your final result of the competition.

**sample_submission.csv** - sample answer to the testing data.

Data fields

**id** - the id of each news pair.  
**tid1** - the id of fake news title 1.  
**tid2** - the id of news title 2.  
**title1_zh** - the fake news title 1 in Chinese.  
**title2_zh** - the news title 2 in Chinese.  
**title1_en** - the fake news title 1 in English.  
**title2_en** - the news title 2 in English.  
**label** - indicates the relation between the news pair: agreed/disagreed/unrelated.  

## Solution

I extract several similarity based features between the title1_en(title of a fake news article A) and title2_en(title of a coming news article B) and train the classifier to predict the labels based on these features.

The following features were used - 

1. Count Vector similarity - Find the count vector representation of title1 and title2, and measure the similarity between the two titles.
2. Count of a set of words in title2 and title1. Gives a higher value if a set of words are present in title2 and not in title1.
3. SVD matrix similarity - Cosine similarity and euclidean distance of the svd matrix representation of title1 and title2.
4. Polarity and subjectivity of title1 and title2.
5. Polarity difference and subjectivity difference between title1 and title2.
6. Topic similarity - Cosine similarity and euclidean distance similarity of the topic distribution in title1 and title2 based on a LDA model.
7. Word Mover's distance - WMD between the word2vec representation of title1 and title2.

 These features are fed to various classifiers trained to predict the multiclass labels - agreed, disagreed, and unrelated.

I implement the Logistic Regression, SVM, Random Forest Classifier, XGBoost and Neural Networks and report the results of the best classifier model. 

## Results

10 fold cross validation

| Models | Weighted Accuracy | Weighted Precision | Weighted Recall | Weighted F1 |
| ------------- | ------------- | ------------- | ------------- | ------------- |
| Logistic Regression  | 0.664  | 0.790  | 0.664  | 0.705 |
| Random Forest Classifier | 0.803 | 0.794 | 0.803 | 0.789 |
| XGBoost | 0.806 | 0.799 | 0.806 | 0.795 |
| Neural Networks | 0.801  | 0.790 | 0.801 | 0.789 |
