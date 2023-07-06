---
layout: default
title: Black Scholes Option Price Derivation
parent: Option Pricing Theory
grand_parent: Equity Pricing
mathjax: true
nav_order: 1
---
# The Stock process
We have mentioned before that the stock process is given by a GBM. We assume that the process under some measure P is given by:

$$dS_t = \alpha (t) S_t dt + \sigma S_t dW^P$$

We create a discount process given by D(t), and the dynamics are given by:

$$dD_t = -R(t)D(t)dt$$

Under the risk neutral measure, we assume that the interest rate is constant. Furthermore, even if the rate wasnt constant, an instant change would not be realised in the money market account instantly, and so over shorter periods dt, we can assume the rate to not be stochastic.
We show that the discounted stock process is a martingale: We create a new function f of both the discount factor and the stock process:

$$df(D(t)S(t))$$

The differential for this function can be derived using Ito's Product rule:

$$df(D(t)S(t)) = dD(t)S(t) + D(t)dS(t) + dD(t)dS(t)$$

$$df(D(t)S(t)) = -R(t)D(t)dtS(t) + D(t)(\alpha(t) S_t dt + \sigma S_t dW^P) + (-R(t)D(t)dt)(\alpha (t) S_t dt + \sigma S_t dW^P)$$

The product on the far right will cancel out as $$dt^2 = 0$$ and $$dtdW_t = 0$$

$$df(D(t)S(t)) = D(t)S(t)dt[\alpha(t) - R(t)] + \sigma D(t)S(t)dW^P$$

We can take out the $$\sigma$$, D(t) and S(t), shifting everything inside the bracket:

$$df(D(t)S(t)) = D(t)S(t)\sigma [\frac{\alpha (t) - R(t)}{\sigma}dt + dW^P] $$

Using Girsanovs Theorem, we can define a new brownian motion under a new risk neutral measure:

$$dW^P = dW^Q + \theta dt$$

We can do some manipulation to the differential equation for the discounted stock price:

$$df(D(t)S(t)) = D(t)S(t)\sigma [\theta dt + dW]$$

Where $$\theta = \frac{\alpha (t) - R(t)}{\sigma}$$, which we define as the **market price of risk, or the Sharpe ratio**

And using the brownian motion from Girsanovs theorem, we get:

$$df(D(t)S(t)) = D(t)S(t)\sigma [dW^Q] $$

If we take the integral of this, we get an Ito Integral, which by definition is a martingale. So under the risk neutral measure Q, the discounted stock price is a martingale.

A summary of what we have done:
1. We have the stock process under some measure P
2. We have a discount process under the same measure P
3. We calculate the differential of the discounted stock process using Ito's Product rule
4. We use a change of measure to change the brownian motion from the measure P to an equivalent martingale measure Q, known as the risk neutral measure.
5. Under this measure, the discounted stock price is a martingale.

An interesting note is that if we did not change the measure, then the discounted stock price process would not be a martingale under the original measure. 

## The replicating portfolio
We replicate the option payoff portfolio using an investment into the stock and into the money market account. We buy $$\Delta (0)$$ amounts of the stock and invest the remainder into a money market account (NOT A BOND). The dynamics of this can be shown as:

$$dX(t) = \Delta (t)dS(t) + R(t)[X(t) - \Delta(t)S(t)]dt$$

We can input our stock price process into here (under the measure P):

$$dX(t) = \Delta (t)(\alpha (t) S_t dt + \sigma S_t dW^P) + R(t)[X(t) - \Delta(t)S(t)]dt$$

$$dX(t) = \Delta (t)\alpha (t) S_t dt + \Delta (t)\sigma S_t dW^P + R(t)X(t)dt - R(t)\Delta(t)S(t)dt$$

$$dX(t) = \Delta (t) S_t dt (\alpha (t) - R(t)) + \Delta (t)\sigma S_t dW^P + R(t)X(t)dt $$

$$dX(t) = \Delta (t) S_t \sigma(\frac{\alpha (t) - R(t)}{\sigma}dt +  dW^P) + R(t)X(t)dt $$

$$dX(t) = \Delta (t) S_t \sigma(\theta dt +  dW^P) + R(t)X(t)dt $$

So this is the dynamics of the replicating portfolio. Now what would be the dybamics of the discounted replicating portfolio? We show the following using Ito's product rule:

$$d(X(t)D(t)) = dX(t)D(t) + dD(t)X(t) + dX(t)dD(t)$$$

$$d(X(t)D(t)) = (\Delta (t) S_t \sigma(\theta dt +  dW^P) + R(t)X(t)dt)D(t) + X(t)(-R(t)D(t)dt) + (-R(t)D(t)dt)(\Delta (t) S_t \sigma(\theta dt +  dW^P) + R(t)X(t)dt)$$$

Again, the right product will cancel out, giving us the following:

$$d(X(t)D(t)) = \Delta (t) S_t \sigma dW^Q$$$

Which, just like the discounted price process is a martingale.
