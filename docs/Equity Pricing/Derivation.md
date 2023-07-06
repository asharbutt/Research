---
layout: default
title: Black Scholes Option Price Derivation
parent: Option Pricing Theory
grand_parent: Equity Pricing
mathjax: true
nav_order: 1
---
# The Stock process
We have mentioned before that the stock process is given by a GBM. Under the risk neutral measure, the drift is the risk free rate, given by:

$$dS_t = r S_t dt + \sigma S_t dW_t$$

We create a discount process given by D(t), and the dynamics are given by:

$$dD_t = -R(t)D(t)dt$$

We show that the discounted stock process is a martingale: We create a new function f of both the discount factor and the stock process:

$$$$
