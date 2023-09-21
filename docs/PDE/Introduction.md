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

The Black-Scholes PDE is a 2nd order PDE. 

## Linearity
Just like ODE's, we can seperate PDE's into Linear and Non-Linear categories:

### Linear
In order for a PDE to be linear, all derivatives have to be linear and can only be products of the independent variables at most (i.e they cannot be products of the dependent variable):
Examples of Linear PDEs:
$$\frac{\delta^2 u}{\delta x^2}(x-a) + \frac{\delta^2 u}{\delta y^2}(y-b) - ua = 0$$

$$\frac{\delta^2 u}{\delta x^2} + \frac{\delta u}{\delta y} + \frac{\delta u}{\delta x} = 0$$

### Semi-linear
For a PDE to be semilinear, the highest order derivatives have to be linear and only products of the independent variables at most

Examples of Semi-linear PDEs:
$$\frac{\delta^2 u}{\delta x^2}(x-a) + \frac{\delta^2 u}{\delta y^2}(y-b) - ua = 0$$

$$\frac{\delta^2 u}{\delta x^2} + \frac{\delta u}{\delta y}u + \frac{\delta u}{\delta x}u = 0$$

In the above, the highest order derivative (the first one) is not a product of the dependent variable, whilst the 1st order derivatives are - this is still a semi-linear PDE.

### Quasi-linear
A quasi-linear PDE is one where the highest order derivative is linear, i.e product of independent variables or lower order derivatives:

Examples of Quasi PDEs:
$$\frac{\delta^2 u}{\delta x^2}\frac{\delta u}{\delta y} + \frac{\delta u}{\delta y}u + \frac{\delta u}{\delta x}u = 0$$

## Boundary and Initial Conditions
PDE's can be solved in a space subject to conditions which specify the values of the function in those regions. A Boundary Condition sets out how the function behaves when close to those boundaries of the variables. 

Initial Conditions are normally also added in when one of the independent variables is time, such that a condition is imposed when t=0, i.e. initially. This means the values of the function are specified in all regions at t=0.

Black-Scholes PDE is one with Initial and Boundary conditions, which are normally dependent on the type of option (i.e how call is worth 0 if underlying is 0).

The Boundary conditions and Initial conditions are normally required to solve the PDE for boundary value and initial value problems. Black Scholes PDE requires a Boundary condition in order to specify the type of contract being solved for.

