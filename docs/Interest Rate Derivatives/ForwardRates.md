---
layout: default
title: The Forward Measure and Forward Rate
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
