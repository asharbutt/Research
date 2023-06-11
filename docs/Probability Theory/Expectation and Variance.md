---
layout: default
title: Expectation and Variance
parent: Basics
grand_parent: Probability Theory
mathjax: true
permalink: /docs/Probability Theory/Basics/Expectation And Variance/
---

# Expectation - Introduction
Let X be a random variable on a probability space ($$\Omega$$, $$\digamma$$, P). We are interested to know what the average value X may take over a range of experiments given the probability of each of those outcomes. 

When $$\Omega$$ is finite and discrete (countable), then this is simple:

$$EX =  \ \sum_{w \in \Omega}^{} P(w)X(w) \]$$

If $$\Omega$$ is infinite but still countable, then we can compute the expectation as:

$$EX =  \ \sum_{w \in \Omega}^{\infty} P(w)X(w) \]$$

In the case that $$\Omega$$ is uncountable and infinite, then we need to use integration instead in order to compute the expectation. 
When considering intergrals, we have two options: The Riemann Integral and the Lebesgue Integral. The Riemann is the most widely used integral method, consered mainly in calculus. However, an issue with Riemann is that it is composed as of the following:

$$EX =  \int_{a}^{b} f(x) \,dx \]$$

The issue with this is that $$X(\omega)$$ is a function of $$(\omega)$$, the event outcome, and the event outcome is a subset of the measurable space, $$\Omega$$. The measurable space may be abstract, as is often the case in probability and thus is not a subset of the real line, meaning it becomes difficult to use the Riemann Integral in this case. How do we partition the probability space such that it can be represented on the real line?

This is where the Lebesgue Integral comes in with the following representation:

$$EX =  \int_{\Omega}^{} X(\omega) \,dP(\omega) \]$$

We instead look to integrate the random variable, the function of the events with respect to the probability of those events. This involves partitioning the probabiltiy distribution of each outcome of the random variable, thus allowing us to be able to integrate. 

Under the Lebesgue Integral, we can now define some properties of Expectations:

1. If X takes a finite number of values (countable), then the expectation can be defined as a sum:

$$EX =  \ \sum_{k=1}^{n} x_k P{X = x_k} \]$$

In case $$\Omega$$ is infinite but countable, then:

$$EX =  \ \sum_{k=1}^{\infty} x_k P{X = x_k} \]$$

2. Integrability: X is only integrable if and only if the modulus expectation is finite:

$$E|X| < \infty$$

3. Comparison: If X $$\leq$$ Y and are integrable and non-negative surely, then:
```math
EX $$\leq$$ EY
```
A particular result from this is that if X = Y almost surely (with probability 1), and one of them is almost surely non-negative or integrable, then both of them are non-negative and/or integrable, and:
```math
EX = EY
```
