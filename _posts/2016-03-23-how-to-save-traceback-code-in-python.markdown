---
author: guidedmissile
comments: false
date: 2016-03-23 08:48:20+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2016/03/23/how-to-save-traceback-code-in-python/
slug: how-to-save-traceback-code-in-python
title: How to save traceback code in Python?
wordpress_id: 957
categories:
- Python
tags:
- Backtrace
- Errors
---

Traceback is the part of the error which generally help you find out where is the root cause of the error.

Here is a piece of code I collected from [LINK](http://stackoverflow.com/questions/36165455/how-to-catch-an-exception-if-its-caused-by-a-specific-function/36172462#36172462), which will throw error in its last step.

    
    <code>import pandas as pd
    import numpy as np
    from sklearn import preprocessing
    from sklearn.neighbors import KNeighborsClassifier
    from sklearn import cross_validation
    
    df = pd.DataFrame(np.random.choice(["a", "b", "c", "d"], (200, 4)))   
    
    for col in df:
        le = preprocessing.LabelEncoder()
        le.fit(df[col])
        df[col] = le.transform(df[col])
    
    value_dict = df[0].value_counts().to_dict()
    
    def custom_distance(point1, point2, value_dict):
        #this is not the actual distance function, just a simplified version for reproducibility
        distance = .0
        for i in range(1, len(point1)+1):
            distance += abs(value_dict[point1[i]] - value_dict[point2[i]])
        return distance
    
    neigh_custom = KNeighborsClassifier(n_neighbors=10, metric=custom_distance, 
                            metric_params = {"value_dict": value_dict})
    
    scores = cross_validation.cross_val_score(neigh_custom, df.ix[:,1:], df.ix[:,0], cv=10)
    
    </code>


How to save this trace back error and analyse it according to it?

    
    <code>
    >>> import traceback
    >>> import sys
    >>> from pprint import pprint
    >>>
    ... 
    ... 
    ... 
    >>> # after execution of normal code
    >>> 
    >>> try:
    ...     scores = cross_validation.cross_val_score(neigh_custom, df.ix[:,1:], df.ix[:,0], cv=10)
    ... except Exception, err:
    ...     exc_type, exc_value, exc_traceback = sys.exc_info()
    ...     sam =  traceback.format_exception(exc_type, exc_value,
    ...                                           exc_traceback)
    ...     if 'PyFuncDistance.__init__' in sam[-3]:
    ...         print 'I knew it'
    ...
    I knew it
    >>>
    >>> # printing error
    >>> err
    KeyError(0.21818613266678455,)
    >>>
    >>> # now I am printing the error code traceback
    >>> pprint(sam)
    ['Traceback (most recent call last):\n',
     '  File "", line 2, in \n',
     '  File "/Users/sampathkumarm/anaconda/lib/python2.7/site-packages/sklearn/cross_validation.py", line 1433, in cross_val_score\n    for train, test in cv)\n',
     '  File "/Users/sampathkumarm/anaconda/lib/python2.7/site-packages/sklearn/externals/joblib/parallel.py", line 804, in __call__\n    while self.dispatch_one_batch(iterator):\n',
     '  File "/Users/sampathkumarm/anaconda/lib/python2.7/site-packages/sklearn/externals/joblib/parallel.py", line 662, in dispatch_one_batch\n    self._dispatch(tasks)\n',
     '  File "/Users/sampathkumarm/anaconda/lib/python2.7/site-packages/sklearn/externals/joblib/parallel.py", line 570, in _dispatch\n    job = ImmediateComputeBatch(batch)\n',
     '  File "/Users/sampathkumarm/anaconda/lib/python2.7/site-packages/sklearn/externals/joblib/parallel.py", line 183, in __init__\n    self.results = batch()\n',
     '  File "/Users/sampathkumarm/anaconda/lib/python2.7/site-packages/sklearn/externals/joblib/parallel.py", line 72, in __call__\n    return [func(*args, **kwargs) for func, args, kwargs in self.items]\n',
     '  File "/Users/sampathkumarm/anaconda/lib/python2.7/site-packages/sklearn/cross_validation.py", line 1531, in _fit_and_score\n    estimator.fit(X_train, y_train, **fit_params)\n',
     '  File "/Users/sampathkumarm/anaconda/lib/python2.7/site-packages/sklearn/neighbors/base.py", line 803, in fit\n    return self._fit(X)\n',
     '  File "/Users/sampathkumarm/anaconda/lib/python2.7/site-packages/sklearn/neighbors/base.py", line 258, in _fit\n    **self.effective_metric_params_)\n',
     '  File "sklearn/neighbors/binary_tree.pxi", line 1059, in sklearn.neighbors.ball_tree.BinaryTree.__init__ (sklearn/neighbors/ball_tree.c:8381)\n',
     '  File "sklearn/neighbors/dist_metrics.pyx", line 262, in sklearn.neighbors.dist_metrics.DistanceMetric.get_metric (sklearn/neighbors/dist_metrics.c:4032)\n',
     '  File "sklearn/neighbors/dist_metrics.pyx", line 1091, in sklearn.neighbors.dist_metrics.PyFuncDistance.__init__ (sklearn/neighbors/dist_metrics.c:10586)\n',
     '  File "", line 5, in custom_distance\n',
     'KeyError: 0.21818613266678455\n']
    </code>
