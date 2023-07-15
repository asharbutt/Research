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


