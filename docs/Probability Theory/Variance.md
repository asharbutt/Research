---
layout: default
title: Variance 
parent: Basics
grand_parent: Probability Theory
mathjax: true
permalink: /docs/Probability Theory/Basics/Variance/
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

</div>
