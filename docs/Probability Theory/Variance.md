---
layout: default
title: Variance and Covariance
parent: Basics
grand_parent: Probability Theory
mathjax: true
permalink: /docs/Probability Theory/Basics/Variance and Covariance/
---

# Variance - An Introduction
Whilst the mean gives us an idea of the centre of location of the distribution, we need some measure of the spread around that mean value. One of the simple methods is the variance of the distribution. 

In simple terms, the variance is defined as:

$$Var(X) = E[(X - EX)^2]$$

We can rewrite this as the following (through expanding the brackets):

$$Var(X) = EX^2 - (EX)^2$$

Variance has the following properties which can be used to calculate and/or scale other random variables:

<div class="code-example" markdown="1">
- Constants: $$Var(aX) = a^2Var(X)$$ - this can be used when looking to scale a random variable: we create another random variable with the desired expectation/variance, and then we look at what constant we would need to multiply our original variable by to scale it to match the new variance. Example: We know the increments of a Brownian motion are normally distributed with mean 0 and variance of dt. How can we simulate this? We can start with a standard normal random variable X such that:

$$X \sim N(0,1)$$

How do we scale this into a brownian motion? We know that we need to multiply it by something in order for it to become Brownian, and so do the following:

$$Var(kX) = dt$$

$$k^2Var(X) = dt$$

Because Var(X) is 1 (as X is standard normally distributed), then:

$$k^2 = dt$$

$$k = \sqrt{dt}$$

So we need to multiply the variable X, or the standard normal distribution by $$\sqrt{dt}$$ in order to get a Brownian motion increment.

- Additivity of Variance (Independent Variables): If X and Y are independent random variables, then the sum of their variances can be written as:

Var(X + Y) = Var(X) + Var(Y)

- Additivity of Variance (Dependent Variables): If X and Y are dependent variables, then their sum of variances is given by:

Var(X + Y) = Var(X) + Var(Y) + 2abCov(X,Y)
</div>

## Covariance
Covariance is a meaure of how two variables vary together - whilst Variance tells you how a single variable varies, the covariance provides details about how two variables move together. It is given by:

$$Cov(X,Y) = E[(X - EX)(Y - EY)]$$

For some constants a,b,c,d and random variables U,V,Y,Z, the covariance between the sums is the breakdown of each pair, given as follows:

$$Cov(aU + bV, cY + dZ) = acCov(U,Y) + adCov(U,Z) + bcCov(V,Y) + bdCov(V,Z)$$


Given that the covariance describes how two variables move together, we can interpret is as the strength of relationship between two variables: the higher the cov(), the stronger the relationship. It is important to note that covariances cannot be compared accross datasets with different measurements/units. 

The issue with interpreting the covariacne result is that if X and Y values are large, the covariance value will also be large - then how do you know whether the relationship between two variables is strong or not?

## Correlation Coefficient
Because the covariance figure makes it hard see how strongly two variables are related, we standardise the covariance result by dividing by the two standard deviations of the variables to get a Pearson Correlation Coefficient:

$$\rho = \frac{Cov(X,Y)}{\sqrt{Var(X)Var(Y)}}$$

This gives us a standardised result between -1 and 1, providing us with an interpretation of how strong the result is.

An issue with this is that this coefficient only measures linear relationships - if a higher order relationship is present, this will not be able to pick it up.

An Important note is that the Variance of a random variable is not well defined unless it has a finite expectation, i.e $$EX < \infty$$. The same applies to correlation - two random variables do not have a well defined correlation unless their individual variances are finite (thus meaning their expectations are finite).
