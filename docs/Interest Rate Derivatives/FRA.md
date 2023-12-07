---
layout: default
title: FRAs
parent: Interest Rate Derivatives
mathjax: true
nav_order: 1
---

# Forward Rate Agreements
An FRA is an agreement to exchange some float reference rate for a fixed rate K some time in the future. The fixed rate K is set such that the value of the FRA at initiation is 0. The FRA has 3 key dates: Initiation, maturity, where the float rate is decided to be exchanged, and the settlement, which is where the cashflows are exchanged (if cash settled, then the difference can be exchanged)

The value of the Long FRA is therefore the following at maturity:

$$FRA(0,T,\delta, i_T) = \frac{\delta(i_T - K)}{1+\delta i_T}$$

i.e. the discounted cashflow from settlement. If $$B(0, T+\delta)$$ is the value of a zero coupon bond from today maturing at the settlement date, then the value of the FRA today is:

$$FRA(0,T,\delta, i_T) = B(0, T+\delta)(\delta(f_{0,T,\delta} - K))$$

The zero coupon bond in this case would be a combination of the forward rate and the current rate till T. 

