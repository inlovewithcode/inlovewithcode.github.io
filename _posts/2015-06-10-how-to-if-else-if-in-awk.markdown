---
author: guidedmissile
comments: true
date: 2015-06-10 04:48:57+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2015/06/10/how-to-if-else-if-in-awk/
slug: how-to-if-else-if-in-awk
title: How to 'if else if' in awk?
wordpress_id: 350
categories:
- Linux Scripting
- Unix
tags:
- Bash
- Shell Scripting
---

Have you ever face an issue where you have made multiple files from one big file based on tag/column value present in a line? Then this post is for you. At the end of the post, i.e. in next 5 mins you will be able to answer below questions.


#### How to split a file based on condition?
How to segregate data in file?
How to use if else if condition in awk?
How to pass variable to awk?


Problem statement: I have a list of servers in inventory.csv. Now I want to segregate unix team's data into multiple files based on team name.
I know that I have teams - teamA, teamB, teamC

    
    # defining myPathiable
    folder_location="/tmp/sam"
    
    # using 'grep -iw' we search for Unix team data
    # using '-v' option passing variable inside awk
    grep -iw unix inventory.csv | awk -v myPath="${folder_location}" -F: '{
    # using condition if & else if condition seggregating data
    # below conditon for teamA
    if ($8 == "teamA") print > "myPath/teamA.csv"
    # below conditon for teamB
    else if ($8 == "teamB") print > "myPath/teamB.csv"
    # below conditon for teamC
    else if ($8 == "teamC") print > "myPath/teamB.csv"
    # optimism # below conditon if there is a new team which is not teamA or teamB or teamC
    else print > "myPath/others.csv"
    }'
    


Re-writing above code

    
    #!\bin\bash
    folder_location="/tmp/sam"
    grep -iw unix inventory.csv | awk -v myPath="${folder_location}" -F: '{
    if ($8 == "teamA") print > "myPath/teamA.csv"
    else if ($8 == "teamB") print > "myPath/teamB.csv"
    else if ($8 == "teamC") print > "myPath/teamB.csv"
    else print > "myPath/others.csv"
     }'
    


Assignment: In programming, parsing a file twice is a sin. In the above code we are using 'grep' to parse & find the unix data. If you have understood awk, you should be able to make above code more beautiful just with -awk. Good Luck.
