---
author: guidedmissile
comments: false
date: 2015-05-24 15:34:02+00:00
layout: page
link: https://inlovewithcode.wordpress.com/bash/
slug: bash
title: Shell Scripting(BASH)
wordpress_id: 339
---

In this Bash Tutorial, we will learn about variables, loops and functions.







#### How to start writing a shell script?




First we write header, to tell the system that this is no common file and so try to use specified tool generally which is either -bash or -sh or -csh



    
    #!/bin/bash







#### What are variables?




Variables are the building blocks every programming language. Say you need to count 2 numbers, or say you need to find number of sshd-process are running, no. of users logged in - you need a place or a point to store this value, which we call it variable.



    
    KEY='portal.conf'
    COMMAND='ps -ef'




These variable can store all kinds of information. In programming languages like C, Java, C#, Python, Ruby, Scala and all we have specific category of variables depending on their purpose. For storing numerical values we use integer-variables, float-variables & double-variables. For storing characters and names we use String-Variables or list or arrays - variables.







Here in Shell Script, we don't much distinguish on what category type of variable except we need to remember what operation we might need to perform on them. Like for integer or numbers, we can perform addition or subtraction or division operations.




#### What is a loop/looping?




Loop/Looping - as the name defines, it is an action/event which occurs in repetitive manner to give desirable output.







For example you need to print 100 numbers, implies we need a repetitive event for adding 1 to a number in step wise manner and while doing it we need to print the value. Thus we can print 100 numbers.




#### How to do looping?




There are many types of loop, but one such famous is for-loop.



    
    for line in `${COMMAND} | grep -i ${KEY}`
    do
    echo $line
    done




#### How to read a file line by line?



    
    while read line;
    do $line
    done < `${COMMAND} | grep -i ${KEY}`




#### What is a function?




A function is nothing but a accumulation of set of instructions to be performed in a constructive sequence to generate a desired output.




#### How to create a function?




Here we are creating a function which to count no.of sshd - processes running in the system



    
    get_processes_count() {
    ps -ef | grep -i ssd | grep -v 'grep' | wc -l
    }




#### How to re-use above function code for find no.of for ntpd or httpd or sendmail ?


First we are creating a function which to count no.of sshd - processes running in the system

    
    get_processes_count() {
    check_for=$1 # taking input from user
    ps -ef | grep -i $check_for | grep -v 'grep' | wc -l
    }




##### Usage:



    
    get_processes_count httpd
    get_processes_count sshd







#### How to define numbers or adding number in shell?



    
    #Here we are defining a variable called -ct
    ct=0
    ct=$(( ct + 1 ))
    # print value of to screen
    echo ct
    ct=$(( ct + 1 ))
    echo $ct




#### How to count number of lines in a file # same as '''wc -l my.csv'''



    
    word_count() {
    input_line=$1
    ct=0
    for i in $input_line
    do
    echo $i
    ct=$(( ct + 1 )) # counting
    done
    ct=0
    while read line
    do
    ct=$(( ct + 1 )) # adding number
    done < my.csv
    


# counting number of words in a line

    
    word_count() {
    input_line=$1
    ct=0
    for i in $input_line
    do
    echo $i
    ct=$(( ct + 1 )) # counting
    done
    




#### Simple Learning Projects to enhance your scripting script?


Here is a small script which is count the number of words in a given input line.

    
    # Here is the code with comments and explanation
    word_count() {
        # reading input from user
        data=$1
        # starting a counter
        ct=0
        # looping around the input
        for i in ${data}
            do
            # for each word increase value in ct
            ct=$((ct + 1))
            done
        # printing value of ct
        echo $ct
    }
    



    
    # same as above, just removed comments
    word_count() {
        data=$1
        ct=0
        for i in ${data}
            do
            ct=$((ct + 1))
            done
        echo $ct
    }
    



    
    Lets tests above function
    bash-3.2$ word_count "hello world"
    2
    bash-3.2$ word_count "hi siraj, how are you doing today would you care for a Pie?"
    13
    bash-3.2$
    


Lets modify this code to show how for each variable count is increasing

    
    word_count_new() {
        data=$1
        ct=0
        for i in ${data}
            do
            ct=$((ct + 1))
            # here we are adding new line for printing
            echo ${ct}" "${i}
            done
        echo $ct
    }
    


here is an sample test

    
    bash-3.2$ word_count_new "hi siraj, how are you doing today would you care for a Pie?"
    1 hi
    2 siraj,
    3 how
    4 are
    5 you
    6 doing
    7 today
    8 would
    9 you
    10 care
    11 for
    12 a
    13 Pie?
    13
    
    bash-3.2$ echo "hi siraj, how are you doing today would you care for a Pie?" | wc -w
    13
    




#### How to read a file line by line and count number of words in each line?



    
    bash-3.2$ cat test.sh
    #!/bin/bash
    word_count() {
        data=$1
        ct=0
        for i in ${data}
            do
            ct=$((ct + 1))
            done
        echo $ct
    }
    
    FILE="about"
    while read line; do
         word_count "$line"
    done < $FILE
    bash-3.2$
    bash-3.2$ chmod +x test.sh
    bash-3.2$ ./test.sh 
    39 
    30 
    48 
    0 
    2
    




You might have already known but if you knew about "wc" tool, you can easily do this count script but in real time scenario where you might need to this job like find nslookup value of hundred servers or other, you need to learn parsing. This tutorial is not about efficient or about doing the jobs quickly.

This tutorial is only to help to learn shell scripting quickly!
