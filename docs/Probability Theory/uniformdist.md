---
layout: default
title: Uniform Distribution
parent: Continious Distributions
grand_parent: Probability Theory
permalink: /docs/Probability Theory/Distributions/Gaussian Distribution/
nav_order: 1
---
# Uniform Distribution
A uniform distribution is any rectangular distribution ditributed with X $\sim$ U(a,b) where a and b are interval end points. Recall that for a discrete uniform disitribution, i.e. one where all outcomes have an equal probability, the probability is 1/number of outcomes.

The same applies for this distribution. The probability density function can be given by:

$$f_X(x) = \frac{1}{b-a}$$ if $$a \leq x \leq b$$

Thus the CDF can be given through the integral:

```math

F_X(x) = \int_{a}^{x} f_X(x)dx

F_X(x) = \int_{a}^{x} \frac{1}{b-a}dx

F_X(x) = \prescript{a}{x}[ \frac{x}{b-a}] 

F_X(x) = \frac{x - a}{b-a}
```
## Expectation
The expectation can be calculated through:
```math
E[X] = \int_{a}^{b} x f_X(x)dx

E[X] = \int_{a}^{b} \frac{x}{b-a}dx

E[X] =  \prescript{a}{b}[\frac{x^2}{2(b-a)}]

E[X] =  \frac{b^2 - a^2}{2(b-a)}]

E[X] =  \frac{(b-a)(b+a)}{2(b-a)}]

E[X] =  \frac{(b+a)}{2}]
```
