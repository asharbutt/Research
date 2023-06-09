---
layout: default
title: Basics Of Probability
parent: Probability Theory
nav_order: 6
mathjax: true
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
