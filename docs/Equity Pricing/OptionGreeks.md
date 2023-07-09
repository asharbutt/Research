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

$$\frac{\partial}{\partial S} \int_{-\infty}^{d_1} \phi (x)dx$$

According to the second theorem of calculus and the chain rule, the derivative of an integral is the function being integrated time the derivative of any function in the bounds. If the bounds of the integral are a constant, there is no derivative, and so the derivative will just be the function being integrated itself:

$$\frac{\partial}{\partial x} \int_{a}^{f(x)} g(x)dx = g(f(x)) \cdot f'(x)$$

Thus in our case:

$$\frac{\partial}{\partial S} \int_{-\infty}^{d_1} \phi (x)dx = \phi(d_1) \cdot \frac{\partial}{\partial S} d_1$$

The derivative of d1 w.r.t S is:

$$\frac{1}{S\sigma\sqrt{\tau}}$$

Thus the Gamma is given by:

$$\frac{\partial \Delta}{\partial S} = e^{-q\tau}\phi (d_1) \cdot \frac{\partial}{\partial S} d_1 = \frac{e^{-q\tau}}{S\sigma\sqrt{\tau}} \phi (d_1)$$

Where $$\phi$$ is the standard normal density function.

## Vega
The Vega represents the change in the option value as the volatility changes. The formula for vega is given below:

$$\nu = \frac{\partial V}{\partial \sigma} = S_0e^{-q\tau}\phi(d1)\sqrt{\tau}$$

### Proof
The proof for the vega is slightly different. We start with the usual partial differential:

$$\frac{\partial V}{\partial \sigma} = \frac{\partial}{\partial \sigma}S_0e^{-q\tau}N(d_1) - \frac{\partial}{\partial \sigma}Ke^{-r\tau}N(d_2)$$

We know the derivative of the normal CDF will be the density function multiplied by the partial derivative of the upper bound:

$$\frac{\partial V}{\partial \sigma} = S_0e^{-q\tau}\phi(d_1)\frac{\partial}{\partial \sigma}d_1 - Ke^{-r\tau}\phi(d_2)\frac{\partial}{\partial \sigma}d_2$$

We know that $$d_2 = d_1 - \sigma\sqrt{\tau}$$

and so can subsititute this in:

$$\frac{\partial V}{\partial \sigma} = S_0e^{-q\tau}\phi(d_1)\frac{\partial}{\partial \sigma}d_1 - Ke^{-r\tau}\phi(d_2)\frac{\partial}{\partial \sigma}(d_1 - \sigma \sqrt{\tau})$$

$$\frac{\partial V}{\partial \sigma} = S_0e^{-q\tau}\phi(d_1)\frac{\partial}{\partial \sigma}d_1 - Ke^{-r\tau}\phi(d_2)\frac{\partial}{\partial \sigma}d_1 + Ke^{-r\tau}\phi(d_2)\frac{\partial}{\partial \sigma}\sigma \sqrt{\tau})$$

$$\frac{\partial V}{\partial \sigma} = [S_0e^{-q\tau}\phi(d_1) - Ke^{-r\tau}\phi(d_2)]\frac{\partial}{\partial \sigma}d_1 + Ke^{-r\tau}\phi(d_2)\sqrt{\tau})$$

There is a relationship between the density functions which we will not prove here, but is given by the following:

$$S_0 e^{-q\tau}\phi(d_1) = Ke^{-r\tau}\phi(d_2)$$

We can therefore subsitute this in for the first square bracket, and thus make the terms cancel out, leaving us with the second part:

$$\frac{\partial V}{\partial \sigma} =  Ke^{-r\tau}\phi(d_2)\sqrt{\tau}$$

$$\frac{\partial V}{\partial \sigma} = S_0 e^{-q\tau}\sqrt{\tau}\phi(d_1)$$

## Theta
The Theta is the relationship between the option value and time to maturity. There is a negative relationship, because as we get closer to the maturity, if the option is out of money, then the smaller the value of the option becomes, approaching 0.

The theta can be written as:

$$\Theta = - \frac{\partial V}{\partial \tau} = -\frac{-S_0 n(d_1)\sigma}{2\sqrt{\tau}} - rKe^{-r\tau}N(d_2)$$

The proof for this 
