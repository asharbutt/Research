---
layout: default
title: Stationarity and Other Concepts
parent: Introductory Concepts
grand_parent: Econometrics
has_children: false
mathjax: true
nav_order: 1
---

# Stationarity
Let $${X_t}$$ be a collection of random variables which represent the value of a time series at some time t. Stationarity means that the probabilistic properties of a time series $${X_t}$$ will not change with time. There are 2 types of stationarities: strict and weak. 

## Strict Stationarity
Strict stationarity states that the joint distribution of all the random variables in a time series $$[X_t] = (X_1, X_2,...,X_n)$$ is the same as the joint distribution of the same time series but lagged for some integer value h $$[X_{t+h}] = (X_{1+h}, X_{2+h},...,X_{n+h})$$ This means that if we take the time series and shift it for some random time i.e. move back in time, then the join distribution of the shifted series should be exactly the same as what we had originally.
