---
layout: default
title: Properties of Brownian Motion
parent: Stochastic Calculus
mathjax: true
nav_order: 2
---
# Properties of Brownian Motion
## Scaling and Symmetries
Given that a process $${W(t)}_{t \geq 0}$$ is a Brownian motion, then so are the following:
1. {-W(t)}
2. $${aW(\frac{t}{a^2})}$$
3. $${tW(\frac{1}{t^2})}$$
4. {W(t+s) - W(t)}

4 is as a result of the Markov Property which we will talk about later. The importance of the scaling and symmetries is that if we were to have a Brownian process, then if we flipped the sign, then the resulting path would still be a Brownian process with the same distribution. Due to the continuity of the process, it is differentiable everywhere and so the min and max operators are well defined:

1. $$M(t) = max {W(s): 0 \leq s \leq t}$$
2. $$M^-(t) = min {W(s): 0 \leq s \leq t}$$

Due to the symmetry, if we were to have {-W(t)}, it would still be a Brownian motion, and so would the resulting M(t) process. Furthermore, max operator of the original process would be the same as the negative min operator in distribution:

$$M(t) \stackrel{d}{=} -M^-(t)$$

## Stopping times
We will quickly revisit stopping times. A time/event $$/tau$$ is a stopping time if $${\tau < t} \in F_t$$. A stopping time is a strict stopping time if $${\tau \leq t} \in F_t$$. In essence, a stopping time is some event that on happening becomes measurable with respect to the current filtration. This means that if it has not happened, we have no information on the event in our current filtration.

This is quite useful in the cases of Barrier options where we would want to monitor whether or not the maximum of the price process has hit a pre-determined level or not

## Markov properties
Markov Property:
Given a Brownian motion $$ {W_t}_{t \geq 0} $$, then the interval $$ {W(t+s) -  W(t)}_{s,t \geq 0} $$ is also a Brownian motion and independent of the process up till time t:

$${W(t+s) -  W(t)}_{s,t \geq 0} \perp\kern-5pt\perp {W(t)}_{t \geq 0} $$ and is also a standard Brownian Motion
