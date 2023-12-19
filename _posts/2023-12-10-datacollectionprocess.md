---
layout: post
title:  "NBA Data Collection Process"
author: "Adam Gao"
description: "My semester project for NBA Data Analysis"
image: /assets/images/semesterprojectheaderimage.png
--- 
#Objective
My overall objective for this project is to see what statistics correlate with one another from NBA league leaders. As someone who's too broke to afford NBA league pass and other sports channels, I've always analyzed basketball games by looking at their box scores as a performance indicator. Pretty basic right? However, a simple stat line of points, assists, and rebounds do not tell the whole story. With an EDA up next, I would like to explain how I got the data that I performed my analysis on and what I did to filter and clean the data for a more enhanced analysis.

# Finding the Data  
The NBA has an official website where they have league leaders. League leaders are determined by this metric given by the offical NBA [here](https://www.nba.com/stats/help/statminimums). I found [this](https://www.nba.com/stats/leaders) website to collect my data through the offical NBA API. What I did was 
<br>
1. Inspect the page (or control + shift + c)
2. Clicked over on the network tag of the insepct element feature.
3. Click on the top link of the name heading to open the request URL
<br>

From there you have your request URL! Now onto the coding.

<br>
Make sure these packages are imported
```
import pandas as pd
import requests
pd.set_option('display.max_columns', None)
import time
import numpy as np



Create a url variable and set it equal to your request URL:

```
test_url = 'https://stats.nba.com/stats/leagueLeaders?LeagueID=00&PerMode=PerGame&Scope=S&Season=2021-22&SeasonType=Regular%20Season&StatCategory=PTS'
```

Use the test_url variable to put into the request.get(url = ).json() function so that the JSON will convert to a dictionary. 


```
r = requests.get(url = test_url).json()
```




