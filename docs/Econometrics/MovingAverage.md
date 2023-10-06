---
layout: default
title: Moving Average Process
parent: Introductory Concepts
grand_parent: Econometrics
has_children: false
mathjax: true
nav_order: 1
---
# Moving Averages
A MOving average process of order q is a process where the time series is regressed on lagged white noise variables, and can we written as:

$$X_t = Z_t + \theta_1 Z_{t-1} + \theta_2 Z_{t-2} + ... $$

where:

$$Z_t \sim WN(0,\sigma^2)$$

## MA(1)

MA(1) can be written as:

$$X_t = Z_t + \theta Z_{t-1}$$

### Parameters of MA(1)
The expectation of this process is 0, given that both random variables on the right side have a mean of 0 (they are white noise). The covariance can be derived as the following:

1. $$\gamma _X (t, t+1) = E[(X_t - E(X_t))(X_{t+1} - E(X_{t+1}))]$$

2. $$\gamma _X (t, t+1) = E[(X_t)(X_{t+1})]$$

3. $$\gamma _X (t, t+1) = E[(Z_t + \theta Z_{t-1})(Z_{t+1} + \theta Z_{t})]$$

4. $$\gamma _X (t, t+1) = E[Z_tZ_{t+1}] + \theta E[Z_tZ_{t}] +  \theta E[Z_{t-1}Z_{t+1}] + \theta^2E[Z_{t-1} Z_{t}]$$

5. $$\gamma _X (t, t+1) = \theta E[Z_tZ_{t}] $$

6. $$\gamma _X (t, t+1) = \theta \sigma^2 $$

Line 4 to 5 comes from the fact that white noise are independent, meaning the expectation of a lagged product is 0. 

For lag 0:

1. $$\gamma _X (t, t) = E[(X_t - E(X_t))(X_t - E(X_t))]$$

2. $$\gamma _X (t, t) = E[(Z_t + \theta Z_{t-1})(Z_t + \theta Z_{t-1})]$$

3. $$\gamma _X (t, t) = E[Z_t^2] + \theta E[Z_{t-1}Z_t] + \theta^2 E[Z_{t-1}^2]$$

4. $$\gamma _X (t, t) = \sigma^2 + \theta^2 \sigma^2$$

5. $$\gamma _X (t, t) = \sigma^2 (1 + \theta^2 $$

