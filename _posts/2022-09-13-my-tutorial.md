---
layout: post
title:  "Using R to Calculate Density Probabilities"
date:   2022-09-13
author: Eric Reid
description: A tutorial about calculating probabilities from distributions
image: /assets/images/poisson_distribution.png
---
### Background on Data Distributions

An essential aspect of statistics is understanding the distributions of random variables. If we know how a random variable is distributed, then we can use this information to calculate probabilities of certain events occuring based on the data that has been collected. The statistical software R has many built in packages that work effectively with random variable distributions. In this blog, I will give a couple examples of what this will look like.

### Poisson Distribution

A good way to understand how random variable distributions can translate to calculating probabilities is to use an actual distribution. A common distribution of random variables is called the Poisson Distribution. This distribution deals with discrete variables, which are variables that are finite in nature. Also, these variables are collected in a specified range of time. The only parameter we need for this distribution is lambda which is the mean. An example of this would be in the number of customers entering into a store during a randomly selected hour. we know that the number of people entering has to be a whole number, so x could be 1,2,3...100+. We can assume that the mean is 25. After locking in the distribution of x, we can use statistical arithmetic and R to caluclate probabilities related to different values of x. An example given the customer scenario could look something like this:

What is the probability that 20 people walk into the store during this hour if the mean (lambda) is 25?

R has built in functions that help us easily calculate this. We will use the dpois function to find this probability.
```
# x is the random variable that we chose while lambda is the mean for this distibution.
dpois(x = 20, lambda = 25)
0.05191747
```
