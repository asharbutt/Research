---
layout: default
title: Martingales
parent: Stochastic Calculus
mathjax: true
permalink: /docs/Stochastic Calculus/Martingales/
nav_order: 2
---
# Martingales
## Definitions
We first start with some basic definitions:

A **filtration** is a sequence of $$\sigma$$-algebras which contain all the information up till the time of the filtration. This means that each $$\sigma$$-algebra within the sequence will contain as much or more information than the filtration before it.

A **stochastic process** is a sequence of random variables $$X_t$$, and an **adapted process** is a stochastic process which is measurable to its relative filtration i.e $$X_t$$ is $$F_t$$ measurable. 

## Martingales - Definitions
A martingale is an adapted stochastic process (it is $$F_t$$ measurable) which has an expectation in the future equal to its current value, such that:

$$E[X_t|F_s] = X_s$$

where $$s\leq$$. This means that the expected value of some adapted stochastic process in the future is equal to what its current value is given all the information currently available.

A **super martingale** is one where the future expected value is less than or equal to its current value:

$$E[X_t|F_s] \leq X_s$$

A **sub-martingale** is a martingale where the future expected value is greater than or equal to its current value:

$$E[X_t|F_s] \geq X_s$$

## Stopping Times
A stopping time is some event that occurs which is known to have occured if it is within the filtration. A more formal definition is that the stopping time is some event/random variable T in the same observable space $$\Omega$$ as our stochastic process, such that $$X_T = X_s$$ if our stochastic process is $$X = {X_s: s\geq 0}$$. T will be the stopping time when the stochastic process $$X_s$$ stops based on all the information we know up until that time, meaning that the stopping time will then be $$F_s$$-measurable.

Given that T is a stopping time as soon as it becomes $$F_t$$ measureable, we will not know when T occurs if $$t \geq s$$ where s is the current time.

Two very simple examples of a stopping time are:

1. Assume we are gambling, and $$X_n$$ gives us the amount of money we have after time n. The stopping time $$\tau = n$$ is a rule which can only be achieved when we have all the information we need to know in order to fulfil the rule i.e. we stop gambling after we have made a certain amount of money. We do not know how much money we have until after we have placed a bet and gotten our earnings, and the total money equals the required amount to stop. This means that the stopping time is dependent on how much information we have, and we do not have enough information to determine that we need to stop up until the point we do, meaning it is not predictable.
2. We have a stock, and $$X_n$$ is the random variable that represents the stock value. Our decision to buy and sell at a set price depends on what the price is at the time, thus all the information available at the time. We cannot predict this, and can only determine this based on the current filtration.

### Martingales and Stopping times
A variable $$M_t$$ is a martingale if:

$$E[M_T] = E[M_0] for all stopping times T$$

In order words, if T is a stopping time i.e. a time of interest where a random event happens, then M is a martingale if the expectation of the variable at any stopping time is equal to the expectation of the initial value. 

## Hitting time
The hitting time is the first time a stochastic process will **hit** a certain value or a certain subset of the state space, also known as the first passage time. 
