---
layout: default
title: Ito Integral
parent: Stochastic Calculus
mathjax: true
permalink: /docs/Stochastic Calculus/Ito Integral/
nav_order: 1
---
# Ito Integral
General integrals are quite easy to work out because the functions are differentiable, and we can use theory to split up the intergrals into smaller and smaller sections in order to calculate the values. However, an Ito Integral is one that is being integrated with respect to a Brownian Motion, for example:

$$\int_{0}^{t} \Delta (u) ,dW$$

The issue with this intergral is that the brownian motion that its being integrated w.r.t cannot be differentiated. This makes these integrals very special as we cannot use ordinary calculus on them, meaning we resort to something called Ito Calculus.

We first describe the characteristics of Ito Integrals. Let I(t) = $$\int_{0}^{t} \Delta (u) ,dW$$, and Ito Integral, then:
1. Continuity - The Integral is continious everywhere
2. Adaptivity - The Integral is F(t) measurable
3. Linearity - Just like with expectations, we can split the integral into seperate integrands
4. Martingale - The Integral is a martingale just like the Brownian Motion
5. Ito Isometry - $$EI^2(t) = E \int_{0}^{t} \Delta^2 (u) ,du$$
6. Quadratic Variation - [I,I]_t = $$\int_{0}^{t} \Delta^2 (u) ,du$$
7. The expectation of the Ito Integral is 0 - only in the case that the integrand is an arbitrary martingale. If it is a local martingale, the expectation of the integral can be anything

## Ito-Doeblin Formula
Because the brownian motion function is not differentiable unlike regular functions, we need to use a different rule when it comes to differentiation. 

Assume we have a function of a Brownian motion, f(W(t)). We need to use the chain rule to differentiate this:

$$\frac{d}{dt}f(W(t)) = f'(W(t))W'(t)$$

which in differential notation is written as:

$$df(W(t)) = f'(W(t))dW(t)$$

But Brownian motions have non-zero quadratic variation, meaning that we need to add in an extra term at the end:

$$df(W(t)) = f'(W(t))dW(t) + \frac{1}{2}f''(W((t))dW(t)dW(t)$$

Because the dW(t)dW(t) is the quadratic variation, recall that this is equal to dt, or the change in time of the increment, and therefore the above formula becomes:

$$df(W(t)) = f'(W(t))dW(t) + \frac{1}{2}f''(W((t))dt$$

We can also write the above in integral form as:

$$f(W(t))- f(W(0)) = \int_{0}^{t} f'(W(u)) ,dW(t) + \frac{1}{2} \int_{0}^{t} f''(W((u)) ,du$$

The second integral is a regular integral, whereas the first integral is an Ito Integral.

### Ito-Doeblin Formula for functions of time and Brownian Motion
What if the function was not only a function of brownian motion but also time? In Ito Calculus, the time is now an additional factor which must also be differentiated:

$$df(T, W(T)) = f_t(T, W(T))dt + f_x(T, W(T))dW(T) + \frac{1}{2}f_{xx}(T, W((T))dt$$

Because the change in time is no longer non-zero, we must consider the differential wrt time as well. But we must also remember that the quadratic variation of time is 0 i.e. dtdt = 0. Furthermore, dtdW = 0, as the cross variation is also 0.

### Integration with respect to Ito processes
An Ito Process is any general stochastic process which is absolutely continious, which includes all stochastic processes except any that have jumps. An example of an Ito process is:

$$X(t) = X(0) + \int_{0}^{t} \Delta (u) ,dW(u) + \int_{0}^{t} \Theta (u) ,du$$

We can see that one integrand is deterministic, meaning ordinary calculus applies whereas the first is an Ito Integrand. The quadratic variation of this Ito process is the same as an ito integral:

$$[X,X]_t = \int_{0}^{t} \Delta^2 (u) ,du$$

What if we were to integrate a deterministic process with respect to this Ito process?

Suppose we have the following integral:

$$\int_{0}^{t} \Gamma(u) ,dX$$

We can rewrite the above as:

$$\int_{0}^{t} \Gamma(u) ,dX = \int_{0}^{t} \Gamma (u) \Delta (u) ,dW(u) + \int_{0}^{t} \Gamma(u) \Theta (u) ,du$$
