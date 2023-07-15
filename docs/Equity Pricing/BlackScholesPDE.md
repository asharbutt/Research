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

Where $$\Delta = \frac{\partial V}{\Partial S}$$

What we want to know is, how does the value of this portfolio change? In a no-arbitrage risk neutral environment, the portfolio should grow at the risk free rate such that:

$$d\Pi = r\Pi dt$$
