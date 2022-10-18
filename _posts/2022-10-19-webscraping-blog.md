---
layout: post
title:  "Pitching Dominance: Importing data for the best 500 pitching performances"
date:   2022-10-18
author: Eric Reid
description: This blog will show the process for scraping baseball data from Baseball Reference in preparation for futher analysis.
image: /assets/images/wrigleyfield.jpg
---
### Introduction

Baseball is considered to be America's pastime, but in recent years, it has grown into a game with deep international roots. As of the time of this blog post, the MLB playoffs are underway as teams compete to be the 2022 World Series Champion and have their names etched in the history books as an ultimate winner. Many are drawn to the game to stand in awe of booming home runs and flashy fielding play, but nothing in baseball can happen until a pitcher throws the ball. 
![pitcher#1](https://user-images.githubusercontent.com/100799679/196492955-b7b60fd3-39ee-4874-9777-eb0b9e275a17.jpg)

Without a clock or timer, baseball relies on pitchers to control the pace and outcomes of each game, and it would not be inappropriate to say that pitchers have the largest impact on the outcome of an individual game, so it is vital to figure out which pitchers are the best in the game. A quick peek at the image below shows the common pitching statistics that are used to judge the performance of a player in an individual game, season, or their entire career. While strike-outs and wins are valuable contributions to our understanding of pitching dominance, an aggregated statistic called Earned Run Average or ERA is the most valuable statistic to note when it comes to deciding pitching excellence. 

![pitching_stats](https://user-images.githubusercontent.com/100799679/196504768-da58d3c5-07c9-4d13-8154-ed324b1f0771.jpg)

### ERA

ERA is a statistic calculated by taking the total number of Earned Runs (which are runs scored excluding those that are the result of errors) and averaging them over 9 innings. If a pitcher pitched 18 innings and gave up 2 runs, then he would have an ERA of 1.00, but if a pitcher were to give up 5 earned runs during one inning pitched, then he would have an ERA of 45.00. The lower the ERA the better. Over an entire career, the pitcher with the lowest ERA was Ed Walsh who had a career ERA of 1.816, so if he pitched a full 9 inning game, it would be expected for him to give up less than 2 earned runs. 
![Walsh-Ed-2083-89](https://user-images.githubusercontent.com/100799679/196507495-fa76ce85-3dbe-4969-bcab-0421f0d9bc0b.jpg)

### Data

For this assignment, I found a dataset on the website Baseball Reference that has the 500 greatest pitching seasons based on ERA. The first row has the lowest value of ERA and it slowly rises as I look through the data. Along with the player and era for the individual season, there was also data related to the age of the player when they had the season, the year of the season, the number of innings pitched, and which hand the pitcher threw with. As I looked through this data, I saw some aspects that could use some more analysis, whether it was the wide range of innings pitched for the people found on this list, or the overwhelming number of pitchers whose career seasons happened prior to the end of the Second World War. I decided to take this data and create a dataframe that could be used for further analysis at a later step.

![era](https://user-images.githubusercontent.com/100799679/196507717-df5ea449-8bc3-4947-a542-b99e163fba61.jpg)

### Scraping the Data

To get this data from the web into python, we can use a variety of methods. Fortunately, the python package Pandas has a convenient builtiin function pd.read_html() to take tables from a website and move them into python so they can be turned into a dataframe. The challenge with web scraping is the legal element of web scraping. Sometimes data has been copyrighted or protected in another way, so before we can scrape the data, we need to check if it is ok to scrape the data. Using the 'requests' package, we gain access to a function called status_code that will let us know if the data is ok to use. If the function returns a value of 200, then we are good to go. The code can look something like this,

```
url = 'https://www.baseball-reference.com/leaders/earned_run_avg_season.shtml'
r = requests.get(url)
r.status_code
```
After running this code we received the value 200, which is what we hoped it would be.
![status](https://user-images.githubusercontent.com/100799679/196509341-ff6f2658-aa3f-4abe-94f8-86f3fcb20714.jpg)

Now that we know that the data is eligible to be scraped, we can go ahead and use the pd.read_html() function to select the tables from the website. This function will create a list of tables if there is more than one, so we will want to use a simple command to select the first table as our dataset of interest.
```
dfs = pd.read_html(url)
era = dfs[0]
```
With those 2 simple steps, we have scraped the data from the Baseball Reference website! Now we can spend some time cleaning the data and preparing it for future analysis.

![firstera](https://user-images.githubusercontent.com/100799679/196510196-cbde56dd-80c6-42ae-b5a1-024175de7bb1.jpg)

### Cleaning the Data

A challenge with using data from a website is that it often comes in a form that needs to be cleaned. Sometimes there are missing values and it is common for the variables to be imported as an object or string rather than an integer or float. Depending on the type of analysis desired, the data can be cleaned in a variety of ways. I won't go into detail on how I cleaned this dataset, but I did spend some time removing unnecessary rows and changing the numerical columns from strings to numbers. I also added a new column extracting the age of the player from the 'Player' column and created a new column with the age of the player during that season. Columns and rows could either be added or removed during this process. If you are interested in seeing what steps I took in cleaning the data, or if you are interested in seeing what the dataset ended up becoming, you can find it here, [ERA Github Repository](https://github.com/erictreid514/baseball_era)

### Conclusion

Collecting the data is only the first step in the analysis of this data. As you look through this data, there may be some trends that you find interesting. You may notice some trends related to the ages of the pitchers, or the handedness of the pitchers as it relates to their season era. These are things that we can look at further if we spend some time performing a variety of exploratory data analysis processes. With this in mind, please continue to check in on this blog to see when I analyze the data and see if I can figure out why the older pitchers seem to have a much lower ERA than contemporary players and some other things as well!
