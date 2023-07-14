---
layout: default
title: Numeraires and Martingales
parent: Stochastic Calculus
mathjax: true
permalink: /docs/Stochastic Calculus/Numeraire/
nav_order: 1
---
# Numeraires
The idea of Numeraires can be a confusing one. The simple definition of a Numeraire is that it is some sort of measure that we use to express everything else in terms of. For example, if we want to set a cow as a numeraire, then we would express the price of everything else in terms of numeraire.

Why is this important in financial maths and asset pricing? When determining the value of a contract, we want to know how to price it. What would be a fair price? In order to determine that, we need to know what we can compare it to? What is a simple investment in the real life that we can use to compare the price of a contract to? Realistically, people invest in contracts for either speculation purposes or hedging. Speculation carries risk, and thus people invest in order to be rewarded. So what is the risk free alternative? In the risk neutral worl, the alternative would be the risk free bank account - investing in a bank account paying a continiously compounded rate. Thus in risk neutral pricing, we can define the price of all contracts relative to the money market bank account.

The reason why this is so important is because in financial maths, one way of determining the price of a contract is to calculate the martingale expectation of the payoff of that contract. This builds the foundations to how we get the famous Black-Scholes Merton equation. 

We use some tradeable asset as a numeraire, normally something that has a non-negative value such as the money market account (for risk neutral) or a zero coupon bond. We then find an equivalent martingale measure under which the numeraire adjusted asset value is a martingale. This, as mentioned above, allows us to represent the price of the payoff/process as a martingale expectation.

## Numeraires and Martingales
Any asset divided by a numeraire is a martingale under the measure associated with that numeraire. Of course we need to be able to prove that the numeraire adjusted process is indeed a martingale, but generally there is always some measure for every numeraire such that the measure is a martingale measure.

Where the numeraire is the money market account $$B(t) = e^{\int_{0}^{t} r(s)ds}$$, the associated martingale measure is the risk neutral measure. We can show the proof for this under the option pricing formula.


