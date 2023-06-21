---
layout: default
title: Joint Distributions
parent: Basics
grand_parent: Probability Theory
mathjax: true
permalink: /docs/Probability Theory/Basics/Joint Distributions/
nav_order: 6
---

# Joint Probability Distributions
Joint Distributions give the probability of more than one random variable taking on a value at the same time.

We can consider two cases: where the variables are independent, which is a simple case, or where the variables are dependent, in which case we need to also consider their correlations and covariances.

## The Discrete Case
For discrete random variables, the joint probability of (X,Y) is the probability that this takes a value in the sequence of ordered pairs $${x_i, y_i}$$. Thus the joint probability is X = x, Y = y.

The Joint discrete probability mass function fulfils the following two conditions:

1. $$0 \leq p(x_i, y_i) \leq 1$$
2. The total probability is equal to 1, i.e.

$$ \ \sum_{}^{m} \sum_{}^{n} p(x_i, y_i) = 1$$

## The Continious Case
In the continious case, we have a joint pdf which gives us the density of both x and y. Just like in the case of the single continious variable, the joint density of X and Y can be greater than 1, since it only gives the density of the variables, not the probabilities.

The joint pdf has to fulfill the following conditions:

1. $$0 \leq f(x,y)$$
2. The total probability has to be equal to 1:

   $$\int_{a}^{b} \int_{c}^{d} f(x, y) \,dx \,dy = 1$$

## Marginal pdfs
There may be a case where we may want to consider the probability distribution or density function of one variable rather than 2. In this case, we have to integrate out the one we do not want to consider:

$$f_Y(y) = \int_{a}^{b} f(x, y) \,dx$$

$$f_X(x) = \int_{a}^{b} f(x, y) \,dy$$

## Independence and Joint Distributions
It was mentioned previously that 2 variables are independent if their probabilities are independent:

$$P(A \cap B) = P(A)P(B)$$

A more formal definition of independence is:

<div class="code-example" markdown="1">
Two variables are said to be independent if their joint cumulative distributions are a product of the individual cumulative distributions:
   
   $$F(X,Y) = F_X(x)F_Y(y)$$

This means that their joint density is also a product of the individual density functions:

   $$f(x,y) = f_X(x)f_Y(y)$$

This makes checking for independence alot easier as you can see whether the products of the individual variables generate the joint distribution
</div>

## Functions of two continious random variables
According to the law of the unconsious statistician, LOTUS, the expectation of a function on two random variables is given by:

