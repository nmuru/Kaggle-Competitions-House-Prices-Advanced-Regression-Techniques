# Kaggle-Competitions-House-Prices-Advanced-Regression-Techniques

This is an Ongoing Knowledge Competition with rolling leaderboard hosted by Kaggle for beginners

Most of the high scoring notebooks focused on python libraries like XGBoost Regressors. I have proved that a simple deep learning neural network can perform equally or better than XGBoost for this advanced regression problem. 

My notebook could achieve a reproducible kaggle accuracy of 0.119x. Uses stacking and blending that includes a deep learning model. This keeps the notebook at 116/4582 - within top 3% of all submitted notebooks

Introduction

Notebook - Ames_Housing_Stacking_with_DeepLearning_Top3.5%

This notebook is a continuation of my previous kaggle notebook - https://www.kaggle.com/code/murugesann/ames-housingprices-deep-learning-model-top-4 where I have explained the model in depth. That notebook could achieve an accuracy of top 4.5% with Kaggle score of 0.11946 (submission - nm-dl-final9.csv) without stacking and blending
Objective of this notebook is find the effect and role of randomness vis-a-vis stacking and blending. How much does stacking improves the accuracy, over and above the previous notebook's 0.11946?
In my previous notebook above, I had noted, based on several trials and experimentations, that the accuracies of machine learning models depends on not only the content of input data but also order of columns. However, by using python hashseed and random state, we can very well reproduce any result in any computer. But if we change the random state (row order) or the order of columns (column order), the accuracies will change. These accuracies have been found to vary leading to Kaggle scores of 0.10 to 0.13. It is a pure random luck whether you get a kaggle score of 0.10 or 0.13 - it depends on random state and the column tranformation order!
But how relevant is above kind of accuracy of 0.10 or 0.13 for the real world production dataset? Can we say that the confidence level, with which the sales prices are predicted, will be same BOTH for the model with accruacy of 0.10 and model with accuracy of 0.13?
Also, with respect to the methodology of stacking, another important question arises: Given the well established fact that Stacking improves accuracy, How relevant is any improvement through stacking given the fact that I can achieve the maximum score of, say, 0.11 even without stacking?
Does stacking does nothing more than solve the above "random luck phenomenon" by allowing multiple random states to work together through several models, thereby improving accuracy? -
OR How relevant is the accuracy of 0.11 achieved by 'random luck' vs 0.11 achieved through a stable stacking procedure? Does both the models can be used with same confidence level?
How confident we can be that our Kaggle score will still be valid for a Ames dataset (2006-2010) of subequent period say 2010-2015 assuming that factors that affect the prices remain same?
Model Results
XGBoost Cross Validation - Average - 11.15%, Minimum - 10.35% and Kaggle Score for Minimum - 12.35%
Deep Learning Model Cross Validation - Average - 11.16%, Minimum - 10.2%
SKlearn Stacking Regressor (without Deep learning Model) - Kaggle Score - 12.02%
MLXtend StackingCV Regressor (Without Deep Learning Model) - Kaggle Score - 11.96%
MLXtend StackingCV Regressor (With deep learning model) - Kaggle Score - 11.98%
Stacking and Blending along with Deep Learning Model - Kaggle Score - 11.95%
An important observation with respect to Stacking as a methodology - As like cross validation of any machine learning model, the cross validation of stacked regression also gives a wide range of 10% to 11x% implying that the accuracy gained through stacking is minimal and that it is also dependent on random state and input data order

Conclusions & Insights
The cross validation accuracies for XGBoost and Deep Learning are nearly same. The range of accuracies obtained in cross validation are the examples of the range we may get on accuracies depending on random state or order of input data etc

The accuracies obtained through Stacking is higher than the accuracy obtained for basic model without stacking, a given random state.

The accuracy obtained through stacking is still within the range of cross validation scores of basic model. This means a better basic model (depending on random state) can achieve higher accuracy than stacked model

Best accuracy obtainable will be when the model is stacked with a random state / hashseed that gives lowest accuracy. For example, the best accuracy possible is near 10% as per cross validation scores. We don't know the input data / content oder for that particular cross validated data (though it can be saved and reused). If we use that input data and same random state numbers, and then use stacking, we will get the best possible accuracy.

However, we cannot conclude which of the model should be used in production: whether the model with the lowest accuracy obtained without stacking (11.9) vs model with lowest accuracy obtained with stacking (11.8)?

It may even be that one of the above two models might be overfitting the current kaggle test data and may fail in regularizing the actual production data. In fact, most of the competition models with large number of models stacked together giving high accuracy might be overfitting the given test data

In otherwords, each accuracy of particular random state is equivalent to a particular sample in overall population. That sample may or may not reflect the overall population. The field of statistics helps decide which of the sample / model might work better in production by giving confidence level based on standard error (IN deep learning section, I have mentioned that we don't need to bother about general assumptions behind linear regression like normality, homoskedacity etc. They are however applicable when we want to do inferential statistics

We do all these model design and analyses to get better accuracies, in order to better the data science models. In reality, no housing price can be predicted with any such accuracy, we are fighting here for! The prices are not determined solely by these quantitative factors and several other subjective factors might determine the price which are applicable for individual purchase and the range of prices could be wide. Hence, we can conclude that any of the above models with reasonable accuracy should be fine rather than striving for lowest accuracy which may neither be achievable in real world real estate market nor be applicable for production data
