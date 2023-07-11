---
layout: default
title: Radon-Nikodym theorem and Change of Numeraire
parent: Stochastic Calculus
mathjax: true
nav_order: 6
---
# Radon-Nikodym Theorem
When 2 measures are equivalent, we know that both measures agree with what is not possible i.e if $$\mu(A) = 0$$ then $$\nu(A) = 0$$ as well. Another way of saying this is that $$\nu$$ is absolutely continious with respect to $$\mu$$ i.e. $$\nu \ll \mu$$.

The Radon-Nikodym theorem states that for 2 equivalent measures on a space, there exists a non-negative function/variable Z such that EZ = 1 and:

$$\nu(A) = \int_{A}^{} Z(w)d\mu$$

Intuitively, Z is some function that represents the relationship between two integrable finite and positive equivalent measures on the same space. The theorem states that this non-negative function Z is known as the **Radon-Nikodym derivative**, which is shown as:

$$Z = \frac{d\nu}{d\mu}$$

which means we can re-write the above equation as:

$$\nu(A) = \int_{A}^{} \frac{d\nu}{d\mu}d\mu$$

### Easy Summary
Generally the expectation of some function of a random variable is defined as:

$$E[g(X)] = \int_{\Omega}^{} g(x)dF(X)$$

where dF(X) represents the change in the CDF over the interval. There generally exists a function f on the real line such that:

$$E[g(X)] = \int_{\Omega}^{} g(x)f(X)dx$$

This function can be regarded as the pdf, or the density function of probability over a very small interval. Now if we are two define two equivalent measures such that they are absolutely continious w.r.t each other, then is there some function Z such that such that we convert an integral with respect to one measure to an integral w.r.t to the other measure:

$$\int_{\Omega}^{} g(x)d\mu = \int_{\Omega}^{} g(x)Z(x)\nu(x)$$$

This function is regarded as the Radon-Nikodym derivative, and represents the ratio of the change between the two functions such that:

$$Z = \frac{d\nu}{d\mu}$$

## Change of Numeraire
The change of numeraire technique is introduced by Gemna et al, and is as follows: We have some asset price X, and the contract will have some payoff which is a function of this asset price, given by h(X). Under the risk neutral measure, the value of the process is calculated as follows:

$$D(t)V(t) = E^Q[D(T)V(T)|F(t)]$$

Where the numeraire under the risk neutral measure is the money market account, given by:

$$B(t) = D(t)^{-1}$$

The value process is being divided by the numeraire, but since the discount factor is the inverse, it is convenient to write it out as a product of the discounted process instead.

A change of measure means that the process has to be a martingale under its new respective measure, and if we define the numeraire to be S, then the expectation would change and look as follows:

$$E^Q[D(T)V(T)|F(t)] = E^S[\frac{V(T)}{S_T}|F(t)]$$

We will use this quite often when it comes to defining new measures in the future, such as the T-forward measure or periodic measure for interest rates.
