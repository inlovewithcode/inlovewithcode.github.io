---
author: guidedmissile
comments: false
date: 2016-04-14 17:30:25+00:00
excerpt: short note from my data science  class. cover introduction machine learning,
  types of classification, linear regression, classification, modelling, models, performance
  checking, features modelling, testing, training, bias, variance and some links
layout: page
link: https://inlovewithcode.wordpress.com/data-analaysis/datascience01/
slug: datascience01
title: datascience01 notes
wordpress_id: 989
---

hei, there might some spell issues and other bug please excuse, I will try to put more details. please provide comments/suggestion here. thank you.





# Table of contents








	
  * Table of contents

	
  * Keywords

	
  * Introduction

	
    * Some ways we can classify our models

	
      * Based on feedback

	
      * Based on Model type




	
    * Regression or Classification

	
    * linear regression

	
    * logistic regression

	
    * how does these model work in sklearn

	
      * General Steps




	
    * Test-Train Data

	
      * Development Steps




	
    * performance checking

	
      * root mean square error

	
      * K-fold







	
  * Models

	
    * overfitting and underfitting

	
    * bias and variance




	
  * features selection and engineering

	
    * feature engineering








This is notes I collected from a ML Session I attended


# Keywords





	
  * essemblers

	
  * theta

	
  * learning rate

	
  * gradient decesnt

	
  * data model or classifier or regressor




# Introduction


Machine Learning can be simply described by 3 variables. Task, Experience & Performance.

    
    <code> TASK         | Describle/decide what goal is required.
     EXPERIENCE   | Training your data model
     PERFORMANCE  | How good is your solution?
    </code>




## Some ways we can classify our models




### Based on feedback





	
  * Supervised: We know how answers/solution sets looks like. Mail is spam or not.

	
  * Un-supervised: From start we don’t know what to classify it and we need to classify.

	
  * Reinforced Learning: Solution set we know may change in future.




### Based on Model type





	
  * Discriminative: Simple model, starts from zero and start generate a model to predict

	
  * Generative: Model which uses Discriminative models and start understanding how answers are distributed. Here we take some random guess of our model(coeff) and start adjusting till we get better results.

	
  * [https://en.wikipedia.org/wiki/Generative_model](https://en.wikipedia.org/wiki/Generative_model)

	
  * [https://en.wikipedia.org/wiki/Discriminative_model](https://en.wikipedia.org/wiki/Discriminative_model)




## Regression or Classification


World is full of challenging problem and interesting answers. No doubt but we don’t want to tackle all those here rt now. We generally focus on two of problem statement, one is classification and other is continuous distribution type.

Like you can understand classification is about categorising if a particular document belongs to a group or a author or say a mail from xyz.com is spam or not,.. so on.

Regression problem generally include a continue distribution function. For example say, you wrote a wonderful articles or created dub smash video which is going viral. Now you want to understand how many more and people are going to search for that video so that you can pull the traffic into your site.


## linear regression


we are going to apply a machine learn code on data we have, thus creating a data model. Here this model is nothing but a linear model,. i.e. **y = mx +c** but with some extra dimension or variable or features included.

**y = a1 * x1 + a2 * x2 + a3 * x3 + c**

Simple. Fast. Hassle Free. My Fav. All other machines fav too.


## logistic regression


Imagine there is a special function simmilar to round function which we are very familar with and we a machine to figure it our all by itself. All the sytem has to do is figure it out where

    
    <code>In [12]: round(0.445, 0)
    Out[12]: 0.0
    
    In [13]: round(0.455, 0)
    Out[13]: 0.0
    
    In [14]: round(0.555, 0)
    Out[14]: 1.0
    
    In [15]: round(0.655, 0)
    Out[15]: 1.0
    
    In [16]: round(0.255, 0)
    Out[16]: 0.0
    
    In [17]: round(0.155, 0)
    Out[17]: 0.0
    
    In [18]: round(0.055, 0)
    Out[18]: 0.0
    </code>


train_data = [ 0.445, 0.455, 0.555, 0.655, 0.255 ]

target_data = [0.0, 0.0, 1.0, 1.0, 0.0, 0.0, 0.0]

test_data = [ 0.155, 0.755 ]

for this our prediction should come as [ 0.0, 1.0 ]

As you can see, in this problem our input is all with in 0.0 till 1.0 and output is also with in same bound. Our goal is let machine find where is the cut off edge.


## how does these model work in sklearn




### General Steps





	
  * step1: select & import a model from models available from sklearn libs

	
  * step2: initiate a new model( create a instance of it )

	
  * step3: fit the data into that model

	
  * step4: predict the solution




## Test-Train Data





	
  * test data

	
  * train data

	
  * target data/ labels data




### Development Steps





	
  * step1: select & import a model from models available from sklearn libs

	
  * step2: initiate a new model ( create a instance of it )

	
    * step2.1: split our main training data into sets

	
    * step2.2: take one set for testing and another for training.

	
      * Generally split is done in 90 : 10 % or 80 : 20 % ratios

	
      * Small set is for testing and larger for training.







	
  * step3: fit the data into that model

	
    * fit only our training data (80%) of data




	
  * step4: predict the solution

	
    * here test only our testing data for which we know answers.





**Almost all sklearn models follow following structure**

from sklearn.marvel_comics import superman

clf = superman()

clf.fit( test-data, target-data)

predicted_data = clf.predict(test-data)


## performance checking


Performance Checking. Some thing simmilar to checking our own code. Frankly speaking this is something I really dont like :) Sadly, as a sr. developer this is no option for me but to like and love it to do. Luckily, sklearn has all the tool required for checking. ( thank you for letting to be still lazy :)

K-fold, GridCv, RandomisedCV checking are few generic techniques which can help to do most of the stuff like split data into test, train sets and then train mode and calculate the scores.


### root mean square error


say y is actual data and y-pred is the data predicted, then average sum of squares of error generated between y and y-pred.



	
  * squaring takes care of counting postive errors and negitive error

	
  * squaring make sure total error starts making too much noise and we start moving away from solution and decreases as we close to our answer. Excellent alaram.


say error is -4.0, then rms value will be 16.

say error is -3.0 then rms value will be 9.

say error is 0.1 then rms value will be 0.01.

say error is 0.9 then rms value will be 0.81.

**Note: Lower the rms/error rate means the better the model is.**


### K-fold, CrossValidation, GridSearch





	
  * randomise the test data and splits into multiple into test and train datasets

	
  * trains the model for a data and tests it according

	
  * provide score for each of these sets


Generally data sets consists of some noise, which is natural is real world and its difficlut to predict and filter. Training on randomised set helps to know that we are n0t relying that noise to predict data and our model is good.

[http://scikit-learn.org/stable/modules/cross_validation.html](http://scikit-learn.org/stable/modules/cross_validation.html)


# Models





	
  * linear regression

	
  * logistic regression

	
  * random forest




## overfitting and underfitting




## bias and variance


**find and uses test & train scores to know if your Model is caught in bias/variance issues.**


# features selection and engineering





	
  * understand variance based feature selection

	
  * random forest feature selection

	
  * [http://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.OneHotEncoder.html](http://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.OneHotEncoder.html)

	
  * analysis of features, why features are working good or bad




## feature engineering





	
  * null values based creation of columns

	
  * generated data based on best features behaviour




<blockquote>Written by [Sam](https://inlovewithcode.wordpress.com/).</blockquote>
