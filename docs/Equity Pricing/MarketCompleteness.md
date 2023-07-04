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

What we are essentially stating is that: 
1. A payoff or contingent claim X exists if it can be replicated using a self financing strategy
2. An equivalent martingale measure exists which allows this self-financing strategy to be a martingale under that measure
3. A market is said to be complete if a self-financing strategy exists with an equivalent martingale probability measure - this ensures that the discounted value of the portfolio process is a martingale under all equivalent measures, thus fulfilling the Law of One Price condition for an arbitrage free market

