---
layout: default
title: Brownian Motion
parent: Stochastic Calculus
mathjax: true
permalink: /docs/Stochastic Calculus/Brownian Motion/
nav_order: 1
---
# Brownian Motion
## Symmetrical Random Walk
We start with a symmetrical random walk - suppose we have a coin tossing experiment, where $$X_t$$ can be either 1 or -1. This is symmetrical because the results are evenly distributed. We define the value of our random walk using:

$$M(t) = \sum_{j=0}^{t} X_j$$

Such that the value of our path is the sum of the random variable outcomes till t. We note important characteristics of the increments of the random walk:

1. $$E[M(t) - M(s)] = 0$$ - this is because we either get +1 or -1 with probability of 0.5, thus leading to an expectation of 0
2. The variance of the increment is equal to the difference in time i.e Var(M(t) - M(s)) = t - s

This random walk is also a martingale:

1. E[M(t)|F(s)] = E[(M(t) - M(s)) + M(s)| F(s)] <- the value at M(t) is equal to the increment from s to t plus the value at t
2. E[M(t)|F(s)] = E[(M(t) - M(s)|F(s)] + E[M(s)|F(s)] <- we can split the expectation through linearity property
3. E[M(t)|F(s)] = E[(M(t) - M(s)|F(s)] + M(s) <- M(s) is F(s) measurable - we already know the value at time s
4. E[M(t)|F(s)] = E[(M(t) - M(s)] + M(s) <- The value of the increments are independent, thus not measurable with regards to the filtration
5. E[M(t)|F(s)] = M(s) <- The expectation of the increment is 0, thus the expectation of a symmetrical random walk given a prior filtration is equal to the prior value

### Quadratic Variation
The Quadratic Variation of a function is the sum of the squared differences at each increment of the function. It gives us an idea how much the function has varied in absolute terms since the start of the function leading up till time t. 

For a symmetrical random walk, the quadratic variation is equal to the time it is measured till:

[M, M](t) = t

This is an important result as this result is consistent throughout stochastic calculus

## Scaled Symmetrical Random Walk
We have discussed the characteristics of a symmetrical random walk. Now we look to scale it by doing n steps, and scaling down the result such that the function does not explode:

$$W^n(t) = \frac{1}{\sqrt{n}}M(t)$$

The value of the brownian motion as a scaled symmetrical random walk is the scaled down step sum of the total path. Just like with the random walk, the scaled symmetrical random walk has the same characteristics.

As we increase n towards infinity, the random walk will have a limiting distribution. In this case, the limiting distribution is the normal distribution. So as we increase n, the scaled symmetrical random walk will approximately be normally distributed with mean 0 and a variance of t.

## Brownian Motion
We can now formally define a Brownian Motion. Suppose we have a probability space $$(\Omega, \Digamma, P)$$, and we have a continious function W(t) where $$t \geq 0$$ that satisfies W(0) = 0. Then W(t) is a brownian motion if it satisfies the following conditions:
1. The Increments are independent
2. The Increments are normally distributed with mean 0 and variance t

The important difference between a Brownian Motion and a scaled symmetrical random walk is that the random walk is only approximately normal, whereas the Brownian Motion is exactly normal.

### Levy's characterization of Brownian Motion
Levy's theorem characterizes Brownian Motions such that any stochastic process which fulfills these conditions can be identified as a brownian motion.

Assume a stochastic process X on a probability space $$(\Omega, \digamma, P)$$ such that $$X_0 = 0$$. Then X is a brownian motion if:
1. X is a local martingale on the filtration
2. The process $$X^2 - t$$ is a local martingale
3. The process X and $$X^2 - t$$ are both continious

## Filtration for a Brownian Motion
As mentioned previously, a filtration is a sequence of $$\sigma-algebras$$ that contain all information known until that filtration time. For a Brownian motion, there is a filtration associated with the brownian motion random variable which satisfy the following conditions:
1. Information Accuulation - as mentioned previously, we expect that infromation is accumulating in every new $$\sigma-algebra$$ in the filtration, as each one should have equal to or more information than the previous $$\sigma-algebra$$
2. Adaptivity - We expect that the Brownian Motion random variable is measurable with respect to its relative filtration, meaning W(t) is measurable with respect to its filtration F(t) for every t.
3. Independence of future increments - any future increments of the Brownian Motion are independent of the filtration at the beginning of the increment. This means that we cannot use the information we know currently to predict what the change will be in the future

  
  
