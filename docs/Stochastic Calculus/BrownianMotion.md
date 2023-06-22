---
layout: default
title: Brownian Motion
parent: Stochastic Calculus
mathjax: true
permalink: /docs/Stochastic Calculus/Brownian Motion/
nav_order: 1
---
# Brownian Motion
## Symmetrical Random Walk
We start with a symmetrical random walk - suppose we have a coin tossing experiment, where $$X_t$$ can be either 1 or -1. This is symmetrical because the results are evenly distributed. We define the value of our random walk using:

$$M(t) = \sum_{j=0}^{t} X_j$$

Such that the value of our path is the sum of the random variable outcomes till t. We note important characteristics of the increments of the random walk:

1. $$E[M(t) - M(s)] = 0$$ - this is because we either get +1 or -1 with probability of 0.5, thus leading to an expectation of 0
2. The variance of the increment is equal to the difference in time i.e Var(M(t) - M(s)) = t - s

This random walk is also a martingale:

1. E[M(t)|F(s)] = E[(M(t) - M(s)) + M(s)| F(s)] <- the value at M(t) is equal to the increment from s to t plus the value at t
2. E[M(t)|F(s)] = E[(M(t) - M(s)|F(s)] + E[M(s)|F(s)] <- we can split the expectation through linearity property
3. E[M(t)|F(s)] = E[(M(t) - M(s)|F(s)] + M(s) <- M(s) is F(s) measurable - we already know the value at time s
4. E[M(t)|F(s)] = E[(M(t) - M(s)] + M(s) <- The value of the increments are independent, thus not measurable with regards to the filtration
5. E[M(t)|F(s)] = M(s) <- The expectation of the increment is 0, thus the expectation of a symmetrical random walk given a prior filtration is equal to the prior value

