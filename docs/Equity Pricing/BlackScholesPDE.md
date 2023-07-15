---
layout: default
title: Black Scholes PDE
parent: Option Pricing Theory
grand_parent: Equity Pricing
mathjax: true
nav_order: 1
---
# The Black Scholes PDE
There are a few methods of deriving the famous Black Scholes PDE. We will look at the original method Black and Scholes used to derive the famous differential equation: the hedging portfolio.

The hedging portfolio acts as a replicating portfolio to replicate the payoff of the orignial instrument, and is used to remove any risks arisnig from sensitivities in the contract. The simplest hedging portfolio for a European Option is shorting an x amount of the underlying stock.

This means that if we construct a hedged portfolio called $$\Pi$$, it will be made of:

$$\Pi = V - \Delta S$$

Where $$\Delta = \frac{\partial V}{\partial S}$$

What we want to know is, how does the value of this portfolio change? In a no-arbitrage risk neutral environment, the portfolio should grow at the risk free rate such that:

$$d\Pi = r\Pi dt$$

The change in the portfolio itself is shown as:

$$d\Pi = dV - \Delta dS$$

We know that the stock dynamics can be shown as below:

$$dS = \mu S dt + \sigma S dW$$

The change in the option value can be derived through Ito Calculus:

$$dV(S,t) = V_t(S,t)dt + V_S(S,t)dS + \frac{1}{2}V_{SS}(S,t)dSdS$$

$$dV(S,t) = \frac{\partial V}{\partial t}dt + \frac{\partial V}{\partial S}(\mu S dt + \sigma S dW) + \frac{1}{2}\frac{\partial^2 V}{\partial S^2}(\mu S dt + \sigma S dW)^2$$

$$dV(S,t) = \frac{\partial V}{\partial t}dt + \frac{\partial V}{\partial S}\mu S dt  + \frac{\partial V} \sigma S dW + \frac{1}{2}\frac{\partial^2 V}{\partial S^2}\sigma^2 S^2 dt$$
