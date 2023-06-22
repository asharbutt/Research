---
layout: default
title: Martingales
parent: Stochastic Calculus
mathjax: true
permalink: /docs/Stochastic Calculus/Martingales/
nav_order: 6
---
# Martingales
## Definitions
We first start with some basic definitions:

A **filtration** is a sequence of $$\sigma$$-algebras which contain all the information up till the time of the filtration. This means that each $$\sigma$$-algebra within the sequence will contain as much or more information than the filtration before it.

A **stochastic process** is a sequence of random variables $$X_t$$, and an **adapted process** is a stochastic process which is measurable to its relative filtration i.e $$X_t$$ is $$F_t$$ measurable. 

## Martingales - definition
A martingale is an adapted stochastic process (it is $$F_t$$ measurable) which has an expectation in the future equal to its current value, such that:

$$E[X_t|F_s] = X_s$$

where $$s\leqt$$. This means that the expected value of some adapted stochastic process in the future is equal to what its current value is given all the information currently available.

A **super martingale** is one where the future expected value is less than or equal to its current value:

$$E[X_t|F_s] \leq X_s$$

A **sub-martingale** is a martingale where the future expected value is greater than or equal to its current value:

$$E[X_t|F_s] \geq X_s$$
