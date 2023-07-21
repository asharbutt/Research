---
layout: default
title: Integration Techniques in C++
parent: Computational Methods
nav_order: 1
---

# Midpoint Method
The midpoint method works by splitting the function into several intervals, getting the midpoint at each interval, and then multiplying the function value at that point by the interval to get the area of the rectanlge. The estimate of the integral is then the sum of all rectangles.

Let f(x) be a continious function on the interval [a,b], and n be the number of subintervals we want to use to estimate the area. Then $$\Delta x = \frac{b-a}{n}$$. If $$m_i$$ is the midpoint of the ith subinterval, then the estimate of the area is given by:

$$M_n = \sum _{i=1}{n} f(m_i)\Delta x$$
