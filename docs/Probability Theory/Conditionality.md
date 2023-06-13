---
layout: default
title: Conditionality
parent: Basics
grand_parent: Probability Theory
mathjax: true
permalink: /docs/Probability Theory/Basics/Conditionality/
nav_order: 5
---
# Conditional Probability
A Conditional Probability P(A|B) means the probability of A occuring given that B has occured, for example probability of a flooding given that it has rained the previous day.

<div class="code-example" markdown="1">
A simple conditional probability formula is given through:

$$Pr(A|B) = \frac{Pr(A\cap B)}{Pr(B)}$$

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

$$E[X|Y = y] = \int_{-\infty}^{\infty} x f_{X,Y}(x|y) dx$$

Which can be re-written as:

$$E[X|Y = y] = \int_{-\infty}^{\infty} x \frac{f(x,y)}{f_Y(y)} dx$$

## Conditional Expectation as a random variable
If we have two random variables, X and Y, and we have the conditional expectation E[X|Y], then we can treat this expectation itself as a function of the random variable Y because it depends on what the value of Y is. We know what values of X can appear given Y, and so this expectation inherits its randomness from the distribution of Y rather than X.

So what is the expectation of this random variable?
$$
E[E[X|Y]] = E[X]
$$

This is because the expectation of X after knowing Y is just the same as what we expect X to be now (This is the law of iterated expectations).

We provide the properties of conditional expectations below:

<div class="code-example" markdown="1">
- Linearity of Conditional expectations - the expectation of two random variables given some set G:
  $$E[aX + bY|G] = aE[X|G] + bE[Y|G]$$

- Taking out what is known -  if X is G-measurable, then:
$$E[XY|G] = XE[Y|G]$$
  <div class="code-example" markdown="1">
- Iterated Conditioning - If a set H contains less information than some set G, then:
$$E[E[X|G]|H] = E[X|H]$$

This also applies to iterating without a second set:
$$E[E[X|Y]] = EX$$

The proof for this is:
$$E[E[X|Y]] = \sum_{y}^{} E[X|Y = y] Pr(Y = y)$$ - Because this is the expectation of the expectation of X given Y, Y is the random variable first, and then we therefore take the expectation with regards to y first. 

$$E[E[X|Y]] = \sum_{y}^{} \sum_{x}^{} x_i Pr(X = x|Y = y) Pr(Y = y)$$ - The expectation of x is summed with respect to x. We note here that $$Pr(X = x|Y = y) Pr(Y = y)$$ through Bayes theorem is the equivalent of  $$Pr(Y = y|X = x) Pr(X = x)$$

We get the following based on this:

$$E[E[X|Y]] = \sum_{y}^{} \sum_{x}^{} x_i Pr(Y = y|X = x) Pr(X = x)$$ 

We can separate these into their respective sums:

$$E[E[X|Y]] = \sum_{y}^{} Pr(Y = y|X = x) \sum_{x}^{} x_iPr(X = x)$$ 

The sum of the conditional probability over all y values will be equal to 1 (as we are summing over the entire probability space for y):

$$E[E[X|Y]] = \sum_{x}^{} x_iPr(X = x)$$

$$E[E[X|Y]] = EX $$
  </div>
</div>

