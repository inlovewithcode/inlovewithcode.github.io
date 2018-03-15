---
author: guidedmissile
comments: false
date: 2016-08-23 03:18:01+00:00
layout: page
link: https://inlovewithcode.wordpress.com/zero-to-pro-tips/
published: false
slug: zero-to-pro-tips
title: Zero to Pro Tips
wordpress_id: 1357
---

Here is a diagram of the Predictive Modelling Process, obtained from [this link](http://www.nextbit.it/classification.php), just for your reference:
[![classification01.jpg](https://udacity-github-sync-content.s3.amazonaws.com/_imgs/8650/1463482120/classification01.jpg)](https://udacity-github-sync-content.s3.amazonaws.com/_imgs/8650/1463482120/classification01.jpg)





**Data Set Imbalance**:



	
  * A very peculiar characteristic of this dataset is that it’s labels are quite unbalanced.

	
  * This means that the number of positive training examples is much more than the number of negative training examples, or the number of students who passed is much more than the number of students who failed.

	
  * It’s for this reason that an [F1 score](https://en.wikipedia.org/wiki/F1_score) is chosen as the default evaluation metric rather than an accuracy score.

	
  * Please note that one could also use [precision or recall](https://en.wikipedia.org/wiki/Precision_and_recall) as the evaluation metric for this classification problem.





### Suggestions and Comments:


When writing code in iPython notebook, please remember to make sure you define a function/variable/object before using it. If not, when someone runs the cells one by one from the top, they might encounter a mistake, because the you defined the function to run the code in the cell below instead of above the said cell.


### Pro Tips:





	
  * Mastering Markdown formatting is extremely useful if you want to produce Quality Reports in iPython Notebook.

	
  * Please check out [this link](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) if you want to learn more about Markdown formatting.





### Pro Tips:




#### STRATIFIED SHUFFLE SPLIT:





	
  * You may also consider making use of Stratified Shuffle Split since we have an unbalanced dataset. Please look at [here](http://scikit-learn.org/stable/modules/generated/sklearn.cross_validation.StratifiedShuffleSplit.html) and [here](http://stats.stackexchange.com/questions/117643/why-use-stratified-cross-validation-why-does-this-not-damage-variance-related-b) for more information.




#### SEEDING YOUR ALGORITHMS:





	
  * In order to remove randomness of your algorithms, and to make sure your results don’t differ at each run, please consider to always use a [random seed](https://en.wikipedia.org/wiki/Random_seed) to seed your algorithms.

	
  * A standard practice I’ve come across is to define a random seed as a global variable in your work, and to use it throughout all the algorithms/methods which require random number generation (splitting data, decision tree initialisation, neural network weight initialisation etc).

	
  * In sklearn, as far as I know, random seeds are provided to methods and functions using the parameter `random_state`. Please seed all of your algorithms in the future if you haven’t been doing so yet





### Random Forest:




#### SUGGESTED READING





	
  * If you wanna go deeper with Random Forests, check these out:

	
    * [http://rstudio-pubs-static.s3.amazonaws.com/4239_fcb292ade17648b097a9806fbe026e74.html](http://rstudio-pubs-static.s3.amazonaws.com/4239_fcb292ade17648b097a9806fbe026e74.html)







### SVM:




#### SUGGESTED READING





	
  * If you wanna go deeper with SVMs, check these out:

	
    * [http://scikit-learn.org/stable/modules/svm.html](http://scikit-learn.org/stable/modules/svm.html)

	
    * [https://www.researchgate.net/post/What_is_the_running_time_complexity_of_SVM_and_ANN](https://www.researchgate.net/post/What_is_the_running_time_complexity_of_SVM_and_ANN)

	
    * [http://cs229.stanford.edu/notes/cs229-notes3.pdf](http://cs229.stanford.edu/notes/cs229-notes3.pdf)





SVMs are indeed a fantastic choice for this problem, nice job giving info about them!


### Naive Bayes




#### SUGGESTED READING





	
  * These links below might be helpful if you want to learn more about Naive Bayes:

	
    * [http://www.inf.ed.ac.uk/teaching/courses/iaml/slides/naive-2x2.pdf](http://www.inf.ed.ac.uk/teaching/courses/iaml/slides/naive-2x2.pdf)

	
    * [http://scikit-learn.org/stable/modules/naive_bayes.html](http://scikit-learn.org/stable/modules/naive_bayes.html)

	
    * [http://www.research.ibm.com/people/r/rish/papers/RC22230.pdf](http://www.research.ibm.com/people/r/rish/papers/RC22230.pdf)








### Pro Tips:





	
  * Nice job using F1 (harmonic mean of precision and recall) to evaluate your algorithms results.

	
  * One of the advantages of using precision and recall rather than [F1 score](http://scikit-learn.org/stable/modules/generated/sklearn.metrics.f1_score.html) is ease of interpretability.

	
  * For example, for this particular problem, [precision](http://scikit-learn.org/stable/modules/generated/sklearn.metrics.precision_score.html#sklearn.metrics.precision_score) can be interpreted as the number of students who really need intervention out of those picked by the model for intervention.

	
  * While [recall](http://scikit-learn.org/stable/modules/generated/sklearn.metrics.recall_score.html) is the number of students identified for intervention by the model out of those who really need intervention







#### LAYMEN'S TERMS EXAMPLES:





	
  * Check out this excellent description of the [adaboost algorithm](https://www.quora.com/What-is-AdaBoost) for an idea of what will be the ideal layman's description of SVMs.
This one might also help:
[https://www.reddit.com/r/MachineLearning/comments/15zrpp/please_explain_support_vector_machines_svm_like_i/](https://www.reddit.com/r/MachineLearning/comments/15zrpp/please_explain_support_vector_machines_svm_like_i/)







































**Using Stratified Shuffle Split**:



	
  * As mentioned in the section about dataset exploring the data, the dataset is quite unbalanced.

	
  * To better model unbalanced data, it’s always preferable to use a stratified shuffle split.

	
  * This is because using Stratified shuffle split, the dataset is split so as to **preserve the percentage of samples for each class.**

	
  * This method avoids not having a single representative of the minor class in a fold.

	
  * Also, given a small data with highly unbalanced classes, stratification provides a safeguard and more consistency among the classes in the two splits.

	
  * This paper gives more information on stratified cross-validation. In the paper, it is stated that the main advantage of this procedure is that it reduces experimental variance, which makes it easier to identify the best methods under consideration (hyper-parameters)

	
  * Below is a short implementation of StratifiedShuffleSplit from sklearn, using adaboost as the classifier. Note that you could also use other algorithms such as SVMs or Decision Trees to conduct grid search using stratified shuffle split.



    
    <code><span class="hljs-comment"># Import StratifiedShuffleSplit from sklearn</span>
    <span class="hljs-keyword">from</span> sklearn.cross_validation <span class="hljs-keyword">import</span> StratifiedShuffleSplit
    <span class="hljs-keyword">from</span> sklearn.grid_search <span class="hljs-keyword">import</span> GridSearchCV
    <span class="hljs-keyword">from</span> sklearn.metrics <span class="hljs-keyword">import</span> make_scorer
    
    <span class="hljs-comment"># Define a random state to seed your algorithms</span>
    ran_state = <span class="hljs-number">201</span>
    
    <span class="hljs-comment"># Define your classifier to optimise. You can choose to optimise classifiers</span>
    <span class="hljs-comment"># other than adaboost.</span>
    clf = AdaBoostClassifier(random_state=ran_state)
    
    <span class="hljs-comment"># Create the parameters list you wish to tune</span>
    parameters = {<span class="hljs-string">'n_estimators'</span> : [<span class="hljs-number">5</span>, <span class="hljs-number">10</span>, <span class="hljs-number">15</span>, <span class="hljs-number">20</span>],
                  <span class="hljs-comment">#'algorithm'    : ['SAMME', 'SAMME.R'],</span>
                  <span class="hljs-string">'learning_rate'</span>: [<span class="hljs-number">0.01</span>, <span class="hljs-number">0.50</span>, <span class="hljs-number">0.60</span>, <span class="hljs-number">0.70</span>]}
    
    <span class="hljs-comment"># Create the Stratified Shuffle Split object</span>
    sss = StratifiedShuffleSplit(y_train, n_iter=<span class="hljs-number">10</span>, test_size=<span class="hljs-number">0.24</span>, random_state=ran_state)
    
    <span class="hljs-comment"># Make an f1 scoring function using 'make_scorer'</span>
    f1_scorer = make_scorer(f1_score, pos_label=<span class="hljs-string">"yes"</span>)
    
    <span class="hljs-comment"># Create a grid search object, and use the sss object in place of cv parameter</span>
    grid_obj = GridSearchCV(clf, param_grid=parameters, scoring=f1_scorer,
                           cv=sss)
    
    <span class="hljs-comment"># Fit the grid search object to the training data and find the optimal parameters</span>
    grid_obj.fit(X_train, y_train)
    
    <span class="hljs-comment"># Get the estimator</span>
    clf = grid_obj.best_estimator_
    
    <span class="hljs-comment"># Print the parameters</span>
    <span class="hljs-keyword">print</span> clf.get_params(), <span class="hljs-string">'\n'</span>
    
    <span class="hljs-comment"># Report the final F1 score for training and testing after parameter tuning</span>
    <span class="hljs-keyword">print</span> <span class="hljs-string">"Tuned model has a training F1 score of {:.4f}."</span>.format(predict_labels(clf, X_train, y_train))
    <span class="hljs-keyword">print</span> <span class="hljs-string">"Tuned model has a testing F1 score of {:.4f}."</span>.format(predict_labels(clf, X_test, y_test))
    </code>





































### 




### StratifiedSplit with GridSearch:


Although we expect the tuned model to perform better, you may observe that the tuned model can give worse result than untuned one if you run the code with different random splits. This is largely due to the small and unbalanced dataset, and you can use techniques like StratifiedShuffleSplit to ensure that the ratio of the two classes are well maintained. For example:

    
    <code>from sklearn.cross_validation import StratifiedShuffleSplit
    ...
    ssscv = StratifiedShuffleSplit( <span class="hljs-keyword">y_t</span>rain, n_iter=<span class="hljs-number">10</span>, test_size=<span class="hljs-number">0.1</span>)
    grid = GridSearchCV(clf, parameters, cv = ssscv , scoring=f1_scorer) 
    grid.fit( X<span class="hljs-keyword">_t</span>rain, <span class="hljs-keyword">y_t</span>rain ) 
    ...</code>







### 




### F1 Score:






The F1 score assigns equal weighting to precision and recall. In some cases (not required for this project), you may favor one over another, and you may use the generic F-beta score instead:

    
    <code>f1_scorer = make_scorer(fbeta_score, beta=<span class="hljs-number">1</span>, pos_label= <span class="hljs-string">"yes"</span>)
    </code>


The beta parameter determines the weight of precision in the combined score:



	
  * beta = 1; equal weight to precision and recall, equivalent to F1 score

	
  * beta < 1 lends more weight to precision;

	
  * beta > 1 favors recall


Ref: [http://scikit-learn.org/stable/modules/generated/sklearn.metrics.fbeta_score.html](http://scikit-learn.org/stable/modules/generated/sklearn.metrics.fbeta_score.html)









### Pro Tips:


Writing Clean code is very important and is an integral part of being a Machine Learning Engineer. If you wish to master the art of writing clean code in Python, you may want to check out the [Google Python Style Guide](https://google.github.io/styleguide/pyguide.html).
You don’t have to read all the guide at once; you can choose to read only the parts relevant to you at the moment.









**Tip: Scalability, developing a proactive attitude**
An interesting question you might address to further improve your answer, and show some business-oriented proactivity by anticipating the customer’s needs, regards the scalability of your chosen algorithm: What would happen if you had to classify thousands or hundreds of thousands of students? What would happen with training time and with prediction time? Would you still choose the same algorithm? (Please note that this is relevant as not every algorithm scales linearly, some might scale exponentially, which means that the computational costs might grow exponentially with size. This is not an issue as for now but it would be if we were considering a much bigger number of students).
[https://github.com/jeff1evesque/machine-learning/wiki/Algorithm:-Big-O-Notation](https://github.com/jeff1evesque/machine-learning/wiki/Algorithm:-Big-O-Notation)






















