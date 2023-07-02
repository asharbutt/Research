---
layout: default
title: Equity Pricing Introduction
parent: Equity Pricing
nav_order: 1
---
# Equity Derivatives Pricing Introduction
Stock can be represented through a Log-normal distribution due to the simple fact that stocks are limited liability - they cannot go below 0 in value. This makes the Log-normal distribution a great candidate due to its lower bound being 0, something the normal distribution does not have. 

We can model the stock price as a Geometric Brownian Motion, with Geometric meaning that the process is scaled by the current value of the variable such that as the variable approaches 0, the process also approaches 0:

$$dS_t = \mu S_t dt + \sigma S_t dW_t$$

where $$\mu$$ and $$\sigma$$ are the instantaneous mean and volatility, and $$dW_t$$ is the brownian motion increment, modelled as a random variable distributed normally: $$X \sim N(0, dt)$$, which we can compute analytically as some random variable calculated as: $$Y \sqrt{dt}$$ such that Y is a standard normal variable.

