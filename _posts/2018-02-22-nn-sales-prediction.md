---
layout: single
title: "Using Neural Networks to predict sales"
permalink: neural-networks
date: 2018-02-22
tags: [machine learning, neural networks, deep learning, python]
---

> This posts discusses my team's approach to the second week's challenge in the Bletchley Artificial Intelligence Bootcamp at Erasmus University Rotterdam. I will specifically discuss feature engineering and tweaking of the model, instead of discussing the data in detail. Aditionally I will not discuss all package importations etc. in order to compute this model. 

### The Challenge
Based on historical data, this challenge requires the participants to predict sales for different departments across 45 Wallmart stores, on a weekly basis. In order to make a significant contribution to the challenge, a linear neural network has to be used.


### Feature engineering
Before computing and training our model, we have to look at the distribution of our data. In a python dataframe this can be simply be done with the following command. The pandas dataframe used for this model is named "df".

```   
df.describe()
```

In this data it could easily be seen that not all features are distributed around the same mean, and standard deviations vary significantly. When using the raw data in a regression neural network, results will be disappoint. This problem can however very easily be solved. Simply apply feature scaling.

The following formula should be used in python:

```
df['feature1'] = np.where(df['feature1'] == 999,df[df['feature1'] < 999]['feature1'].mean(),df['feature1'])
```

### The model
After succesfully processing the data, we can start computing the model. 

Our team has chosen the following model:
```
model = Sequential()
model.add(Dense(65, activation='relu', input_dim=135))
model.add(Dense(32, activation='relu'))
model.add(Dense(1))
adam=optimizers.Adam(lr=0.15, beta_1=0.9, beta_2=0.999, epsilon=None, decay=0.0, amsgrad=False)
model.compile(optimizer=adam, loss='mae')
```

The abovementioned model is a three layer, sequential neural network. As a rule of the thumb we have chosen to divide the number of input dimensions by two to find the amount of neurons in the first hidden layer. The number of neurons in the first layer is again divided by two, in order to arrive at the number of neurons for the second hidden layer. The number of neurons chosen is highly arbitrary, and therefore the model should be ran a few times to come to a right number. The first and second hidden layers, use the 'relu' activation function, thereby dropping negative values in the intermediate computational process. Note, the final layer of this model uses no activation function. In this model we want to find an absolute value for a number of sales. Say, sales can be 10, 15, or a thousand. We are not solving a classifaction or multiple classification problem here. 

Since we believe sales will be influenced by previous sales, we capture a momentum effect in the model. In practice this means applying an 'adam' optimizers and setting the beta values. 

The learning rate was simply chosen by trail and error, and closely monetoring the results in order to preclude overfitting.

After the model is compiled it can be fit on the data.

```
Sequential_feature_scaled = model.fit(X,y,batch_size=2048,epochs=10)
``` 
This code used 10 epochs, this can easily be scaled upwards, depending on the computing power of your machine. Or even better, execute your code in a cloud environment. Remember to store the model.fit in a variable, this makes it easy to plot the results lateron.

### Results



