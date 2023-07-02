---
layout: default
title: Geometric Brownian Motion Representation of Equity
parent: Equity Pricing
nav_order: 1
---

# Geometric Brownian Motion
We can model the stock price as a Geometric Brownian Motion, with Geometric meaning that the process is scaled by the current value of the variable such that as the variable approaches 0, the process also approaches 0:

$$dS_t = \mu S_t dt + \sigma S_t dW_t$$

where $$\mu$$ and $$\sigma$$ are the instantaneous mean and volatility, and $$dW_t$$ is the brownian motion increment, modelled as a random variable distributed normally: $$X \sim N(0, dt)$$, which we can compute analytically as some random variable calculated as: $$Y \sqrt{dt}$$ such that Y is a standard normal variable.

The Geometric part of the brownian motion means that the entire process is lognormally distributed, supporting the 0 absorbing barrier of the process.

The right hand side of the brownian motion is known as the diffusion term, or the term that dictates the size of the up and down movements. The left side is the drift term, which dictates what the process will drift towards in the long term, the mean. It is important to note that the GBM is not stationary as the diffusion term is dictated by the change in time, thus is dependent on time. 


