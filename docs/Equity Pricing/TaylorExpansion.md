---
layout: default
title: Taylor Expansion and ATM Estimation + Greeks
parent: Option Pricing Theory
grand_parent: Equity Pricing
mathjax: true
nav_order: 6
---
# Taylor Expansion
The Taylor function is an approximation to any function using its derivatives. The single variable expansion can be given by:

$$f(x) = f(a) + f'(a)(x-a) + \frac{f''(a)}{2!}(x-a)^2 + ... + \frac{f^n(a)}{n!}(x-a)^n$$

The McLaurin series expansion is the Taylor series around a = 0, such that:

$$f(x) = f(0) + f'(0)x + \frac{f''(0)}{2!}x^2 + ... + \frac{f^n(0)}{n!}x^n$$

Of course to have an n Taylor expansion, the function f must be n-differentiable. 

For the multivariable expansion, we get:

$$f(x,y) = f(a) + f_x(a)(x-a) + f_y(a)(y-b) + \frac{f_{xx}(a)}{2!}(x-a)^2 + \frac{f_{yy}(a)}{2!}(y-b)^2 + \frac{f_{xy}(a)}{2!}(x-a)(y-b) +...$$

If we cut off the expansion before the n differentiable limit, we introduce an error. For example, for an n+1 differentiable funtion f:

$$f(x,y) = f(a,b) + f_x(a)(x-a) + f_y(a)(y-b) + \frac{f_{xx}(a)}{2!}(x-a)^2 + \frac{f_{yy}(a)}{2!}(y-b)^2 + \frac{f_{xy}(a)}{2!}(x-a)(y-b) +... O(x^{n+1}) + O(y^{n+1})$$

For a 2nd degree Taylor expansion, the error term is:

$$f(x,y) = f(a) + f_x(a)(x-a) + f_y(a)(y-b) + \frac{f_{xx}(a)}{2!}(x-a)^2 + \frac{f_{yy}(a)}{2!}(y-b)^2 + \frac{f_{xy}(a)}{2!}(x-a)(y-b) + O(x^{3}) + O(y^{3})$$

If we remove the error terms, we get an approximation:

$$f(x,y) \sim f(a) + f_x(a)(x-a) + f_y(a)(y-b) + \frac{f_{xx}(a)}{2!}(x-a)^2 + \frac{f_{yy}(a)}{2!}(y-b)^2 + \frac{f_{xy}(a)}{2!}(x-a)(y-b)$$

## Greeks relationship via Taylor expansion
Given the greeks represent changes in the option value relative to other values, let us use Taylors expansion to evaluate V(S+dS,t+ dt). We will have the following parameters: x = S + ds, y = t + dt, a = S, b = t. This gives us the following when doing a 2nd order expansion:

$$f(x,y) = f(a,b) + f_x(a)(x-a) + f_y(a)(y-b) + \frac{f_{xx}(a)}{2!}(x-a)^2 + \frac{f_{yy}(a)}{2!}(y-b)^2 + \frac{f_{xy}(a)}{2!}(x-a)(y-b) + O((x-a)^{3}) + O((y-b)^{3})$$

Replacing the terms with the original parameters:

$$V(S + dS,t + dt) = V(S,t) + \frac{\partial V}{\partial S}dS + \frac{\partial V}{\partial t}dt  + \frac{\partial ^2 V}{\partial S^2}\frac{dS^2}{2}  + \frac{\partial ^2 V}{\partial t^2}\frac{dt^2}{2} + \frac{\partial ^2 V}{\partial S \partial t}\frac{dSdt}{2} + O(dS^{3}) + O(dt^{3})$$

Recalling that dSdt = 0, dtdt = 0 and dSdS = $$\sigma ^2 S^2 dt$$, and removing the error terms at the end, we get the following approximation:

$$V(S + dS,t + dt) \sim V(S,t) + \frac{\partial V}{\partial S}dS + \frac{\partial V}{\partial t}dt  + \frac{\partial ^2 V}{\partial S^2}\frac{\sigma^2 S^2 dt}{2}$$

We can replace the derivatives with their respective greeks:

$$V(S + dS,t + dt) \sim V(S,t) + \Delta dS + \Theta dt  + \Gamma \frac{\sigma^2 S^2 dt}{2}$$
