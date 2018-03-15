---
author: guidedmissile
comments: false
date: 2017-03-30 12:24:41+00:00
layout: page
link: https://inlovewithcode.wordpress.com/data-analaysis/precision-and-recall/
slug: precision-and-recall
title: Precision and Recall
wordpress_id: 1837
---

## Introduction



For every ML models, when go back and check how well they do then especially for classification problems we encounter the following matrix.

A matrix that shows how well the ML model is classifying categories. Here is a Binary classification matrix for predicting say spam emails.





  * True ==> Spam Email


  * False ==> Not a spam



We call this matrix "Prediction Success" Matrix, in scientific terms "Confusion Matrix".

[code lang=text]
             |---------------------|
             |     Actual Values   |
|------------|---------------------|
|            |   |   +     |  -    |
| Predicted  | + |  tp     | fp(I) |
|    values  | - |  fn(II) | tn    |
|------------|---------------------|
[/code]



  * tp: truly(correctly) predicted as positives


  * tf: truly(correctly) predicted as false


  * fp: falsely predicted as positives


  * fn: falsely predicted as negatives





## Null Hypothesis/Type I & Type II Errors



In terms of Null Hypothesis, we can two of these error as Type I & Type II





  1. Type I error(Greek letter α):



    * Reject the Hypothesis w.r.t data




  2. Type II erorr(Greek letter β):



    * Failed to reject Hypotheseis(which is not same as accepting)







## Precision & Recall Formulas



[code lang=text]
Precision = 1 / (1 + (fp / tp))

Recall = 1 / (1 + (fn / tp))

Accuracy = tp + fn / ( tp + tn + fp + fn)
[/code]

**Example: Brain surgery provides an illustrative example of the tradeoff.**
(from wikipedia, reformatted)

Consider a brain surgeon tasked with removing a cancerous tumor from a patient’s brain.  The surgeon needs to remove all of the tumor cells since any remaining cancer cells will regenerate the tumor. Conversely, the surgeon must not remove healthy brain cells since that would leave the patient with impaired brain function.

Case 1: The surgeon may be **more liberal** in the area of the brain she removes to ensure she has extracted all the cancer cells. This decision **increases recall** but reduces precision.

Case 2: On the other hand, the surgeon may be **more conservative** in the brain she removes to ensure she extracts only cancer cells. This decision **increases precision** but reduces recall.

That is to say, greater recall increases the chances of removing healthy cells (negative outcome) and increases the chances of removing all cancer cells (positive outcome). Greater precision decreases the chances of removing healthy cells (positive outcome) but also decreases the chances of removing all cancer cells (negative outcome).

https://www.youtube.com/watch?v=2f-J5yWQpAQ
