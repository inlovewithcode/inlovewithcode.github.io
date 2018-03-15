---
author: guidedmissile
comments: false
date: 2016-08-05 06:07:26+00:00
layout: page
link: https://inlovewithcode.wordpress.com/data-science-notes2/
slug: data-science-notes2
title: data science notes2
wordpress_id: 1321
---

# Feature selection




## **Pearson Coefficient:**


Measures linear correlation between two variables. The resulting value lies in [-1;1], with -1 meaning perfect negative correlation (as one variable increases, the other decreases), +1 meaning perfect positive correlation and 0 meaning no linear correlation between the two variables.






<table cellpadding="0" cellspacing="0" border="0" >
<tbody >
<tr >

<td class="code" >




    
    <code class="python keyword">import</code> <code class="python plain">numpy as np</code>
    
    <code class="python keyword">from</code> <code class="python plain">scipy.stats </code><code class="python keyword">import</code> <code class="python plain">pearsonr</code>
    
    <code class="python plain">np.random.seed(</code><code class="python value">0</code><code class="python plain">)</code>
    
    <code class="python plain">size </code><code class="python keyword">=</code> <code class="python value">300</code>
    
    <code class="python plain">x </code><code class="python keyword">=</code> <code class="python plain">np.random.normal(</code><code class="python value">0</code><code class="python plain">, </code><code class="python value">1</code><code class="python plain">, size)</code>
    
    <code class="python functions">print</code> <code class="python string">"Lower noise"</code><code class="python plain">, pearsonr(x, x </code><code class="python keyword">+</code> <code class="python plain">np.random.normal(</code><code class="python value">0</code><code class="python plain">, </code><code class="python value">1</code><code class="python plain">, size))</code>
    
    <code class="python functions">print</code> <code class="python string">"Higher noise"</code><code class="python plain">, pearsonr(x, x </code><code class="python keyword">+</code> <code class="python plain">np.random.normal(</code><code class="python value">0</code><code class="python plain">, </code><code class="python value">10</code><code class="python plain">, size))</code>




</td>
</tr>
</tbody>
</table>








<blockquote>`Lower noise (0.71824836862138386, 7.3240173129992273e-49)
Higher noise (0.057964292079338148, 0.31700993885324746)`</blockquote>




Sklearn: http://scikit-learn.org/stable/modules/generated/sklearn.pipeline.Pipeline.html

Use sklearn, pipeline to get the job faster.

Major Drawback of Pearson correlation as a feature ranking mechanism is that it is **only sensitive to a linear relationship**. If the relation is non-linear, Pearson correlation can be close to zero even if there is a 1-1 correspondence between the two variables.
For example, a correlation between x and x2 is zero or when x is centered on 0.






<table cellpadding="0" cellspacing="0" border="0" >
<tbody >
<tr >

<td class="code" >





`x ``=` `np.random.uniform(``-``1``, ``1``, ``100000``)`




`print` `pearsonr(x, x``*``*``2``)[``0``]`




</td>
</tr>
</tbody>
</table>








<blockquote>`
-0.00230804707612`</blockquote>




**Pearson Correlation Chart**

https://upload.wikimedia.org/wikipedia/commons/thumb/d/d4/Correlation_examples2.svg/506px-Correlation_examples2.svg.png





Source: [http://blog.datadive.net/selecting-good-features-part-i-univariate-selection/](http://blog.datadive.net/selecting-good-features-part-i-univariate-selection/)




