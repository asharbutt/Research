---
layout: default
title: Chebyshev's Inequality
parent: Basics
grand_parent: Probability Theory
mathjax: true
nav_order: 12
---
# Chebyshev's Inequality
If we do not know the exact parameters needed to calculate the probability of a random variable taking a certain value, we can calculate upper (and lower) bounds to what the probability may be.

If we know the mean and standard deviation of a random variable, then the probability that the random variable will take a value outside of **k** standard deviations is given by the upper bound:

$P(|X-\mu| \geq k\sigma^2) \leq \frac{1}{k^2}$

If we wanted to know the probability that X will fall inside **k** standard deviations, then we would do the reverse:

$P(|X-\mu| \leq k\sigma^2) \geq 1 - \frac{1}{k^2}$
