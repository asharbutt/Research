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


$$\frac{\partial \Delta}{\partial S} = \frac{\partial ^2V}{\partial S^2} = \frac{\partial}{\partial S}e^{-q\tau}N(d_1)$$
