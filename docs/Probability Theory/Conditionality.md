---
layout: default
title: Conditionality
parent: Basics
grand_parent: Probability Theory
mathjax: true
permalink: /docs/Probability Theory/Basics/Conditionality/
---
# Conditional Probability
A Conditional Probability P(A|B) means the probability of A occuring given that B has occured, for example probability of a flooding given that it has rained the previous day.

<div class="code-example" markdown="1">
A simple conditional probability formula is given through:

$$Pr(A|B) = \frac{Pr(A\capB)}{Pr(B)}$$

In terms of random variables, we can re-write this as:

$$Pr(X = x|Y = y) = \frac{Pr(X = x \cap Y = y)}{Pr(Y = y)}$$

Bayes theorem further extends this by showing:

$$Pr(X = x|Y = y) = \frac{Pr(Y = y|X = x)Pr(X = x)}{Pr(Y = y)}$$

This is a simple substitution into the same formula, replacing $$Pr(X = x \cap Y = y)$$ with a re-arranged version.
Another way to write the probability of X = x given Y = y is:

$$p_{X,Y}(x|y) = Pr(X = x| Y = y)$$
</div>

Constructing a conditional probability space is normally a 2-stage process. We first sample Y from its relevant marginal distribution and obtain Y - y. We then sample X from its marginal distribution given that Y = y.

## Conditional Expectation
What does E[X|Y = y] mean? It means the expected value of X given that Y = y. For discrete, we can define the formula as:

$$E[X|Y = y] = \sum_{i = 1}^{n} x_i Pr(X = x_i|Y = y)$$

Where the probability can be worked out using the conditional probability method or Bayes theorem.

In a continious setting, the conditional density is given by the conditional formula:

$$f_{X,Y}(x|y) = \frac{f(x,y)}{f_Y(y)}$$

Thus, given the conditional density, the continious expectation can be calculated as:

$$E[X|Y = y] = \int_{-\infty}^{\infty} x f_{X,Y}(x|y) ,\dx$$

Which can be re-written as:

$$E[X|Y = y] = \int_{-\infty}^{\infty} x \frac{f(x,y)}{f_Y(y)} ,\dx$$

