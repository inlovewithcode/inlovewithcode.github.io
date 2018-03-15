---
author: guidedmissile
comments: true
date: 2016-06-02 19:24:53+00:00
excerpt: short note of a blog article on document classification is possible
layout: post
link: https://inlovewithcode.wordpress.com/2016/06/03/notes-on-document-classification/
slug: notes-on-document-classification
title: Notes on document classification
wordpress_id: 1062
categories:
- DS
tags:
- Classification
- Document
- ML
- Naive Bayesian
- Tokenisation
---

Notes on document classification



One of the main challenge every starter in ML wants to understand how can you do document classification because is a chunk of words but not like an array or a vector or parameters of fixed specific things. Then Answer is



Then Answer is below is



	
  * text-normalisation

	
    * concert words to lower case

	
    * removing punctuations

	
    * stemming: convert words to basic word tokens. For example, convert ‘happiness or happily’ to happy.







This process of splitting docs to bags(groups) of words is called **Tokenisation**.




So once this Tokenisation is done, how to do we do classification of a document ?




If you have done some probability then you might have heard of this theorem and problem statement




A bag consists of ’x' number of green ball, ‘y’ number of red ball and ‘z’ number of blue balls. Naturally x, y,z are non-negative integers and can be zero.




our document classification is also similar to above, where a bag refers to a document and words refer to balls.




Answer is finding the “probability of  “ which category




NB: Naive Bayes - Naive Bayes, why because NB thinks all words are **independent** of one another and tries to give equal way to seeing things. As much as this does not really make sense in the real world, this has lots times made wonders in terms of Statistics and Accuracy Scores.




**Key part in categorisation:**




For spam or not spam, we can define with either 0 or 1 which is simple and great. Now how about finding a document if is class1 or class2 or class3 or class4, a case where we can have more than 2 options.




For such special cases we do like






	
  * calculate the probability for being each of those

	
  * take the highest probability




Example: class of a document is one with which has highest probability of [ (probability of being class1),




  (probability of being class2),




  (probability of being class3),




  (probability of being class4) ]




If you search a bit, I think the first thing you would notice or you might have already heard that Naive Bayesian got a lot of fan following both in terms of good & bad.  Personally, I heard Naive Bayesian is one the wonderful tool in terms of generating good results. Good Luck.





Here is the source. Here this author, did more than just write article of document classification but shared some code in JS. I'm nt really much fan of JS, thanks for wonderful explanation he provided so much and I could understand only a little. A wonderful Learning.



	
  * https://www.burakkanber.com/blog/machine-learning-naive-bayes-1/



