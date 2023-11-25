# WSDM---Fake-News-Classification
This notebook shares my solution for the WSDM Fake News Classification Challenge on Kaggle

## Problem Description

Given the title of a fake news article A and the title of a coming news article B, classify B into one of the three categories - 
agreed: B talks about the same fake news as A, disagreed: B refutes the fake news in A, unrelated: B is unrelated to A.

For detailed description visit the competition website link - https://www.kaggle.com/competitions/fake-news-pair-classification-challenge.

## Dataset

train.csv - training data contains 320,767 news pairs in both Chinese and English. This file provides the only data you can use to finish the task. Using external data is not allowed.
test.csv - testing data contains 80,126 news pairs in both Chinese and English. The approximately 25% of the testing data is set to be public and is used to calculate your accuracy shown on the leading board. The remaining 75% private data is used to calculate your final result of the competition.
sample_submission.csv - sample answer to the testing data.

Data fields
id - the id of each news pair.
tid1 - the id of fake news title 1.
tid2 - the id of news title 2.
title1_zh - the fake news title 1 in Chinese.
title2_zh - the news title 2 in Chinese.
title1_en - the fake news title 1 in English.
title2_en - the news title 2 in English.
label - indicates the relation between the news pair: agreed/disagreed/unrelated.

## Solution

Preprocessing - 

I design the solution based on extracting similarity features between the title1_en(title of a fake news article A) and title2_en(title of a coming news article B) nemely - 
1. Count Vectorizer similarity - Find the count vector representation of title1 and title2, and measure the similarity between the two titles.
2. Count of a set of words in title2 and title1.
3. SVD matrix similarity - Cosine similarity and euclidean distance of the svd matrix representation of title1 and title2.
4. Polarity and subjectivity of title1 and title2.
5. Polarity difference and subjectivity difference between title1 and title2.
6. Topic similarity - Cosine similarity and euclidean distance similarity of the topic representation based on a LDA model.
7. Word Mover's distance - WMD between the word2vec representation of title1 and title2.

For every data point these features are fed to a classifier trained to predict the multiclass labels - agreed, disagreed, and unrelated.

I implement the Logistic Regression, SVM, Random Forest Classifier, XGBoost and Neural Networks and report the results of the best classifier model. 

## Results
