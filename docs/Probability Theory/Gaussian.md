---
layout: default
title: Gaussian Distribution
parent: Continious Distributions
grand_parent: Probability Theory
permalink: /docs/Probability Theory/Distributions/Gaussian Distribution/
---

# The Gaussian Distribution
The most widely used distribution accross all fields, also known as the bell curve, the Gaussian, or Standard Normal distribution is given by a symmetrical bell shaped continious distribution. 

## Gaussian Function
We start with the base function called the Gaussian function, named after German Mathematician Gauss. The base function is in the form of:

$$f(x) = e^{-x^2}$$

The parametric form of this base function is given by:

$$f(x) = ae^{-\frac{(x-b)^2}{2c}}$$

where a and b are constants and c is a non-zero constant. This function produces a symmetrical bell curve, known as a Gaussian curve. The area produced by the standard Gaussian function is $$\sqrt{\pi}$$, whilst the parametric form of the function has an area of $$c\sqrt{2\pi}$$.

### Normalizing factor
For all probability distribution functions, we need to ensure that the total area underneath the density function is equal to 1, as in the integral, or total probability of the entire curve has to be 1 (recall that a density function necessarily does not need to always be less than 1 since it represents density). 

To convert a probability function to a probability density, we multiply by a normalizing factor, which normalizes the entire function area to 1. This is important when calculating probabilities. 

Since the area of a Gaussian parametric function is $$c\sqrt{2\pi}$$, we normalize the Gaussian function by dividing it:

$$\phi(x) = \frac{1}{c\sqrt{2\pi}}e^{-\frac{(x - b)^2}{2c}}$$

We already know that b is the mean and c is the standard deviation of the distribution.

## Normal PDF
The density function of the normal distribution (the function that assigns a probability density to an infinitely small interval on the distribution) is given by:

$$f(x) = \frac{1}{\sigma \sqrt{2\pi}} e^{-\frac{(x - \mu)^2}{2\sigma^2}}$$

An important note of this function is that the density function assigns a density to the value x, not a probability. This means that for a given interval, the density assigned to a value x can be greater than 1.

What is important is that when we integrate, which is how we find the probability of a value, the integral is equal to 1 if we integrate over the entire real line.

The $$\frac{1}{\sigma \sqrt{2\pi}}$$ makes sure that the integral equals 1 over R. This is different when compareed to probability mass functions, which assign an actual probability mass to a value x. 
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

Take out the $$\frac{1}{\sigma \sqrt{2\pi}}$$ as it is a constant and remove $$\sigma^2$$ since it is 1, as well as the mean:

$$EX =  \frac{1}{\sqrt{2\pi}}(\int_{-\infty}^{0} x e^{-\frac{(x)^2}{2}} \,dx +  \int_{0}^{\infty} x e^{-\frac{(x)^2}{2}} \,dx)$$

The integral of $$x e^{-\frac{-1}{2}x}$$ is given through substitution method, and equals:

$$EX =  \frac{1}{\sqrt{2\pi}} ( [-e^{-\frac{(x)^2}{2}}] \biggl|_ {-\infty}^0 + [-e^{-\frac{(x)^2}{2}}] \biggl|_{0}^{\infty})$$

We know that $$e^x$$ where $$x = \infty$$ will equal 0, and so:

$$EX = \frac{1}{\sqrt{2\pi}}[(-1 + 0) + (0 - -1)]$$

$$EX = 0$$

## Calculating CDF
The CDF is the collection of probabilities up to a limit. For continious distributions, the CDF is given by the integral of the pdf:

$$P( X \leq a) = \int_{-\infty}^{a} \frac{1}{\sigma \sqrt{2\pi}} e^{-\frac{(x - \mu)^2}{2\sigma^2}} \,dx $$

Just like the above, the probability of an interval can be given by:


$$P(a \geq X \leq b) = \int_{a}^{b} \frac{1}{\sigma \sqrt{2\pi}} e^{-\frac{(x - \mu)^2}{2\sigma^2}} \,dx $$

The general CDF of any distribution (continious) will be the integral of the density function from the lowest limit (in the Gaussian case, $$- \infty$$) to the upper limit which will be x. This can be shown in the following example:

$$F(x) = \int_{-\infty}^{x} \frac{1}{\sigma \sqrt{2\pi}} e^{-\frac{(x - \mu)^2}{2\sigma^2}} \,dx $$

This is because CDF just calculates the cumulative probability up to the upper limit, meaning the total, thus meaning it is a absolute continious and increasing function, with F(Max upper limit) = 1

## Other details
Suppose that X and Y are two independent normal random variables with $$X \sim N(\mu_1, \sigma_1^2)$$ and $$Y \sim N(\mu_2, \sigma^2_2)$$. Then,

1. $$X + Y \sim N(\mu_1 + \mu_2, \sigma_1^2 + \sigma_2^2)$$
2. $$aX \sim N(a\mu_1, a^2 \sigma_1^2)$$

This can be proved through their moment generating functions i.e deriving $$E[e^{\theta (X+Y)}], E[e^{\theta (aX)}]$$

