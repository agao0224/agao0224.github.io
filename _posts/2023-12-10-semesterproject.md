---
layout: post
title:  "NBA Data Analytics in Python"
author: "Adam Gao"
description: "My semester project for NBA Data Analysis"
image: /assets/images/semesterprojectheaderimage.png
--- 

# Introduction 
As a lifelong NBA fan, I've always had an eye for box score stats and looking up the statistics of my favorite NBA players. As an avid NBA box score checker, I've seen that throughout the years of looking at NBA analytics, there are new variables and statistics that measure a player's performance every couple or so years. For example, FiveThirtyEight has came out with a new NBA performance metric called RAPTOR, a rating that measures performance based on the number of points a player contributes to team offense and team defense per 100 possessions, relative to a league-average player. There has also been other metrics such as win shares, true shooting, etc. that have made me realized how easy it is to interpret and collect data from basketball games. For this project, I have gathered data of official league leaders from the beginning of each decade starting from 2000-2020. [Here's how I collected the data.](https://agao0224.github.io/2023/12/10/datacollectionprocess.html) League leaders are based on these metrics: 

<strong>For a player to qualify as a league leader</strong>:

<strong>Scoring & Rebounds</strong>: They need to play in at least 70% of their team's games (which would be 58 out of 82 games in a regular season).

<strong>Field Goal Percentage</strong>: They must make a minimum of 300 field goals.

<strong>Free Throw Percentage</strong>: They need to make at least 125 free throws.

<strong>Three-Point Percentage</strong>: They should make a minimum of 82 three-point field goals.

<strong>Assists, Steals, Blocked Shots, Minutes</strong>: For each of these categories, the player needs to play in 70% of their team's games.

<strong>Assist-to-Turnover Ratio</strong>: They need to achieve at least 200 assists.

<strong>Steal-to-Turnover Ratio</strong>: They should have a minimum of 82 steals.

Meeting these criteria suggests a certain level of consistency and performance in various aspects of the game over the course of a season.

# EDA 
While completing this project, I had a number of questions that I had in mind when looking at NBA league leader statistics. Through this section I will take you through the questions I as well as many others have and the visuals I've generated that can hopefully answer those questions.

# Numerical data distributions
I've created a funciton in python that has generated a histogram of every numerical variable we have in our data. In other words, this shows the distribution of every numerical value in our dataset for NBA Official League Leaders in each decade starting from 2000. This table was created to represent statistical summaries for various basketball-related numeric variables. Each row corresponds to a different statistical measure or property for a specific column in a dataset. I've excluded the ranks from the dataset simply because there is not much of a point to compare the distribution of unique rankings, as the rankings will generally be uniform. 

<br>
<strong>Lets ask ourselves some questions really fast:</strong>

1. What's the average points per game from offical league leaders?
2. What's the average amount of rebounds per game? 
3. What's the average amount of assists per game?
4. What is the common most amount of games played per season?
5. What is the average amount of minutes per game? 

<br>

![Figure](/assets/images/minutesplayed.png)
![Figure](/assets/images/gp.png)
![Figure](/assets/images/fgm.png)
![Figure](/assets/images/fg_pct.png)
![Figure](/assets/images/fg3m.png)
![Figure](/assets/images/fg3a.png)
![Figure](/assets/images/fg3_pct.png)
![Figure](/assets/images/ftm.png)
![Figure](/assets/images/fta.png)
![Figure](/assets/images/ft_pct.png)
![Figure](/assets/images/oreb.png)
![Figure](/assets/images/dreb.png)
![Figure](/assets/images/ast.png)
![Figure](/assets/images/stl.png)
![Figure](/assets/images/blk.png)
![Figure](/assets/images/tov.png)
![Figure](/assets/images/pts.png)
![Figure](/assets/images/eff.png)

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: middle;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Count</th>
      <th>Null</th>
      <th>Unique</th>
      <th>Type</th>
      <th>Min</th>
      <th>Max</th>
      <th>25%</th>
      <th>50%</th>
      <th>75%</th>
      <th>Mean</th>
      <th>Mode</th>
      <th>Std</th>
      <th>Skew</th>
      <th>Kurt</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>RANK</th>
      <td>594</td>
      <td>0</td>
      <td>228</td>
      <td>int64</td>
      <td>1.000</td>
      <td>228.000</td>
      <td>50.00000</td>
      <td>99.5000</td>
      <td>149.00000</td>
      <td>100.65</td>
      <td>60.00</td>
      <td>59.249852</td>
      <td>0.122702</td>
      <td>-1.016754</td>
    </tr>
    <tr>
      <th>GP</th>
      <td>594</td>
      <td>0</td>
      <td>26</td>
      <td>int64</td>
      <td>58.000</td>
      <td>83.000</td>
      <td>70.00000</td>
      <td>76.0000</td>
      <td>80.00000</td>
      <td>74.40</td>
      <td>82.00</td>
      <td>6.371976</td>
      <td>-0.689956</td>
      <td>-0.381956</td>
    </tr>
    <tr>
      <th>MIN</th>
      <td>594</td>
      <td>0</td>
      <td>255</td>
      <td>float64</td>
      <td>9.200</td>
      <td>42.000</td>
      <td>21.50000</td>
      <td>27.6000</td>
      <td>33.10000</td>
      <td>27.18</td>
      <td>26.30</td>
      <td>7.221785</td>
      <td>-0.109682</td>
      <td>-0.851356</td>
    </tr>
    <tr>
      <th>FGM</th>
      <td>594</td>
      <td>0</td>
      <td>95</td>
      <td>float64</td>
      <td>0.700</td>
      <td>11.200</td>
      <td>2.90000</td>
      <td>3.9000</td>
      <td>5.70000</td>
      <td>4.47</td>
      <td>3.60</td>
      <td>2.130021</td>
      <td>0.824448</td>
      <td>0.108317</td>
    </tr>
    <tr>
      <th>FGA</th>
      <td>594</td>
      <td>0</td>
      <td>177</td>
      <td>float64</td>
      <td>1.300</td>
      <td>25.500</td>
      <td>6.40000</td>
      <td>8.7000</td>
      <td>12.30000</td>
      <td>9.72</td>
      <td>7.10</td>
      <td>4.539116</td>
      <td>0.761497</td>
      <td>0.066414</td>
    </tr>
    <tr>
      <th>FG_PCT</th>
      <td>594</td>
      <td>0</td>
      <td>196</td>
      <td>float64</td>
      <td>0.336</td>
      <td>0.761</td>
      <td>0.42325</td>
      <td>0.4510</td>
      <td>0.48900</td>
      <td>0.46</td>
      <td>0.44</td>
      <td>0.058320</td>
      <td>1.467889</td>
      <td>3.618948</td>
    </tr>
    <tr>
      <th>FG3M</th>
      <td>594</td>
      <td>0</td>
      <td>36</td>
      <td>float64</td>
      <td>0.000</td>
      <td>4.500</td>
      <td>0.10000</td>
      <td>0.9000</td>
      <td>1.50000</td>
      <td>0.97</td>
      <td>0.00</td>
      <td>0.849270</td>
      <td>0.705217</td>
      <td>-0.011430</td>
    </tr>
    <tr>
      <th>FG3A</th>
      <td>594</td>
      <td>0</td>
      <td>87</td>
      <td>float64</td>
      <td>0.000</td>
      <td>11.700</td>
      <td>0.42500</td>
      <td>2.5500</td>
      <td>4.20000</td>
      <td>2.68</td>
      <td>0.00</td>
      <td>2.249721</td>
      <td>0.648061</td>
      <td>-0.050451</td>
    </tr>
    <tr>
      <th>FG3_PCT</th>
      <td>594</td>
      <td>0</td>
      <td>196</td>
      <td>float64</td>
      <td>0.000</td>
      <td>1.000</td>
      <td>0.27025</td>
      <td>0.3410</td>
      <td>0.37900</td>
      <td>0.29</td>
      <td>0.00</td>
      <td>0.144798</td>
      <td>-0.749413</td>
      <td>1.738350</td>
    </tr>
    <tr>
      <th>FTM</th>
      <td>594</td>
      <td>0</td>
      <td>69</td>
      <td>float64</td>
      <td>0.200</td>
      <td>9.600</td>
      <td>1.10000</td>
      <td>1.7000</td>
      <td>2.80000</td>
      <td>2.15</td>
      <td>1.20</td>
      <td>1.535517</td>
      <td>1.532203</td>
      <td>2.662149</td>
    </tr>
    <tr>
      <th>FTA</th>
      <td>594</td>
      <td>0</td>
      <td>88</td>
      <td>float64</td>
      <td>0.200</td>
      <td>13.100</td>
      <td>1.50000</td>
      <td>2.3000</td>
      <td>3.60000</td>
      <td>2.80</td>
      <td>1.50</td>
      <td>1.942051</td>
      <td>1.685008</td>
      <td>3.843007</td>
    </tr>
    <tr>
      <th>FT_PCT</th>
      <td>594</td>
      <td>0</td>
      <td>278</td>
      <td>float64</td>
      <td>0.262</td>
      <td>1.000</td>
      <td>0.71400</td>
      <td>0.7765</td>
      <td>0.83375</td>
      <td>0.76</td>
      <td>0.83</td>
      <td>0.096031</td>
      <td>-1.167278</td>
      <td>2.559122</td>
    </tr>
    <tr>
      <th>OREB</th>
      <td>594</td>
      <td>0</td>
      <td>43</td>
      <td>float64</td>
      <td>0.100</td>
      <td>4.600</td>
      <td>0.50000</td>
      <td>0.9000</td>
      <td>1.70000</td>
      <td>1.21</td>
      <td>0.50</td>
      <td>0.893545</td>
      <td>1.215181</td>
      <td>1.050127</td>
    </tr>
    <tr>
      <th>DREB</th>
      <td>594</td>
      <td>0</td>
      <td>84</td>
      <td>float64</td>
      <td>0.900</td>
      <td>11.000</td>
      <td>2.30000</td>
      <td>3.2000</td>
      <td>4.50000</td>
      <td>3.62</td>
      <td>3.20</td>
      <td>1.847794</td>
      <td>1.278320</td>
      <td>1.627872</td>
    </tr>
    <tr>
      <th>REB</th>
      <td>594</td>
      <td>0</td>
      <td>109</td>
      <td>float64</td>
      <td>1.000</td>
      <td>15.200</td>
      <td>3.00000</td>
      <td>4.1000</td>
      <td>5.90000</td>
      <td>4.83</td>
      <td>2.60</td>
      <td>2.567251</td>
      <td>1.200907</td>
      <td>1.307360</td>
    </tr>
    <tr>
      <th>AST</th>
      <td>594</td>
      <td>0</td>
      <td>86</td>
      <td>float64</td>
      <td>0.300</td>
      <td>11.400</td>
      <td>1.20000</td>
      <td>2.1000</td>
      <td>3.50000</td>
      <td>2.69</td>
      <td>1.20</td>
      <td>2.020522</td>
      <td>1.446322</td>
      <td>2.047953</td>
    </tr>
    <tr>
      <th>STL</th>
      <td>594</td>
      <td>0</td>
      <td>25</td>
      <td>float64</td>
      <td>0.100</td>
      <td>2.500</td>
      <td>0.60000</td>
      <td>0.8000</td>
      <td>1.10000</td>
      <td>0.86</td>
      <td>0.70</td>
      <td>0.395128</td>
      <td>0.908068</td>
      <td>1.012023</td>
    </tr>
    <tr>
      <th>BLK</th>
      <td>594</td>
      <td>0</td>
      <td>28</td>
      <td>float64</td>
      <td>0.000</td>
      <td>2.800</td>
      <td>0.20000</td>
      <td>0.4000</td>
      <td>0.70000</td>
      <td>0.55</td>
      <td>0.20</td>
      <td>0.513720</td>
      <td>1.873961</td>
      <td>3.882191</td>
    </tr>
    <tr>
      <th>TOV</th>
      <td>594</td>
      <td>0</td>
      <td>41</td>
      <td>float64</td>
      <td>0.300</td>
      <td>4.500</td>
      <td>0.90000</td>
      <td>1.3000</td>
      <td>2.00000</td>
      <td>1.56</td>
      <td>0.90</td>
      <td>0.798872</td>
      <td>0.948286</td>
      <td>0.411483</td>
    </tr>
    <tr>
      <th>PTS</th>
      <td>594</td>
      <td>0</td>
      <td>209</td>
      <td>float64</td>
      <td>2.000</td>
      <td>31.100</td>
      <td>7.72500</td>
      <td>10.6000</td>
      <td>15.57500</td>
      <td>12.05</td>
      <td>8.30</td>
      <td>5.886051</td>
      <td>0.878403</td>
      <td>0.312686</td>
    </tr>
    <tr>
      <th>EFF</th>
      <td>594</td>
      <td>0</td>
      <td>208</td>
      <td>float64</td>
      <td>3.300</td>
      <td>38.700</td>
      <td>9.10000</td>
      <td>12.4000</td>
      <td>17.00000</td>
      <td>13.52</td>
      <td>7.60</td>
      <td>5.843662</td>
      <td>0.823828</td>
      <td>0.531834</td>Av
    </tr>
  </tbody>
</table>
</div>

Unfortunately, some of these histograms are impacted by outliers as you can tell. From the histograms and table however, we can see that: 

1. The average amount of points per game is 12.05
2. The average amount of rebounds per game is 4.8
3. The average amount of assists per game is 2.69
4. The mode for amount of games played is 82
5. The average amount of minutes per game is 27. 

Some of the outliers shown in the visualizations can be explained however. For example, it says that a player made 100% of their 3's in that decade. However, this could be because it was the only 3 point shot the player has attempted for that season. 

# Which Stats Are Correlated With Each Other
For this next part of the analysis, I want to see which stats are correlated with one another. I've created code that gives a table of correlation values and made a correlation matrix in the process. 

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>YEAR</th>
      <th>MIN</th>
      <th>FGM</th>
      <th>FGA</th>
      <th>FG3M</th>
      <th>FG3A</th>
      <th>FTM</th>
      <th>FTA</th>
      <th>OREB</th>
      <th>DREB</th>
      <th>...</th>
      <th>PTS</th>
      <th>FG%</th>
      <th>3PT%</th>
      <th>FT%</th>
      <th>FG3A%</th>
      <th>PTS/FGA</th>
      <th>FG3M/FGM</th>
      <th>FTA/FGM</th>
      <th>TRU%</th>
      <th>AST_TOV</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>YEAR</th>
      <td>1.000000</td>
      <td>-0.156342</td>
      <td>0.161334</td>
      <td>0.110760</td>
      <td>0.470672</td>
      <td>0.495402</td>
      <td>-0.133901</td>
      <td>-0.168610</td>
      <td>-0.104936</td>
      <td>0.114384</td>
      <td>...</td>
      <td>0.185017</td>
      <td>0.148162</td>
      <td>0.185177</td>
      <td>0.130719</td>
      <td>0.475084</td>
      <td>0.220404</td>
      <td>0.416975</td>
      <td>-0.257614</td>
      <td>0.459798</td>
      <td>0.235780</td>
    </tr>
    <tr>
      <th>MIN</th>
      <td>-0.156342</td>
      <td>1.000000</td>
      <td>0.494108</td>
      <td>0.491652</td>
      <td>0.073588</td>
      <td>0.064409</td>
      <td>0.456245</td>
      <td>0.404330</td>
      <td>-0.141821</td>
      <td>0.027624</td>
      <td>...</td>
      <td>0.520334</td>
      <td>0.013228</td>
      <td>0.038342</td>
      <td>0.245711</td>
      <td>-0.060026</td>
      <td>0.124696</td>
      <td>-0.056597</td>
      <td>0.090600</td>
      <td>0.107527</td>
      <td>0.115425</td>
    </tr>
    <tr>
      <th>FGM</th>
      <td>0.161334</td>
      <td>0.494108</td>
      <td>1.000000</td>
      <td>0.913014</td>
      <td>0.142149</td>
      <td>0.149353</td>
      <td>0.641763</td>
      <td>0.610877</td>
      <td>0.000132</td>
      <td>0.207963</td>
      <td>...</td>
      <td>0.957375</td>
      <td>0.217305</td>
      <td>0.003121</td>
      <td>0.186272</td>
      <td>-0.136899</td>
      <td>0.201079</td>
      <td>-0.159864</td>
      <td>0.044854</td>
      <td>0.233979</td>
      <td>-0.085844</td>
    </tr>
    <tr>
      <th>FGA</th>
      <td>0.110760</td>
      <td>0.491652</td>
      <td>0.913014</td>
      <td>1.000000</td>
      <td>0.358040</td>
      <td>0.380925</td>
      <td>0.582620</td>
      <td>0.509220</td>
      <td>-0.262677</td>
      <td>-0.021695</td>
      <td>...</td>
      <td>0.928221</td>
      <td>-0.182290</td>
      <td>0.080002</td>
      <td>0.321090</td>
      <td>0.083727</td>
      <td>-0.100086</td>
      <td>0.067254</td>
      <td>-0.129912</td>
      <td>-0.044494</td>
      <td>0.017929</td>
    </tr>
    <tr>
      <th>FG3M</th>
      <td>0.470672</td>
      <td>0.073588</td>
      <td>0.142149</td>
      <td>0.358040</td>
      <td>1.000000</td>
      <td>0.987511</td>
      <td>-0.125247</td>
      <td>-0.244759</td>
      <td>-0.638153</td>
      <td>-0.366543</td>
      <td>...</td>
      <td>0.300163</td>
      <td>-0.482116</td>
      <td>0.576276</td>
      <td>0.458296</td>
      <td>0.916281</td>
      <td>-0.132323</td>
      <td>0.917115</td>
      <td>-0.515179</td>
      <td>0.175737</td>
      <td>0.354584</td>
    </tr>
    <tr>
      <th>FG3A</th>
      <td>0.495402</td>
      <td>0.064409</td>
      <td>0.149353</td>
      <td>0.380925</td>
      <td>0.987511</td>
      <td>1.000000</td>
      <td>-0.113924</td>
      <td>-0.232845</td>
      <td>-0.645608</td>
      <td>-0.360629</td>
      <td>...</td>
      <td>0.306500</td>
      <td>-0.515801</td>
      <td>0.521930</td>
      <td>0.451510</td>
      <td>0.921465</td>
      <td>-0.172180</td>
      <td>0.903326</td>
      <td>-0.518073</td>
      <td>0.123094</td>
      <td>0.358009</td>
    </tr>
    <tr>
      <th>FTM</th>
      <td>-0.133901</td>
      <td>0.456245</td>
      <td>0.641763</td>
      <td>0.582620</td>
      <td>-0.125247</td>
      <td>-0.113924</td>
      <td>1.000000</td>
      <td>0.962586</td>
      <td>0.063835</td>
      <td>0.188630</td>
      <td>...</td>
      <td>0.751014</td>
      <td>0.146932</td>
      <td>-0.123340</td>
      <td>0.216010</td>
      <td>-0.309657</td>
      <td>0.461138</td>
      <td>-0.318734</td>
      <td>0.628690</td>
      <td>0.186510</td>
      <td>-0.182727</td>
    </tr>
    <tr>
      <th>FTA</th>
      <td>-0.168610</td>
      <td>0.404330</td>
      <td>0.610877</td>
      <td>0.509220</td>
      <td>-0.244759</td>
      <td>-0.232845</td>
      <td>0.962586</td>
      <td>1.000000</td>
      <td>0.217962</td>
      <td>0.302631</td>
      <td>...</td>
      <td>0.688374</td>
      <td>0.251313</td>
      <td>-0.204253</td>
      <td>-0.020451</td>
      <td>-0.419445</td>
      <td>0.494311</td>
      <td>-0.425595</td>
      <td>0.736016</td>
      <td>0.157715</td>
      <td>-0.271229</td>
    </tr>
    <tr>
      <th>OREB</th>
      <td>-0.104936</td>
      <td>-0.141821</td>
      <td>0.000132</td>
      <td>-0.262677</td>
      <td>-0.638153</td>
      <td>-0.645608</td>
      <td>0.063835</td>
      <td>0.217962</td>
      <td>1.000000</td>
      <td>0.727059</td>
      <td>...</td>
      <td>-0.132660</td>
      <td>0.648804</td>
      <td>-0.481667</td>
      <td>-0.553503</td>
      <td>-0.656225</td>
      <td>0.360683</td>
      <td>-0.646807</td>
      <td>0.475427</td>
      <td>0.155200</td>
      <td>-0.549249</td>
    </tr>
    <tr>
      <th>DREB</th>
      <td>0.114384</td>
      <td>0.027624</td>
      <td>0.207963</td>
      <td>-0.021695</td>
      <td>-0.366543</td>
      <td>-0.360629</td>
      <td>0.188630</td>
      <td>0.302631</td>
      <td>0.727059</td>
      <td>1.000000</td>
      <td>...</td>
      <td>0.122498</td>
      <td>0.534512</td>
      <td>-0.335757</td>
      <td>-0.377702</td>
      <td>-0.413244</td>
      <td>0.375339</td>
      <td>-0.428657</td>
      <td>0.374053</td>
      <td>0.239412</td>
      <td>-0.412141</td>
    </tr>
    <tr>
      <th>REB</th>
      <td>0.033350</td>
      <td>-0.037994</td>
      <td>0.139033</td>
      <td>-0.120254</td>
      <td>-0.503071</td>
      <td>-0.501850</td>
      <td>0.151171</td>
      <td>0.289677</td>
      <td>0.889353</td>
      <td>0.960029</td>
      <td>...</td>
      <td>0.028029</td>
      <td>0.618290</td>
      <td>-0.413270</td>
      <td>-0.476950</td>
      <td>-0.541054</td>
      <td>0.394836</td>
      <td>-0.547609</td>
      <td>0.440406</td>
      <td>0.221537</td>
      <td>-0.497161</td>
    </tr>
    <tr>
      <th>AST</th>
      <td>0.084033</td>
      <td>0.271924</td>
      <td>0.197598</td>
      <td>0.294424</td>
      <td>0.223648</td>
      <td>0.244434</td>
      <td>0.187846</td>
      <td>0.107090</td>
      <td>-0.475528</td>
      <td>-0.311724</td>
      <td>...</td>
      <td>0.257768</td>
      <td>-0.238944</td>
      <td>0.184219</td>
      <td>0.274147</td>
      <td>0.174624</td>
      <td>-0.103589</td>
      <td>0.154561</td>
      <td>-0.111971</td>
      <td>-0.063886</td>
      <td>0.736716</td>
    </tr>
    <tr>
      <th>STL</th>
      <td>0.016009</td>
      <td>0.041517</td>
      <td>-0.055149</td>
      <td>0.008173</td>
      <td>0.079155</td>
      <td>0.096760</td>
      <td>-0.041507</td>
      <td>-0.073164</td>
      <td>-0.227962</td>
      <td>-0.233420</td>
      <td>...</td>
      <td>-0.032751</td>
      <td>-0.161951</td>
      <td>0.057620</td>
      <td>0.094767</td>
      <td>0.132051</td>
      <td>-0.128543</td>
      <td>0.111858</td>
      <td>-0.129977</td>
      <td>-0.082196</td>
      <td>0.351988</td>
    </tr>
    <tr>
      <th>BLK</th>
      <td>-0.070569</td>
      <td>-0.090029</td>
      <td>-0.007863</td>
      <td>-0.211520</td>
      <td>-0.464509</td>
      <td>-0.465949</td>
      <td>0.047327</td>
      <td>0.185534</td>
      <td>0.706623</td>
      <td>0.618330</td>
      <td>...</td>
      <td>-0.101667</td>
      <td>0.505848</td>
      <td>-0.402469</td>
      <td>-0.472988</td>
      <td>-0.467320</td>
      <td>0.300477</td>
      <td>-0.460794</td>
      <td>0.389727</td>
      <td>0.133111</td>
      <td>-0.490808</td>
    </tr>
    <tr>
      <th>TOV</th>
      <td>-0.151187</td>
      <td>0.272099</td>
      <td>0.468690</td>
      <td>0.491533</td>
      <td>-0.094846</td>
      <td>-0.066556</td>
      <td>0.548728</td>
      <td>0.547257</td>
      <td>-0.041263</td>
      <td>0.070385</td>
      <td>...</td>
      <td>0.490553</td>
      <td>-0.041530</td>
      <td>-0.095915</td>
      <td>0.027315</td>
      <td>-0.246164</td>
      <td>0.023715</td>
      <td>-0.261802</td>
      <td>0.263908</td>
      <td>-0.148573</td>
      <td>-0.047842</td>
    </tr>
    <tr>
      <th>EFF</th>
      <td>0.260093</td>
      <td>0.354421</td>
      <td>0.677304</td>
      <td>0.424857</td>
      <td>-0.129986</td>
      <td>-0.131887</td>
      <td>0.565701</td>
      <td>0.591411</td>
      <td>0.441613</td>
      <td>0.684441</td>
      <td>...</td>
      <td>0.637473</td>
      <td>0.598534</td>
      <td>-0.104072</td>
      <td>-0.041948</td>
      <td>-0.307448</td>
      <td>0.585874</td>
      <td>-0.334803</td>
      <td>0.363365</td>
      <td>0.525303</td>
      <td>-0.034636</td>
    </tr>
    <tr>
      <th>PTS</th>
      <td>0.185017</td>
      <td>0.520334</td>
      <td>0.957375</td>
      <td>0.928221</td>
      <td>0.300163</td>
      <td>0.306500</td>
      <td>0.751014</td>
      <td>0.688374</td>
      <td>-0.132660</td>
      <td>0.122498</td>
      <td>...</td>
      <td>1.000000</td>
      <td>0.086329</td>
      <td>0.089540</td>
      <td>0.310973</td>
      <td>0.021039</td>
      <td>0.260089</td>
      <td>0.001675</td>
      <td>0.109884</td>
      <td>0.269595</td>
      <td>-0.032942</td>
    </tr>
    <tr>
      <th>FG%</th>
      <td>0.148162</td>
      <td>0.013228</td>
      <td>0.217305</td>
      <td>-0.182290</td>
      <td>-0.482116</td>
      <td>-0.515801</td>
      <td>0.146932</td>
      <td>0.251313</td>
      <td>0.648804</td>
      <td>0.534512</td>
      <td>...</td>
      <td>0.086329</td>
      <td>1.000000</td>
      <td>-0.188610</td>
      <td>-0.351649</td>
      <td>-0.536932</td>
      <td>0.766561</td>
      <td>-0.551004</td>
      <td>0.461265</td>
      <td>0.693715</td>
      <td>-0.274199</td>
    </tr>
    <tr>
      <th>3PT%</th>
      <td>0.185177</td>
      <td>0.038342</td>
      <td>0.003121</td>
      <td>0.080002</td>
      <td>0.576276</td>
      <td>0.521930</td>
      <td>-0.123340</td>
      <td>-0.204253</td>
      <td>-0.481667</td>
      <td>-0.335757</td>
      <td>...</td>
      <td>0.089540</td>
      <td>-0.188610</td>
      <td>1.000000</td>
      <td>0.317252</td>
      <td>0.543673</td>
      <td>0.041528</td>
      <td>0.561827</td>
      <td>-0.337636</td>
      <td>0.261461</td>
      <td>0.303896</td>
    </tr>
    <tr>
      <th>FT%</th>
      <td>0.130719</td>
      <td>0.245711</td>
      <td>0.186272</td>
      <td>0.321090</td>
      <td>0.458296</td>
      <td>0.451510</td>
      <td>0.216010</td>
      <td>-0.020451</td>
      <td>-0.553503</td>
      <td>-0.377702</td>
      <td>...</td>
      <td>0.310973</td>
      <td>-0.351649</td>
      <td>0.317252</td>
      <td>1.000000</td>
      <td>0.419665</td>
      <td>-0.032485</td>
      <td>0.417164</td>
      <td>-0.302442</td>
      <td>0.163639</td>
      <td>0.303187</td>
    </tr>
    <tr>
      <th>FG3A%</th>
      <td>0.475084</td>
      <td>-0.060026</td>
      <td>-0.136899</td>
      <td>0.083727</td>
      <td>0.916281</td>
      <td>0.921465</td>
      <td>-0.309657</td>
      <td>-0.419445</td>
      <td>-0.656225</td>
      <td>-0.413244</td>
      <td>...</td>
      <td>0.021039</td>
      <td>-0.536932</td>
      <td>0.543673</td>
      <td>0.419665</td>
      <td>1.000000</td>
      <td>-0.191705</td>
      <td>0.985267</td>
      <td>-0.573006</td>
      <td>0.135227</td>
      <td>0.414777</td>
    </tr>
    <tr>
      <th>PTS/FGA</th>
      <td>0.220404</td>
      <td>0.124696</td>
      <td>0.201079</td>
      <td>-0.100086</td>
      <td>-0.132323</td>
      <td>-0.172180</td>
      <td>0.461138</td>
      <td>0.494311</td>
      <td>0.360683</td>
      <td>0.375339</td>
      <td>...</td>
      <td>0.260089</td>
      <td>0.766561</td>
      <td>0.041528</td>
      <td>-0.032485</td>
      <td>-0.191705</td>
      <td>1.000000</td>
      <td>-0.197583</td>
      <td>0.668944</td>
      <td>0.864842</td>
      <td>-0.164823</td>
    </tr>
    <tr>
      <th>FG3M/FGM</th>
      <td>0.416975</td>
      <td>-0.056597</td>
      <td>-0.159864</td>
      <td>0.067254</td>
      <td>0.917115</td>
      <td>0.903326</td>
      <td>-0.318734</td>
      <td>-0.425595</td>
      <td>-0.646807</td>
      <td>-0.428657</td>
      <td>...</td>
      <td>0.001675</td>
      <td>-0.551004</td>
      <td>0.561827</td>
      <td>0.417164</td>
      <td>0.985267</td>
      <td>-0.197583</td>
      <td>1.000000</td>
      <td>-0.563588</td>
      <td>0.121024</td>
      <td>0.402158</td>
    </tr>
    <tr>
      <th>FTA/FGM</th>
      <td>-0.257614</td>
      <td>0.090600</td>
      <td>0.044854</td>
      <td>-0.129912</td>
      <td>-0.515179</td>
      <td>-0.518073</td>
      <td>0.628690</td>
      <td>0.736016</td>
      <td>0.475427</td>
      <td>0.374053</td>
      <td>...</td>
      <td>0.109884</td>
      <td>0.461265</td>
      <td>-0.337636</td>
      <td>-0.302442</td>
      <td>-0.573006</td>
      <td>0.668944</td>
      <td>-0.563588</td>
      <td>1.000000</td>
      <td>0.208723</td>
      <td>-0.359261</td>
    </tr>
    <tr>
      <th>TRU%</th>
      <td>0.459798</td>
      <td>0.107527</td>
      <td>0.233979</td>
      <td>-0.044494</td>
      <td>0.175737</td>
      <td>0.123094</td>
      <td>0.186510</td>
      <td>0.157715</td>
      <td>0.155200</td>
      <td>0.239412</td>
      <td>...</td>
      <td>0.269595</td>
      <td>0.693715</td>
      <td>0.261461</td>
      <td>0.163639</td>
      <td>0.135227</td>
      <td>0.864842</td>
      <td>0.121024</td>
      <td>0.208723</td>
      <td>1.000000</td>
      <td>0.023985</td>
    </tr>
    <tr>
      <th>AST_TOV</th>
      <td>0.235780</td>
      <td>0.115425</td>
      <td>-0.085844</td>
      <td>0.017929</td>
      <td>0.354584</td>
      <td>0.358009</td>
      <td>-0.182727</td>
      <td>-0.271229</td>
      <td>-0.549249</td>
      <td>-0.412141</td>
      <td>...</td>
      <td>-0.032942</td>
      <td>-0.274199</td>
      <td>0.303896</td>
      <td>0.303187</td>
      <td>0.414777</td>
      <td>-0.164823</td>
      <td>0.402158</td>
      <td>-0.359261</td>
      <td>0.023985</td>
      <td>1.000000</td>
    </tr>
  </tbody>

</table>
<p>26 rows × 26 columns</p>
</div>

Here's the correlation matrix vizualization: 

![Figure](/assets/images/correlationmatrix.png)

We can see from both the vizulation and the correlation talbe that: 

1. Field goal makes and free throw attempts have a strong, positive linear relationship. This could be because when players are making shots, opposing teams feel it's best to rather foul them. Not only that, but strategies like hack-a-Shaq where players with low FT% but a high FG% will be forced to shoot free throws to reduce the chances of scoring 2 points. 
2. Minutes and points per game have a moderate, positive linear relationship (surprisingly). This is surpring because you would think the correlation would be a bit stronger, considering points is how you win the game. However, this also shows that hustle points such as defense and rebounds play a big part in getting playing time. 
3. Offensive rebounds and blocks have a strong, positive linear relationship. This could be due to the amount of tall players in the center position that get a height advantage in the paint. 
4. Field goal % and offensive rebounds have a strong, positive linear relationship. This could also be due to players such as Rudy Gobert who shoots a minimal amount of shots but also gets a lot of offensive rebounds because of his height and paint presence. 
5. Three point % and three point makes have a moderate, positive linear relationship, whereas field goal % and field goal makes have a very weak, positive linear relationship. This means that there are a lot of players in the NBA that shoot more than they should due to the mass amount of shots being missed.

# Comparing statistics of the top 10 players of each decade
One big trend analysts have seen in the nba is that the 3 point shot has become more involved thanks to Steph Curry and other shooters that have shown dominance in their performances. Not only that, but analysts and media heads have also been talking about how players are "load managing" more often to save their energy for the playofss. Another big thing is that referee rule changes have made it easier to score, hence why efficiency has gone up for players. We can answer these questions using a simple bar graph to compare the top 10 players of each decade. <strong>Note:</strong> These players are ranked based off of the NBA website, calculated by their own algorithm. 

<strong>1. How does 3 point % compare with the top 10 NBA players in each decade?</strong>

<br>

![Figure](/assets/images/average3ptpercentage.png)

Looks like the 3 point percentage between 2010 and 2020 haven't changed much. Lets try something else. 

<br>

<strong>2. How does 3 point field goal makes compare with the top 10 NBA players in each decade?</strong>

<br>

![Figure](/assets/images/average3pm.png)

Look at that! The amount of 3 point shots made per game has nearly doubled in 2020 compared to each decade. This isn't just because of Steph Curry. This is due to the 3 point shot being a huge arsenal for being a top 10 ranked player in the league. 

<br>

<strong>3a. Now, what is the average minutes per game for the top 10 players in each decade?</strong>

<br>

![Figure](/assets/images/top10playersminutes.png)

<br>

<strong>3b. Now what about games played?</strong>

![Figure](/assets/images/top10playersgp.png)

<br>

As we can see here, there is quite a drop off of minutes per game and games per season in each decade, so the analysts may be onto something. This could negatively affect fans that paid hundreds of dollars to see their favorite players play, and could also cause a drop off in revenue. Lets see if this hinders any player statistics. 

<br>

![Figure](/assets/images/top10playersppg.png)

![Figure](/assets/images/top10averageassists.png)

![Figure](/assets/images/top10averagerebounds.png)

<br>

<strong>4. How has efficiency changed for the top 10 ranked players of each decade? [How Efficiency is Calculated](https://captaincalculator.com/sports/basketball/efficiency/)</strong>

<br>

![Figure](/assets/images/top10playerseff.png)

<br>

We can see here that despite playing less minutes and less games, players have actually gotten BETTER throughout each decade. Why is that exactly? This could be due to the evolution of training, increased competition, advancement in analytics, innovative technology, rule changes, and a deeper understanding of the game. In other words, efficiency has taken place in the modern NBA and we may continue to see a rise of competition in NBA talent, if there wasn't enough already. However, is this even a good sign? Have fans become too numb of multiple 30 and 40 point games, to where they may not even find it amusing anymore? According to this visualization, that's not the case: 
![Figure](/assets/images/nbaticketsales.PNG)

So the NBA must be doing something right by making the rules easier for players to score and crank their stats up. In the meantime, we will see if there will be a drop off in NBA ratings and ticket sales in the next decade when players continue to get better and make high volume scoring figures desensitizing. 

# Conclusion
In conclusion, this analysis gives us a comprehensive visual of NBA League Leaders and their statistical performance, offering valuable insights into the variables that could potentially affect a players performance. Analyzing the statistical evolution of top 10 players over time has shown how the game has changed over time and identifies patterns that we can observe in the modern NBA. In this analysis, we have discovered that: 

* The average of every NBA statistic from league leaders  
* Which NBA statistics are correlated with one another
* How the top players in the NBA have changed the game of basketball
* NBA players have learned how to efficiently play the game of basketball at a higher level than ever

If you would like to explore the data further, head to my [streamlit app](https://semesterprojecapp-hrdfz4vc4t7up45unsew7p.streamlit.app/)! 

If you would like to see how these visualizations were created, visit [my repository](https://github.com/agao0224/agao0224.github.io)


