---
layout: single
title: "Conventional Machine Learning models versus Convolutional Neural Networks in a multi-class text classification problem"
permalink: text-mining
date: 2018-04-18
tags: [machine learning, python, text mining]
---

This blog assume's the reader to have prior knowledge in text mining and classification problems.

The importance of accurate text classification algorithms is straightforward, 
however a consensus on which Machine Learning model is superior in text classification settings remains absent. 
This paper aims to determine whether state-of-the art Convolutional Neural Networks (CNN) outperform conventional 
Machine Learning models. A wide range of models is proposed: Naive Bayes, Logistic Regression, Decision Tree, 
Random Forest, XGBoost and Convolutional Neural Networks. In order to identify a superior classification model, 
a comprehensive model evaluation is performed. Effects of different vectorizers, CountVectorizer and tf-idf vectorizer, 
together with balancing the training dataset is analyzed. A simple CNN architecture consisting of 9 layers is assessed, 
as well as a more complex design consisting of 24 layers. Results show that a more complex CNN does not improve results. 
Considering all models, Logistic Regression shows an outperformance when using a CountVectorizer on an unbalanced training 
dataset. Balancing the training data improves recall rates throughout multiple models, however, implementing the tf-idf 
vectorizer fails to raise performance rates. All models are trained and evaluated on a Coursera review dataset consisting of 
107,018 reviews together with ratings ranging on a 1-5 scale.

The full paper can be downloaded [here](https://github.com/Thijsq/MSc-Statistics-and-Machine-Learning-LiU/blob/master/Text%20Mining/Project/732A92-2019-PRA1-thiqu264.pdf).
