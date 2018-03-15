---
author: guidedmissile
comments: true
date: 2015-07-15 12:51:08+00:00
layout: page
link: https://inlovewithcode.wordpress.com/matplotlib/
slug: matplotlib
title: Matplotlib
wordpress_id: 559
---

[![matplot_hist_scatter_box_plot](http://inlovewithcode.files.wordpress.com/2015/07/matplot_hist_scatter_box_plot.jpg)](http://inlovewithcode.files.wordpress.com/2015/07/matplot_hist_scatter_box_plot.jpg)



### Examples



[code lang=text]
# choosing line with & color & label
plt.plot(X, Y, color="red", linewidth=2.5, linestyle="-", label="sine")

# choosing color and intensity
plt.plot (X, Y, color='blue', alpha=1.00)

# set legend loction & remove outer frame
plt.legend(loc='upper left', frameon=False)

# setting tics for an axis
plt.yticks([-1, 0, +1])

# intutive ticks for a axis
# note: we are setting limits not ticks**
plt.xlim(X.min()*1.1, X.max()*1.1)

# setting plot size and back-ground color
fig = plt.figure(figsize=(6,6), facecolor='white')
[/code]



### plt.figure attributes



<table border="1" class="docutils" > 

<tr >
Argument
Default
Description
</tr>

<tbody valign="top" >
<tr >

<td >num
</td>

<td >1
</td>

<td >number of figure
</td>
</tr>
<tr >

<td >figsize
</td>

<td >figure.figsize
</td>

<td >figure size in in inches (width, height)
</td>
</tr>
<tr >

<td >dpi
</td>

<td >figure.dpi
</td>

<td >resolution in dots per inch
</td>
</tr>
<tr >

<td >facecolor
</td>

<td >figure.facecolor
</td>

<td >color of the drawing background
</td>
</tr>
<tr >

<td >edgecolor
</td>

<td >figure.edgecolor
</td>

<td >color of edge around the drawing background
</td>
</tr>
<tr >

<td >frameon
</td>

<td >True
</td>

<td >draw figure frame or not
</td>
</tr>
</tbody>
</table>

Reference for





  * [Bar plots, Polar, Counter, World Map, Colored Scatter Plots](http://www.labri.fr/perso/nrougier/teaching/matplotlib/)



  * [matplot symbols, line colors, & other](http://www.labri.fr/perso/nrougier/teaching/matplotlib/#quick-references)



