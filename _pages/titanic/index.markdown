---
author: guidedmissile
comments: false
date: 2016-05-28 14:00:35+00:00
layout: page
link: https://inlovewithcode.wordpress.com/titanic/
slug: titanic
title: Titanic
wordpress_id: 1024
---

Note: This is also still draft state.



Goal: To learn **Feature Engg** and **other extremely cools techniques** that had been shared on the Kaggle.com.

Note: This Page is (not) a copy paste or replication but a summary of things I have noticed from these Kagglers. Do not assume.



	
  * using Name Title for predicting Age - Master, Mr, Mrs, Miss, Captain, Officer,..

	
  * use of Title, Sex, Pclass for predicting - Age


Tribute to those awesome programmers.

	
  * https://www.kaggle.com/creepykoala/titanic/study-of-tree-and-forest-algorithms/run/237275

	
    * Kaggler : https://www.kaggle.com/creepykoala




	
  * a

	
    * Kaggler:







# Decision Tree Visualisation and Submission

Here you can see how

https://www.kaggle.com/yildirimarda/titanic/titanic-test3/output

https://www.kaggle.io/svf/134152/3c521ead07195a4add31513c96b51631/Rplot001.png

# How to visualise Tree Graphs


<blockquote>>> from IPython.display import Image
>>> dot_data = StringIO()
>>> tree.export_graphviz(clf, out_file=dot_data,
feature_names=iris.feature_names,
class_names=iris.target_names,
filled=True, rounded=True,
special_characters=True)
>>> graph = pydot.graph_from_dot_data(dot_data.getvalue())
>>> Image(graph.create_png())
http://scikit-learn.org/stable/modules/tree.html</blockquote>




# How to check correlation between columns with respect to Survival

    
    <code class="  language-python">train <span class="token operator">=</span> pd<span class="token punctuation">.</span>read_csv<span class="token punctuation">(</span><span class="token string">"../input/train.csv"</span><span class="token punctuation">,</span> dtype<span class="token operator">=</span><span class="token punctuation">{</span><span class="token string">"Age"</span><span class="token punctuation">:</span> np<span class="token punctuation">.</span>float64<span class="token punctuation">}</span><span class="token punctuation">,</span> <span class="token punctuation">)</span>
    
    <span class="token comment"># Replacing missing ages with median</span>
    train<span class="token punctuation">[</span><span class="token string">"Age"</span><span class="token punctuation">]</span><span class="token punctuation">[</span>np<span class="token punctuation">.</span>isnan<span class="token punctuation">(</span>train<span class="token punctuation">[</span><span class="token string">"Age"</span><span class="token punctuation">]</span><span class="token punctuation">)</span><span class="token punctuation">]</span> <span class="token operator">=</span> np<span class="token punctuation">.</span>median<span class="token punctuation">(</span>train<span class="token punctuation">[</span><span class="token string">"Age"</span><span class="token punctuation">]</span><span class="token punctuation">)</span>
    train<span class="token punctuation">[</span><span class="token string">"Survived"</span><span class="token punctuation">]</span><span class="token punctuation">[</span>train<span class="token punctuation">[</span><span class="token string">"Survived"</span><span class="token punctuation">]</span><span class="token operator">==</span><span class="token number">1</span><span class="token punctuation">]</span> <span class="token operator">=</span> <span class="token string">"Survived"</span>
    train<span class="token punctuation">[</span><span class="token string">"Survived"</span><span class="token punctuation">]</span><span class="token punctuation">[</span>train<span class="token punctuation">[</span><span class="token string">"Survived"</span><span class="token punctuation">]</span><span class="token operator">==</span><span class="token number">0</span><span class="token punctuation">]</span> <span class="token operator">=</span> <span class="token string">"Died"</span>
    train<span class="token punctuation">[</span><span class="token string">"ParentsAndChildren"</span><span class="token punctuation">]</span> <span class="token operator">=</span> train<span class="token punctuation">[</span><span class="token string">"Parch"</span><span class="token punctuation">]</span>
    train<span class="token punctuation">[</span><span class="token string">"SiblingsAndSpouses"</span><span class="token punctuation">]</span> <span class="token operator">=</span> train<span class="token punctuation">[</span><span class="token string">"SibSp"</span><span class="token punctuation">]</span>
    
    plt<span class="token punctuation">.</span>figure<span class="token punctuation">(</span><span class="token punctuation">)</span>
    sns<span class="token punctuation">.</span>pairplot<span class="token punctuation">(</span>data<span class="token operator">=</span>train<span class="token punctuation">[</span><span class="token punctuation">[</span><span class="token string">"Fare"</span><span class="token punctuation">,</span><span class="token string">"Survived"</span><span class="token punctuation">,</span><span class="token string">"Age"</span><span class="token punctuation">,</span><span class="token string">"ParentsAndChildren"</span><span class="token punctuation">,</span><span class="token string">"SiblingsAndSpouses"</span><span class="token punctuation">,</span><span class="token string">"Pclass"</span><span class="token punctuation">]</span><span class="token punctuation">]</span><span class="token punctuation">,</span>
                 hue<span class="token operator">=</span><span class="token string">"Survived"</span><span class="token punctuation">,</span> dropna<span class="token operator">=</span><span class="token boolean">True</span><span class="token punctuation">)</span></code>




https://www.kaggle.io/svf/1603/1db145f4c65249a8bc7b7090fb66369b/1_seaborn_pair_plot.png

Source: https://www.kaggle.com/benhamner/titanic/python-seaborn-pairplot-example/output



# How lucky is your name?

Well sometimes, you happend to be of a high authority family and this reason that could save your life.

https://www.kaggle.com/anthonyg/titanic/lucky-names/code



# how to use "is in alist" paramaeter in pandas

    
    <code class=" language-python">#pull out the passengers that have popular names (> 10 occurances)
    
    top10_popular_firstname = dfTitanic['FirstName'].value_counts()[dfTitanic['FirstName'].value_counts() > 10].index
    
    dfPassengersWithPopularNames = dfTitanic[dfTitanic['FirstName'].isin( top10_popular_firstname )]
    </code>




# How to XGboost your solution?

https://www.kaggle.com/cbrogan/titanic/xgboost-example-python/code



Suggestion:

I see there are lots of interesting questions & interesting finding to ask and figure out from data.



	
  * **distplot/hist of features** values play important role.

	
  * sometimes few columns can be **inter-dependent** and we can use that for **guessing missing values.**

	
  * No values can also mean something like a new feature called **no.of_nulls feature**.

	
  * check for **hidden data** in **Object type features**.

	
  * if you see combinaiton of cols can change show some important, then create a new feaure.

	
  * all **new features **not necesarly adds **signification** values.

	
  * too many feaures are good but having feaures which contribute is more important.

	
  * Failures are stepping stone of sucess. Kill logics the relate to failure. Keep trying.

	
  * ASK **WHY** for everything.

	
    * **What & Why these features are good**?

	
    * What story to make up ?

	
    * What more we can cook up ?




	
  * ...









