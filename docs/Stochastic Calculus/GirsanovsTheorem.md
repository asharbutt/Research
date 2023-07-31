---
layout: default
title: Girsanov's theorem
parent: Stochastic Calculus
mathjax: true
nav_order: 3
---
# Girsanovs Theorem
Girsanov's Theorem states that when switching from one measure to another, we can construct a new stochastic process with a different drift. For example, when switching from the real world measure P to the risk neutral measure Q, Girsanovs theorem states that we can construct a new stochastic process under the Q measure with an adjusted drift. The theorem describes how the process changes between the two measures.

In real world pricing due to risk, we know that derivatives or investments will have an excess return over the risk (risk premium), and when going to the risk neutral measure, this excess return is removed since you earn the rate as the mean. 

This means that there has to be some process which adjusts the drift when moving from the real world measure to the risk neutral measure. For this, we use the market price of risk, which is given by:

$$\theta(t) = \frac{\mu - r(t)}{\sigma}$$

Under Girsanovs theorem, we can switch from one Brownian motion on the real world measure to a risk neutral measure using:

$$W^Q = W^P + \int_{0}^{T}\theta(s) ds$$

Intuitively, we are creating a brownian motion on the risk neutral measure by adjusted the real world brownian motion by the drift process, which is represented as the market price of risk, given previously. This new Brownian Motion is a martingale.

The Radon-Nikodym derivative of the two measures can be given by:

$$Z(T) = e^{ -\frac{1}{2} \int_{0}^{T} \theta ^2(s)ds - \int_{0}^{T} \theta dW^P}$$

## Simple summary
When changing the probability measure, there is no guarantee that our Brownian motion will remain a Brownian motion. Recall Levy theorem which defines a Brownian motion:

1. Brownian Motion is a martingale process
2. The increments of a Brownian Motion are normally distributed with mean 0 and variance dt
3. Non-overlapping increments are independent

When changing the probability measure, we also change the probabilities themselves, and thus introduce a drift within the brownian motion, meaning it is no longer a martingale. 

In order to cancel out this drift, we introduce Girsanovs theorem, which describes how the drift changes under a different probability measure using some deterministic adapted function. 
This drift adjustment can be used to cancel out this newly introduced drift in the process under the measure. 


