---
layout: default
title: Moments and Moment Generating Functions
parent: Basics
grand_parent: Probability Theory
mathjax: true
permalink: /docs/Probability Theory/Basics/Moments/
nav_order: 6
---
# Moments 
Moments in probability are used to describe the shape of the curve and give descriptions. The kth moment for any random variable X can be given by:

$$m(k) = E[X^k]$$

The central moment, which is the moment adjusted for the mean, is given by:

$$m_2(k) = E[(X - EX)^k]$$

The standardised moment, which is the central moment adjusted for the standard deviation, is given by:

$$m_3(k) = E[(\frac{X - EX}{\sigma})^k]$$

We can use these moments to give descriptions for the shape, distribution, mass location and other details for our random variable. 

For example, the first raw moment is the mean, or central location of the distribution. The second central moment gives us the variance (or spread adjusted for the central location).

The third standardised moment gives us the skewness of the distribution - whether the tail is heavier on one side as compared to the other, it is a description of the asymmetry of the curve, For a normal distribution, the skewness is 0, as both tails are equal. A negative skewness means that the tail on the left side of the mean is thinner than the right side, so the curve is fatter on the right, whereas a positive skewness means that the tail on the right side of the mean is thinner than on the left. The odd power allows us to get values both positive or negative.

The 4th standardised moment gives us a measure of kurtosis - which is the relative size of **both** tails compared to the rest of the distribution. The even power of the standardised 4th moment means we can only get positive values for this. THe normal distribution has a kurtosis of 3 (or can be 0 in some models). A higher kurtosis means that more weight of the distribution is in the tails, thus the top of the distribution will be flatter, like a hill. Lower kurtosis on the other hand means that less of the distribution lies in the tails, and thus the peak will be higher. Kurtosis can also be thought of as the peakedness of the distribution, though this is not in the definition, and can only be thought of as an idea of what kurtosis is.

## Moment Generating Functions
We described how the moments describe characteristics of the distribution, and we will now look at what generates these moments. Moment Generating Functions, or MFGs are alternative methods of generating a distributions. The kth derivative of a MFG will allow us to get the kth important moment, and thus the MFG describes the distribution of the random variable.

We can give the kth MFG by:

$$M(k) = E[e^{kX}]$$

An important theorem of MFG is that, given that the MFG of a random variable describes the distribution of that variable, then if two random variables have the same moment generating functions, then they also have the exact same distribution.

We can also use moment generating functions to generate the distributions of combinations or transformations of random variables provided they are **independent**. In this case, the joint moment generating function is the product of individual functions:

$$M(t_1, t_2) = M_X(t_1)M_Y(t_2)$$

In the case two variables are not independent, then the joint moment generating function is given by:

$$M(t_1, t_2) = E[e^{t_1 X_1 + t_2 X_2}]$$

Whilst the dependent joint MFG looks the same as the independent product, this is not the case. For dependent variables, the product of the two individual MFG will not be the joint MFG, just like as it is in the case of dependent distributions. 


