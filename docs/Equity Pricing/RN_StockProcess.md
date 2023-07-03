---
layout: default
title: Stock Price Process under RNM
parent: Equity Pricing
nav_order: 1
---
# Stock Price Process
We have already defined the stock price process in the previous section to be given by the GBM:

$$dS_t = \mu S_t dt + \sigma S_t dW_t$$

Under the risk neutral measure, the mean rate of return is replaced by the risk free rate, as there is no additional risk, hence no reward above the risk free rate, giving us:

$$dS_t = r S_t dt + \sigma S_t dW_t$$

We know the stock price is lognormally distributed, so we can define a new function f = ln(S) and calculate the change in the log price using Ito Calculus:
<div class="code-example" markdown="1">
$$df(S) = f_S dS + \frac{1}{2}f_{SS}dSdS $$

$$f_S = \frac{1}{S}$$

$$f_{SS} = -\frac{1}{S^2}$$

Substitute this back into our above equation:

$$df(S) = \frac{1}{S} (r S_t dt + \sigma S_t dW_t) + \frac{1}{2}-\frac{1}{S^2} (r S_t dt + \sigma S_t dW_t)^2 $$

$$df(S) = rdt + \sigma dW_t + \frac{1}{2}-\frac{1}{S^2} (\sigma ^2 S_t^2 dt) $$

$$df(S) = (r - \frac{1}{2} \sigma ^2)dt + \sigma dW_t $$

Now we substitute in the actual function on the left side f = Ln(S(t)):

$$Ln(S_t) - Ln(S_0) = (r - \frac{1}{2} \sigma ^2)t + \sigma W_t  $$

$$Ln(\frac{S_t}{S_0})= (r - \frac{1}{2} \sigma ^2)t + \sigma W_t  $$

$$\frac{S_t}{S_0}= e^{(r - \frac{1}{2} \sigma ^2)t + \sigma W_t }$$

$$S_t= S_0 e^{(r - \frac{1}{2} \sigma ^2)t + \sigma W_t}$$
</div>

The above is our stock price process, which we can use to calculate the risk neutral value of any stock price in the future. 
