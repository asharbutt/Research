---
layout: default
title: Combinatorial Principles
parent: Basics
grand_parent: Probability Theory
mathjax: true
permalink: /docs/Probability Theory/Basics/Combinatorics/
nav_order: 1
---

# Combinatorial Principles

## Definitions
We start with simple definitions:

<div class="code-example" markdown="1">
- Permutation: This is where we care about the ordering of items, such that a list backwards and forwards is not the same thing. 
example: {1,2,3} != {3,2,1} in a permutation, they are considered two different outcomes. This is where ordering matters.

- Combination: Where ordering does not matter at all. This can also be called unordered.
- example: {1,2,3} = {3,2,1}

In context, they are used for different scenarios.
</div>

### Ordered with replacement
Here, let us assume we want to create a combination of k items from a list of n items, such that ordering matters, for example if we select {1,2} and {2,1} they count as two different lists. 

How do we represent this? This is given by:

$$n^k$$

So to find the number of combinations such that ordering matters and we replace the item after selecting it, we use the above to calculate the number of such combinations.

### Ordered without replacement - Permutation
Ordering without replacement means we care about the order (again {1,2} != {2,1} thus they are two seperate outcomes) but we do not replace the item this time. This means we should expect far fewer outcomes this time.

This can be given by:

 $$\frac{n!}{(n-k)!}$$

Where would this be used? Imagine we have a main group of n people, and we want to figure out how to create a smaller group made up of k people from the main group. How many different ways can we go about this whilst we take care of the ordering?

### Unordered without replacement
Now we do not care about ordering anymore, meaning that picking a black ball and then a white ball is the same as ppicking a white ball and a black ball. In these kind of examples, we would rather be interested in, what is the probability of getting a white and a black.

example:

A = {1,2,3} how many combinations of a list of size 2 can we create such that ordering does not matter and we do not replace?

We can see that we get:
1. 1,2
2. 1,3
3. 2,3

We no longer consider 1,2 and 2,1 as seperate outcomes, they are the same outcome.

This means that the total number of outcomes or combinations has reduced even further. We would expect that the denominator of our permutations formula is even smaller, which it is in the following:

$$\frac{n!}{n!(n-k)!}$$

This is also what builds the foundations for the Binomial distribution formula.

