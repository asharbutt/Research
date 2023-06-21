---
layout: default
title: Transformations Of Random Variables
parent: Basics
grand_parent: Probability Theory
mathjax: true
permalink: /docs/Probability Theory/Basics/Transformations/
nav_order: 6
---
# Transformations
## Transformations of Single Random Variables
We have a continious random variable X, and apply a transformation to it, h(x), which is a continious function which has a inverse function $$h^{-1}(x)$$ which is continious and differentiable.

What would be the probability distribution function and CDF of this transformed variable? This is quite straightforward. Let us create a new variable Y which is the transformed variable such that Y = h(X). Then:
<div class="code-example" markdown="1">
$$F_Y(y) = F_X(h^{-1}(y))$$

$$f_Y(y) = f_X(h^{-1}(y))\frac{d}{dy}h^{-1}(y)$$

Proof:

$$P(Y \leq y) = P(h(X) \leq y)$$

$$P(Y \leq y) = P(X \leq h^{-1}(y))$$

$$F_Y(y) = F_X(h^{-1}(y))$$

$$f_Y(y) = \frac{d}{dy}F_Y(y)$$

$$f_Y(y) = \frac{d}{dy}F_X(h^{-1}(y))$$

$$f_Y(y) = \frac{d}{dy}F_X(h^{-1}(y))$$

We can use the chain rule in the above equation
$$f_Y(y) = \frac{d}{dy}F_X(h^{-1}(y)) \frac{d}{dy}h^{-1}(y)$$

$$f_Y(y) = f_X(h^{-1}(y)) \frac{d}{dy}h^{-1}(y)$$
</div>

## Multiple Random Variables

