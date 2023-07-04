---
layout: default
title: Martingale Measures and No-Arbitrage Pricing
parent: Equity Pricing
nav_order: 1
---
# Martingale Measures and No-Arbitrage Pricing
We discussed in the stochastic calculus section that martingales are those where the expected future value given todays information is equal to todays value. How is this applied in pricing theory?

We say that a contingent claim X, i.e. some sort of payoff thats dependent on a condition is attainable if there exists some replicating self-financing strategy $$\phi (t)$$ such that the future value of this portfolio at time T is: $$V_{\phi}(T) = X$$. We can link this to derivatives, where we say that the payoff of a European Call/Put is attainable if there exists some self-financing strategy that can be used to replicate the payoff. Furthermore, if there exists a replicating strategy for the contingent claim X, then we say the market is complete. 

A probability measure is an equivalent martingale measure, if under that measure, the self-financed replicating portfolio is a martingale i.e:

$$E^*[V_{\phi} (T) | F(t)] = V_{\phi} (t) $$

