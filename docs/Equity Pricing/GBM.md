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

This is the simplest representation of the stock price that was used by Black and Scholes in order to create the Black-Scholes PDE which we will look at later. There are quite a few downsides of representing the stock price as a GBM, of which we can see some below:

1. The GBM process is continious - this is not realistic as we know the stock price is prone to jumps in the real world
2. Whilst 0 is the absorbing barrier for the process, a GBM **cannot** become 0. Realistically, companies can hit 0 and default. This is something we will look at in credit default models later, such as the Merton model.
3. Whilst the equation generated from the process is Log-normal, the diffusion term is normal (due to the Brownian Motion) - this means that the up and down movements are symmetrically distributed. This is not realistic as we observe a leverage effect in real markets (talked about more in econometrics)
4. By definition, Brownian Motion increments are independent and uncorrelated - this is also not realistic as we know that sometimes movements can lead to further trends, meaning there is correlation and dependence between increments.

Whilst these disadvantages are apparent, there are some benefits of using the GBM:
1. Log-normal result, meaning no negative stock prices
2. Very tractable -  can be used very quickly in simulation and verification

