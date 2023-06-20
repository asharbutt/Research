---
layout: default
title: Properties of Expectations
parent: Basics
grand_parent: Probability Theory
mathjax: true
permalink: /docs/Probability Theory/Basics/ExpectationsProperties/
nav_order: 1
---
# Properties of Expectations
## Expectations of functions of random variables
If we have some function of two random variables g(x,y), then the expectation of this function will be given by:

$$Eg(x,y) = \sum_{}^{} g(x,y)f(x,y)$$

where f(x,y) is the joint probability mass function for the two random variables. If the variables are continious, then:

$$Eg(x,y) = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} g(x,y)f(x,y) \,dx \,dy $$

## Conditional expectation
The conditional expectation E[X|Y] follows an important rule using the iterated conditioning law:

$$EX = E[E[X|Y]]$$

Through iteration, this means that E[X|Y] is a random variable in itself, and therefore can be computed using the previous expectation rules. This is because if we assume that E[X|Y] is a random variable, then E[X|Y = y] is one of the outcomes of this random variables. 
For discrete variables:

$$EX = \sum_{y}^{} E[X|Y = y]P(Y = y)$$

This essentially means that if we sum over all the outcomes of y and multiply by their probabilities, then we should be left with just the expectation of X on its own.

In the case of a continious variable:

$$EX = \int_{-\infty}^{\infty} E[X|Y = y]p_Y(y) \,dy$$

## Conditional Variance
Just like the conditional expectation of X given Y, we can also define the conditional variance of X given Y = y:

$$Var(X|Y) = E[(X - E[X|Y])^2|Y]

We can expand this just like the original variance equation:

$$Var(X|Y) = E[X^2|Y] - E[X|Y]^2$$


