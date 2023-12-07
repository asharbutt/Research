---
layout: default
title: FRAs and futures
parent: Interest Rate Derivatives
mathjax: true
nav_order: 1
---

# Forward Rate Agreements
An FRA is an agreement to exchange some float reference rate for a fixed rate K some time in the future. The fixed rate K is set such that the value of the FRA at initiation is 0. The FRA has 3 key dates: Initiation, maturity, where the float rate is decided to be exchanged, and the settlement, which is where the cashflows are exchanged (if cash settled, then the difference can be exchanged)

The value of the Long FRA (receive the float rate, pay the fixed) is therefore the following at maturity:

$$FRA(0,T,\delta, i_T) = \frac{\delta(i_T - K)}{1+\delta i_T}$$

i.e. the discounted cashflow from settlement. If $$B(0, T+\delta)$$ is the value of a zero coupon bond from today maturing at the settlement date, then the value of the FRA today is:

$$FRA(0,T,\delta, i_T) = B(0, T+\delta)(\delta(f_{0,T,\delta} - K))$$

The zero coupon bond in this case would be a combination of the forward rate and the current rate till T. Therefore, at initiation, the strike rate would be set such that:

$$FRA(0,T,\delta, i_T) = 0$$

$$B(0, T+\delta)(\delta(f_{0,T,\delta} - K)) = 0$$

$$f_{0,T,\delta}  = K$$

# Futures
A future is similar to an FRA, but with an FRA being usually OTC, Futures are exchange traded, meaning they come in pre-determined sizes. On top of that, unlike a Forward, Futures are settled on a daily basis, such that the rolling value of a futures is 0 - this is to minimise default loss. 

Futures are settled on maturity date, unlike a forward which is settled after maturity. This, combined with the daily settlement, means that the futures rate is not the same as forward rate on the same contract. Whereas the value of an FRA on maturity is:

$$FRA(0,T,\delta, i_T) = \frac{\delta(i_T - K)}{1+\delta i_T}$$

The value of a future on maturity is:

$$Futures(0,T,\delta, i_T) = \delta(i_T - K)$$

Because of daily settlement, you can capture and reinvest any profits to earn a higher profit on top of a possible futures settlement, meaning the futures rate is higher than the respective foward rate. This difference is known as the convexity adjustment between them, as the relationship is not linear.

When converting between forward and futures rates, we can use the following convexity adjustment:

$$f_{0,T,\delta} = h_{0,T} - \frac{1}{2}\sigma_f T \delta$$
