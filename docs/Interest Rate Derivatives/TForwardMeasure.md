---
layout: default
title: T Foward Measure
parent: Interest Rate Derivatives
mathjax: true
nav_order: 1
---
# T-Forward Measure
As mentioned under the Change of numeraire section, we can define a new numeraire and measure through:

$$S_0 E^S[\frac{V(T)}{S_T}|F(t)]$$

A convenient numeraire to use is a zero coupon bond, and specifically a zero coupon bond which has a maturity date T equal to the maturity of our derivative. This means that at T, the numeraire will have a value of 1 by definition of zero coupon bonds, i.e. P(T,T) = 1. We can therefore re-write the expectation of some value process under a T forward measure as:

$$\frac{\pi}{P(t,T)} = E^T[\frac{V(T)}{P(T,T)}|F(t)]$$

$$\pi = P(t,T)E^T[V(T)|F(t)]$$

This becomes useful when valuing claims under the T forward measure

We can extend this to forward rates themselves. Recall that a forward rate is a simply compounded rate which can be defined by the relationship between certain bonds:

$$\frac{P(t,T)}{P(t,S)} = P(t;T,S)$$

where P(t;T,S) is a forward starting zero coupon bond for $$t \leq T \leq S$$. Based on this, the forward rate for T-S is given through:

$$\frac{P(t,T)}{P(t,S)} = \frac{1}{1 + f(t;T,S)\tau}$$

where $$\tau$$ is the daycount for the rate period. We can rearrange this to find:

$$\frac{P(t,S)}{P(t,T)} = 1 + f(t;T,S)\tau$$

$$\frac{1}{\tau}[\frac{P(t,S)}{P(t,T)} - 1)] = f(t;T,S)$$

The actual future spot rate can then be given under the T-forward measure expectation such that:

$$E^T[L(S,T)|F(t)] = f(t;T,S)$$

## Zero Coupon Bond Options
Assume we have a claim such that:

$$H_T = (P(T,S) - X)^+$$

Where P(T,S) is a zero coupon bond starting 
