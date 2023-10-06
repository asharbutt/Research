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
