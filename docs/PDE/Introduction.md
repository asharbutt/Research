---
layout: default
title: Introduction to PDE
parent: PDE
mathjax: true
nav_order: 1
---

# Introduction
PDE's are multivariable functions where the dependent variable is a function of more than one independent variables and their derivatives. This is what seperates it from an Ordinary Differential Equation, which is only a function of one independent variable.
They can be used to model the evolution of the dependent variable w.r.t other inputs, which are called **spatial variables**.

A simple way of representing the PDE is as a function of all the variables. Say we have a function u = u(x,y), i.e. the variable u is a function of x and y. The PDE for u can be written as $F(x,y,u,u_x, u_y, u_{xx}, u_{yy}, u_{xy}) = 0$, here, u will be a function of x, y, and the 1st and 2nd derivatives of u wrt x and y.

The order of the PDE is the highest derivative present in the equation. Examples include the below:

1st Order:
$$\frac{\delta u}{\delta x} + \frac{\delta u}{\delta y} - u = 0$$

2nd Order:
$$\frac{\delta^2 u}{\delta x^2} + \frac{\delta^2 u}{\delta y^2} - u = 0$$


