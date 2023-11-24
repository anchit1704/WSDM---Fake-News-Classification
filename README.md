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

## Results
