---
layout: default
title: Gaussian Distribution
parent: Continious Distributions
grand_parent: Probability Theory
permalink: /docs/Probability Theory/Distributions/Gaussian Distribution/
---

# The Gaussian Distribution
The most widely used distribution accross all fields, also known as the bell curve, the Gaussian, or Standard Normal distribution is given bya symmetrical bell shaped continious distribution. 

The density function of the normal distribution (the function that assigns a probability mass to an infinitely small interval on the distribution) is given by:

$$f(x) = \frac{1}{\sigma \sqrt{2\pi}} e^{-\frac{(x - \mu)^2}{2\sigma^2}}$$

## Expectation of a Gaussian variable

In order to find the exepctation of a normal random variable, recall that under the discrete setting, we use:

$$EX =  \ \sum_{}^{} P(w)X(w) $$

In the case of a continious variable, the probability of the variable X is given by the density function of X. Furthermore, given the variable is continious, we cannot sum over an uncountable and infinite set, and thus we use integrals instead. Therefore, we get:

$$EX =  \int_{-\infty}^{+\infty} xf(x) \,dx $$

where f(x) is the density function. In the normal variable case, we get:

$$EX =  \int_{-\infty}^{+\infty} x \frac{1}{\sigma \sqrt{2\pi}} e^{-\frac{(x - \mu)^2}{2\sigma^2}} \,dx $$

## Proof of mean of a standard normal variable
The expectation of a standard normal variable, where $$\mu = 0$$ and $$\sigma^2 = 1$$ is 0. The proof is below:

$$EX =  \int_{-\infty}^{+\infty} x \frac{1}{\sigma \sqrt{2\pi}} e^{-\frac{(x - \mu)^2}{2\sigma^2}} \,dx $$

We can split this up into two integrals through the linearity of expectations with half the area because the Gaussian distribution is symmetrical around the mean:

$$EX =  \int_{-\infty}^{0} x \frac{1}{\sigma \sqrt{2\pi}} e^{-\frac{(x - \mu)^2}{2\sigma^2}} \,dx +  \int_{0}^{\infty} x \frac{1}{\sigma \sqrt{2\pi}} e^{-\frac{(x - \mu)^2}{2\sigma^2}} \,dx$$

Take out the $$\frac{1}{\sigma^2 \sqrt{2\pi}}$$ as it is a constant and remove $$\sigma^2$$ since it is 1, as well as the mean:

$$EX =  \frac{1}{\sqrt{2\pi}}(\int_{-\infty}^{0} x e^{-\frac{(x)^2}{2}} \,dx +  \int_{0}^{\infty} x e^{-\frac{(x)^2}{2}} \,dx)$$

The integral of $$x e^{-\frac{-1}{2}x}$$ is given through substitution method, and equals:

$$EX =  \frac{1}{\sqrt{2\pi}}([-e^{-\frac{(x)^2}{2}}]\biggl|_{-\infty}^0 + [-e^{-\frac{(x)^2}{2}}]\biggl|_{0}^{\infty})$$

We know that $$e^x$$ where $$x = \infty$$ will equal 0, and so:

$$EX = \frac{1}{\sqrt{2\pi}}[(-1 + 0) + (0 - -1)]$$

$$EX = 0$$

## Calculating CDF
The CDF is the collection of probabilities up to a limit. For continious distributions, the CDF is given by the integral of the pdf:

$$P( x \leq a) = \int_{-\infty}^{a} x \frac{1}{\sigma \sqrt{2\pi}} e^{-\frac{(x - \mu)^2}{2\sigma^2}} \,dx $$

Just like the above, the probability of an interval can be given by:


$$P(a \geq x \leq b) = \int_{a}^{b} x \frac{1}{\sigma \sqrt{2\pi}} e^{-\frac{(x - \mu)^2}{2\sigma^2}} \,dx $$
