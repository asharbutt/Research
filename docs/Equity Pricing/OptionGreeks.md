---
layout: default
title: Option Greeks
parent: Option Pricing Theory
grand_parent: Equity Pricing
mathjax: true
nav_order: 1
---
# The Option Greeks
The Option Greeks represent the sensitivity of the option price relative to the underlying parameters which affect the price. They can be calculated through a range of first and second derivatives (as well as some third and fouth derivatives). They can be used in hedging trades as well as trading based on what the sensitivity values are.

## Delta
The Delta, represented by $$\Delta _C$$ or $$\Delta_P$$ measures the change in the value of the option relative to a change in the underlying value. Realistically, the value of an option will not change more than 1 times the change in the value of the underlying, thus the Delta is bounded by:

$$0 \leq \Delta_C \leq 1$$ or $$-1 \leq \Delta_P \leq 0$$ for increases in the underlying

We represent the Delta as the first derivative w.r.t the underlying, given by the following for the Black Scholes:

$$\frac{\partial V}{\partial S} = e^{-q\tau}N(d_1)$$

## Gamma
The Delta is not constant over all the values of the underlying. As the value of the underlying changes, the Delta value also changes. This signals that the option can become more or less sensitive with changes to the underlying price. It is calculated as the second derivative of the option price w.r.t underlying price, or the derivative of the delta w.r.t underlying price:

$$\frac{\partial \Delta}{\partial S} = \frac{\partial ^2V}{\partial S^2} = \frac{e^{-q\tau}}{S \sigma \sqrt{2 \pi \tau}}e^{-\frac{1}{2}d_1 ^2}$$

### Proof
$$\frac{\partial \Delta}{\partial S} = \frac{\partial}{\partial S}e^{-q\tau}N(d_1)$$

The derivative of N(d1) is given through the following:

$$\frac{\partial}{\partial S} \[ \int_{-\infty}^{d_1} \phi (x) \,dx \]$$

According to the second theorem of calculus and the chain rule, the derivative of an integral is the function being integrated time the derivative of any function in the bounds. If the bounds of the integral are a constant, there is no derivative, and so the derivative will just be the function being integrated itself:

$$\frac{\partial}{\partial x} \[ \int_{a}^{f(x)} g(x) \,dx \] = g(f(x)) \cdot f'(x)$$

Thus in our case:

$$\frac{\partial}{\partial S} \int_{-\infty}^{d_1} \phi (x)dx = \phi(d_1) \cdot \frac{\partial}{\partial S} d_1$$

The derivative of d1 w.r.t S is:

$$\frac{1}{S\sigma\sqrt{\tau}}$$

Thus the Gamma is given by:

$$\frac{\partial \Delta}{\partial S} = e^{-q\tau}\phi (d_1) \cdot \frac{\partial}{\partial S} d_1 = \frac{e^{-q\tau}}{S\sigma\sqrt{\tau}} \phi (d_1)$$

Where $$\phi$$ is the standard normal density function.
