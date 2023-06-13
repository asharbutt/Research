---
layout: default
title: Basics Of Probability
parent: Basics
grand_parent: Probability Theory
mathjax: true
permalink: /docs/Probability Theory/Basics/BasicsIntroduction/
nav_order: 1
---

# The Basics of Probability Theory
## A Probability Space

A probability space is a space on which we can conduct experiments and calculate the probabiltiies of events happening within that space. In order to form a probability space, we need 3 elements to build it:

### The Infinite Set: $$\Omega$$
This is an infinite set containing all the possible outcomes. The sequences within this set are not only infinite, but also uncountably infite (Recall that in order to be countable, we can place it 1 to 1 against some other countable set, such as the real set, or the set of all integers, all of which are infinite but countable).

Each subset within this set are called events - sets of smaller outcomes. Consequently, we cannot calculate the probability if different subsets by summing them up due to the uncountable nature of the subsets.

### The sigma algebra: $$\digamma$$
A sigma algebra is a collection of subsets within the infinite set which fulfills the following conditions:
1. $$\digamma$$ contains the full set and the null set
2. For every subset in $$\digamma$$, it also contains the complement of that set: if A $$\in$$ $$\digamma$$, then $$A^C$$ $$\in$$ $$\digamma$$
3. For every sequence of subsets in $$\digamma$$, their unions also exist in $$\digamma$$

### Measureability
The idea of measurabiltiy is that whatever is measurable, it allows us to determine the value based on other information. For example, The probability measure below maps/assigns a value in the interval [0,1] (closed) to sets in a $$\sigma$$-algebra. This means that the probability measure P allows us to "measure" the probability of some subset in $$\digamma$$. 

Other examples may include a random variable X being G-measurable, meaning that the information in G is enough for us to know the value of X, we can "measure" the value of X through G.

### The Probability Measure P
The probability measure P is a function that maps the subsets within $$\digamma$$ to the interval [0,1] - in essence assigns a probability to each of the subsets within the sigma algebra. In order for P to satisfy as a probability measure, it must fulfil the following conditions:
1. The probability of the infinite set is 1 P($$\Omega$$) = 1 - this makes sense as the probability of getting the infinite set should always be 100%
2. Countable Additivity -  The Probability of the union of any sequence of sets $$A_n$$ should be the equivalent of the sum of the individual probabilities of the subsets in that sequence

Once these conditions have been satisfied, then these three building blocks are used to create the probability space ($$\Omega$$, $$\digamma$$, P)

## Random Variable
A random variable RV is a function that will map the outcome of an event (a subset) to the real line R. The value of the random variable X is determined through random experiments, for example throwing a coin and assigning 1 or 0 depending on the outcome. In infinite probability spaces like $$\Omega$$, the probability of X taking a specific value is 0, hence we usually consider the probability that X is in a certain subset rather than a specific element of a subset. 

## The distribution measure
The distribution measure of X is the probability measure that assigns each Borel subset on R a mass equivalent to the probability of X being in that Borel subset. 
For example, if P{X $$\in$$ B} = 0.5, where B = [2,5], then the distribution measure $$ \mu_X (B) $$ is equal to 0.5 - basically the distribution measure just assigns a probability to a distribution on the real line, for example a Borel subset, which is an interval rather than a specific value.

In simpler terms, the distribution measure $$\mu_X (B)$$ is a collection of probabilities on the Borel Subset B of X on the real line R. 


