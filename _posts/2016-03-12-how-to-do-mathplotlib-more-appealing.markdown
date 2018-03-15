---
author: guidedmissile
comments: false
date: 2016-03-12 15:47:12+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2016/03/12/how-to-do-mathplotlib-more-appealing/
slug: how-to-do-mathplotlib-more-appealing
title: how to do mathplotlib more appealing?
wordpress_id: 912
categories:
- Python
tags:
- DS
- ML
---

Check this video - to know how to improve your data visualisation using matplotlib.pyplot

https://www.youtube.com/watch?v=YapH1LPbe4Q



Here are some Matplotlib Instruction/Sample Code, I got from EDX- Python Programming for DS. Check that course for quick work-out on MATPLOTLIB

How to customise x-axis scale to log?

    
    # Basic scatter plot, log scale
     plt.scatter(players_ids, scores)
     plt.xscale('log')


How to add Add axis labels?

    
    # Strings
     xlab = 'players'
     ylab = 'Scores'
     title = 'World Chess Tournament in 2007'
     plt.xlabel(xlab)
     plt.ylabel(ylab)


How to add a Graph title?

    
     plt.title(title)


How to add x-axis labels?

    
    # Add players labels
     <span style="line-height:1.7;">plt.xticks([1, 2, 3],['Sam', 'Alex', '</span><span style="line-height:1.7;">Mac</span><span style="line-height:1.7;">'])</span>


How to display plot?

    
     plt.show()




Here is a complete example on **World Population Code** that I copied from above tutorial that really impressed me.

    
    # Import numpy as np
    import numpy as np
    # Store pop as a numpy array: np_pop
    np_pop = np.array(pop)
    <span style="color:#99cc00;"># Double np_pop ==> <strong>increase size of dots or points</strong>
    np_pop = np_pop * 2</span>



    
    <span style="color:#99cc00;"># Update: set s argument to np_pop
    plt.scatter(gdp_cap, life_exp, s = np_pop)</span>
    # Previous customizations
    plt.xscale('log')
    plt.xlabel('GDP per Capita [in USD]')
    plt.ylabel('Life Expectancy [in years]')
    plt.title('World Development in 2007')
    plt.xticks([1000, 10000, 100000],['1k', '10k', '100k'])
    # Display the plot
    plt.show()




    
    # For different colors points; s - refers to size ; c - color for each point[big-red;med-green;small-black];
    <span style="color:#99cc00;"> plt.scatter(x = gdp_cap,
                 y = life_exp,
                 s = np.array(pop) * 2,
                 c=col, # sample col - ['red','blue','green','yellow',...]
                 alpha=0.8)</span>


Note: len(col) should be equal to len(x) ==> **each point specify your colour.** My recommendation would be like take a max function over y.

    
    <span style="color:#99cc00;">def sams_points_color_recommendatiaon_engine(x,y):
        y_max = max(y)
        y_min = min(y)
        # setting a bar at 1/3 & 2/3 in y - spread
        y_avg1 = y_min + (y_max - y_min) * 0.33
        y_avg2 = y_min + (y_max - y_min) * 0.66
        #
        cols = []
        for x, y in zip(x,y):
            if y < y_avg1 : cols.append(‘red’)
            elif y < y_avg2 : cols.append(‘yellow’)
            else: cols.append(‘green’)
        return cols
    </span>




Key Points:



	
  * Add `plt.grid(True)` after the `plt.text()` calls so that gridlines are drawn on the plot



	
  * The strings `xlab` and `ylab` are already set for you. Use these variables to set the label of the x- and y-axis.

	
  * The string `title` is also coded for you. Use it to add a title to the plot.

	
  * After these customizations, finish the script with `plt.show()` to actually display the plot.



	
  * Use `tick_val` and `tick_lab` as inputs to the `xticks()` function to make the the plot more readable.

	
  *  Display the plot with `plt.show()` after you've added the customisations.



	
  * Change the opacity of the bubbles by setting the `alpha `argument to `0.8` inside `plt.scatter()`. Alpha can be set from zero to one, where zero totally transparant, and one is not transparant.



	
  * Add `plt.grid(True)` after the `plt.text()` calls so that gridlines are drawn on the plot.



