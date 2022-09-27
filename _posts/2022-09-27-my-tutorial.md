---
layout: post
title:  "Using R to Predict the Future with Probability Distributions"
date:   2022-09-27
author: Eric Reid
description: A tutorial about using R to calculate probabilities based on random variables
image: /assets/images/poisson_distribution.png
---
No matter where you are in society, you are destined to come across statistics. Often, you'll see this in political campaigns as there are discussions on approval ratings and tax rates. You may also see them when watching a sporting event. Many of these statistics deal with things that have already happened, but an integral aspect of statistics is using the past to try and predict the future. If you've wondered if you can predict what the next card in a deck will be before laying down a large bet at the black-jack table, or if you are wondering what color eyes your future nieces and nephews will have, then you have to learn about how probabilities for these events can be calculated. Fortunately, statistical software like R, can make this process much simpler than you may think possible now.

### Background on Data Distributions

An essential aspect of statistics is understanding the distributions of random variables. If we know how a random variable is distributed, then we can use this information to calculate probabilities of certain events occurring based on the data that has been collected. The statistical software R has many built in packages that work effectively with random variable distributions. In this blog, I will give a couple examples of what this will look like.

### Using R to calculate distributions
Inside of R, there are multiple functions for almost every distribution that we can use to calculate probabilities, densities, and quantiles among other options as well. For many standard distributions, it is not required to install special packages in order to get access to the functions mentioned earlier. Most of these functions look and function very similarly. When asked to calculate the height of the density function at a certain value x, which translates to a probability at a certain point, or in statistical notation: P(X = x), you type in a function that looks like this: ddistribution_name(x,parameters). Some examples of this would be the binomial distribution, dbinom(x,n, theta); the Poisson Distribution, dpois(x, lamdba); and the beta distribution, dbeta(x,alpha, beta). Calculating the cumulative density function is like calculating probabilities over a range like P(x < X), we use the same notiona as the densities but we replace the "d" with a "p". SO those above functions would become pbinom(x,n,theta), ppois(x,lambda) and pbeta(x,alpha, beta). To learn more about some of the basic functions, you can go to this link: [Basic Probabilities Distributions](https://www.cyclismo.org/tutorial/R/probability.html).

### Poisson Distribution

A good way to understand how random variable distributions can translate to calculating probabilities is to use an actual distribution. A common distribution of random variables is called the Poisson Distribution. This distribution deals with discrete variables, which are variables that are finite in nature. Also, these variables are collected in a specified range of time. Below is a an example graph of the Poisson distribution. You can see that the curve is not a line, but rather many open circles which shows that it is a discrete variable instead of a continuous one.

![Poisson_Plot](https://user-images.githubusercontent.com/100799679/192354611-34233a5f-a1a6-4cf4-bcd0-41b0bfccb1dd.jpeg)

The only parameter we need for this distribution is lambda which is the mean. An example of this would be in the number of customers entering into a store during a randomly selected hour. we know that the number of people entering has to be a whole number, so x could be 1,2,3...100+. We can assume that the mean is 25. After locking in the distribution of x, we can use statistical arithmetic and R to calculate probabilities related to different values of x. An example given the customer scenario could look something like this:

What is the probability that 20 people walk into the store during this hour if the mean (lambda) is 25?

R has built in functions that help us easily calculate this. We will use the dpois function to find this probability.
```
# x is the random variable that we chose while lambda is the mean for this distribution.
dpois(x = 20, lambda = 25)
0.05191747
```
Another example would be something like this: What is the probability that less than 20 people walk into the store during this hour if lambda is 25?

For this example we would use the ppois function.
```
ppois(19, lambda = 25)
0.1335748
```

This is a simple example, but it can be used in more situations than just trying to figure out how many customers walk into a store. You could use R to calculate the probability of drawing a spade from a deck of cards using the binomial distribution functions. If you know how a variable is distributed, then the powers of interpretation and prediction can guide you to make an estimated guess on what can happen. If you have any experience using these functions, please leave a comment with any advice that you have. If you have an idea of something you would like to see if it could be predicted using these functions, also feel free to post your ideas below!
