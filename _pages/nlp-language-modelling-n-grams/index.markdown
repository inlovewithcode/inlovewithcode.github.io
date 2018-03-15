---
author: guidedmissile
comments: false
date: 2017-05-09 11:38:48+00:00
layout: page
link: https://inlovewithcode.wordpress.com/nlp-language-modelling-n-grams/
slug: nlp-language-modelling-n-grams
title: NLP - Language Modelling, N-Grams
wordpress_id: 2223
---

## Videos: Lectures on n-grams and Language Modelling



https://www.youtube.com/playlist?list=PLaRKlIqjjguC-20Glu7XVAXm6Bd6Gs7Qi



## Gist of what details videos host



D. Refaeli11 months ago (edited)
This could get a bit confusing, so I wrote the summary of what I understood from this chapter on LM (Language Modeling) in broad scope:





  1. P(Sentence) = We want to model a probability of a sentence to occur.


  2. Markov - in order to simplify our model, we assume only k (= 0, 1, 2, ... or n) previous words affect the probability of any word


  3. nGram - this leads to Unigram (k=0 previous words), Bigram (k=1 previous word), Trigram (2 previous words), .... nGram models


  4. MLE (maximum likelihood estimator) - We can compute the estimators for the probability from our (training) data


  5. Zero's - But what if in the testing data we encounter a uni/bi/tri/n/gram that didn't exist in the training data? It will zero our probabilities...


  6. Solution: Smoothing - we can use smoothing to fix the zero problem
6.1. Unigram Smoothing - Use the unknown words method for un-encountered unigrams, this requires another held-out/development data
6.2. Bigram/Trigram/N-gram smoothing - the simplistic method is add-1 smoothing, and there's also a variant of it with add-k, or add prior smoothing
6.3. Stupid Back-off: if 0 for trigram - go to bigram, if 0 probability for bigram - go to unigram, etc. Used for very large corpus (i.e. training data)
6.4. Interpolation - instead of backing off, use a linear combination of all the different n-grams (i.e. λ1_P(trigram)+ λ2_P(bigram) +...) For this you need to compute ngrams probabilities on the training data, and the λ's on the held-out/development data.
6.5 Good Turing - an advanced smoothing method
6.6 Absolute Discount - the Good Turing can be simplified to just a discount number; This method can be combined with the Interpolation smoothing
6.7 Kneser-Ney Smoothing - Takes the Absolute Discount combined with the Interpolation method - but instead of using a unigram probability, it uses the continuation probability (i.e. how likely a word is a continuation of any word)
Show less


