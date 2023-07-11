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

Intuitively, we are creating a brownian motion on the risk neutral measure by adjusted the real world brownian motion by the drift process, which is represented as the market price of risk, given previously.

