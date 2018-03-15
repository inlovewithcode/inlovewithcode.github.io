---
author: guidedmissile
comments: true
date: 2015-06-22 06:39:32+00:00
layout: page
link: https://inlovewithcode.wordpress.com/pandas/
slug: pandas
title: Pandas
wordpress_id: 398
---

# Pandas



How to creates a dates ranges in Pandas?

How to creates a dates DataFrame in Pandas?


    
    <code># dates
    dates = pd.date_range('2010-04-21', '2015-04-21')
    
    # create a data frame of dates as index column
    df = pd.DataFrame(index=dates)
    </code>



How to read a CSV File?

How to read CSV file with specific index columns?

How to parse dates in a CSV File?

How to read only required columns from CSV File?

How to specific the NULL values notation in CSV File?


    
    <code># read csv file
    df_spy = pd.read_csv(
            'data/%s.csv' %s 'SPY',
            index_col='Dates', # specific index
            parse_dates=True, # identify Date columns as DateTime values
            usecols=['Date', 'Adj Close'], # cols we need
            na_values=['nan'] # csv has NAN as NULL values, so tell CSV ahead.
                )
    </code>



How to join two data frames?


    
    <code># join data frames - default LEFT join
    df = df1.join(df_spy)
    </code>



How to rename a data frame column?


    
    <code>df.rename(columns={'Adj Close':'SPY'})
    </code>



How to drop na values in a data frame?


    
    <code>df.dropna()
    </code>



How to do a inner join of data frames?


    
    <code>df.join(df_)
    </code>



How to plot a DataFrame?

How to set plot fontsize?

How to set plot label?

How to set x label and y label?


    
    <code>ax = df.plot(title='Stock Prices', fontsize=2)
    ax.set_xlabel('Date')
    ax.set_ylabel('Prices')
    plt.show()
    </code>



How take a slice of data?


    
    <code>df_new = df.ix[start_index:end_index]
    </code>





## Cheat Sheet



[![](https://itssampath.files.wordpress.com/2015/06/panda.jpg?w=29)](https://itssampath.files.wordpress.com/2015/06/panda.jpg?w=29)

Felt too easy? Here is one more for you




    
  * [http://www.datadependence.com/2016/05/scientific-python-pandas/](http://www.datadependence.com/2016/05/scientific-python-pandas/)


