---
layout: post
title:  "Pitching Dominance: Importing data for the best 500 pitching performances"
date:   2022-10-18
author: Eric Reid
description: This blog will show the process for scraping baseball data from Baseball Reference in preparation for futher analysis.
image: /assets/images/wrigleyfield.jpg
---
### Introduction

Baseball is considered to be America's pastime, but in recent years, it has grown into a game with deep international roots. As of the time of this blog post, the MLB playoffs in underway as team compete to be the 2022 World Series Champion and have their names etched in the history books as an ultimate winner. Many a drawn to the game to stand in awe of booming home runs and flashy fielding play, but nothing in baseball can happen until a pitcher throws the ball. 
![pitcher#1](https://user-images.githubusercontent.com/100799679/196492955-b7b60fd3-39ee-4874-9777-eb0b9e275a17.jpg)

Without a clock or timer, baseball relies on pitchers to control the pace and outcomes of each game, and it would not be inappropriate to say that pitchers have the largest impact on the outcome of an individual game, so it is vital to figure out which pitchers are the best in the game. A quick peak at the image below shows the common pitching statistics that are used to judge the performance of a player in an individual game, season, or their entire career. While strike-outs and wins are valuable contributions to our understanding of pitching dominance, an aggregated statistic call Earned Run Average or ERA is the most valuable statistic to note when it coms to deciding pitching excellence. 

![pitching_stats](https://user-images.githubusercontent.com/100799679/196504768-da58d3c5-07c9-4d13-8154-ed324b1f0771.jpg)

### ERA

ERA is a statistic calculated by taking the total number of Earned Runs (which are runs scored excluding those that are the result of errors) and averaging them over 9 innings. If a pitcher pitched 18 innings and gave up 2 runs, then he would have an ERA of 1.00, but if a pitcher were to give up 5 earned runs during one inning pitched, then he would have an ERA of 45.00. The lower the ERA the better. Over an entire career, the pitcher with the lowest ERA was Ed Walsh who had a career ERA of 1.816, so if he pitched a full 9 inning game, it would be expected for him to give up less than 2 earned runs. 

### Data

For this assignment, I found a dataset on the website Baseball Reference that has the 500 greatest pitching seasons based on ERA. The first row has the lowest value of ERA and it slowly rises as I looked through the data. Along with the player and era for the individual season, there was also data related to the age of the player when they had the season, the year of the season, the number of innings pitched, and which hand the pitcher throws with. As I looked through this data, I saw some aspect that could use some more analysis, whether it was the wide range of innings ptched for the people found on this list, or the overwhelming number of pitchers whose career seasons happened prior to the end of the Second World War. I decided to take this data and create a dataframe that could be used for futher analysis at a later step.



[ERA Github Repository](https://github.com/erictreid514/baseball_era)
