---
layout: default
title: Universality of Uniforms
parent: Basics
grand_parent: Probability Theory
mathjax: true
nav_order: 7
---
# UoU or Probability Integral transform
We discussed that the CDF of any continious distribution is a function that maps the real line to an interval of [0.1]:

$$F:R \rightarrow [0,1]$$

CDFs can be either increasing or strictly increasing. If the CDF is strictly increasing, then if we plug in any outcome from the random variable associated with the CDF, then we get a cumulative probability (a percentile). And if we repeat this, we get another cumulative probability. But all these outcomes will always be on an interval of [0,1], and the higher the plugged in value, the higher the cumulative probability. This indeed reflects what a uniform distribution is on the interval [0,1].

This means, for any continious random variable with a strictly increasing CDF, plugging in an trial result results in a uniformly distributed value. The inverse is also true, if we take the inverse of the CDF and plug in a value from a uniform distribution on the interval [0,1], then we will get an outcome from the associated random variable.

In a way:

$$F_X(x) \sim U(0,1)$$

$$F_X^{-1}(U) \sim X$$

