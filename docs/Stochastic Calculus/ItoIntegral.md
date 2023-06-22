---
layout: default
title: Ito Integral
parent: Stochastic Calculus
mathjax: true
permalink: /docs/Stochastic Calculus/Ito Integral/
nav_order: 1
---
# Ito Integral
General integrals are quite easy to work out because the functions are differentiable, and we can use theory to split up the intergrals into smaller and smaller sections in order to calculate the values. However, an Ito Integral is one that is being integrated with respect to a Brownian Motion, for example:

$$\int_{0}^{t} \Delta (u) ,dW$$

The issue with this intergral is that the brownian motion that its being integrated w.r.t cannot be differentiated. This makes these integrals very special as we cannot use ordinary calculus on them, meaning we resort to something called Ito Calculus.

We first describe the characteristics of Ito Integrals. Let I(t) = $$\int_{0}^{t} \Delta (u) ,dW$$, and Ito Integral, then:
1. Continuity - The Integral is continious everywhere
2. Adaptivity - The Integral is F(t) measurable
3. Linearity - Just like with expectations, we can split the integral into seperate integrands
4. Martingale - The Integral is a martingale just like the Brownian Motion
5. Ito Isometry - $$EI^2(t) = E \int_{0}^{t} \Delta^2 (u) ,du$$$$
7. Quadratic Variation - [I,I]_t = $$\int_{0}^{t} \Delta^2 (u) ,du$$
