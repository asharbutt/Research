---
layout: default
title: Multiple Ito Processes
parent: Stochastic Calculus
mathjax: true
nav_order: 7
---
# Multiple Ito Processes
It is quite common to have more than one Ito Process involved. For example, take the following two:

$$dX(t) = \mu_x (t)dt + \sigma_x (t)dW_x$$

$$dY(t) = \mu_y (t)dt + \sigma_y (t)dW_y$$

The relationship between the two brownian motions with mean 0 and variance t can be described using the correlation and covariance. There exists some function $$\rho$$ such that the covariance between the two brownian motions can be described using the following:

$$E_t \int_{}^{t} \rho(s)ds$$

The correlation can therefore be calculated as the following for a time u - t:
$$correlation = \frac{covariancee}{\sqrt{u - t} \sqrt{u - t}}$$

$$correlation = \frac{\int_{t}^{u} \rho(s)ds}{\sqrt{u - t} \sqrt{u - t}}$$

If the function is constant, then the integral is just the difference multiplied by the value:

$$correlation = \frac{(u - t)\rho(s)ds}{u - t}$$

The quadratic variation for each process and the two processes combined can be given by:

$$\langle X,X \rangle _T = \sum _{}^{N} [\Delta X(t)]^2 = \int _{0}^{T} \sigma_x ^2 dt$$

$$\langle Y,Y \rangle _T = \sum _{}^{N} [\Delta Y(t)]^2 = \int _{0}^{T} \sigma_y ^2 dt$$

Thus the product of the two can be given by:

$$\langle Y,X \rangle _T = \sum _{}^{N} [\Delta Y(t)][\Delta X(t)] = \int _{0}^{T} \sigma_y \sigma_x \rho dt$$

This is because we assume that the quadratic variation of two brownian motions is the correlation and time: 

$$dW_x dW_y = \rho (t) dt $$
