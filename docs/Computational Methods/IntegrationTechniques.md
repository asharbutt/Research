---
layout: default
title: Integration Techniques in C++
parent: Computational Methods
nav_order: 1
---

# Midpoint Method
The midpoint method works by splitting the function into several intervals, getting the midpoint at each interval, and then multiplying the function value at that point by the interval to get the area of the rectanlge. The estimate of the integral is then the sum of all rectangles.

Let f(x) be a continious function on the interval [a,b], and n be the number of subintervals we want to use to estimate the area. Then $$\Delta x = \frac{b-a}{n}$$. If $$m_i$$ is the midpoint of the ith subinterval, then the estimate of the area is given by:

$$M_n = \sum _{i=1}^{n} f(m_i)\Delta x$$

We show a simple code for a class used to calculate integrals using the midpoint, trapezoid and Simpsons rule below:

```
#include <math.h>
#include <iostream>

class functions
{
public:
    virtual double Evaluate(double x) = 0;
private:
    double x;
};

class squareValue:public functions
{
public:
    virtual double Evaluate(double x){
        return x*x;
    }
};

class expoValue:public functions
{
public:
    virtual double Evaluate(double x){
        return exp(x);
    }
};
class cubeValue: public functions
{
public: virtual double Evaluate(double x){
    return x*x*x;
    }
};

class integrand
{
private:
    int numInterval;
    double subintervalLength;
    double b;
    double a;
    double integrand_value;
public:
    integrand (int n, double a_,double b_):numInterval(n), b(b_), a(a_){}
    
    double midpoint_rule(functions &func){
        
        integrand_value = 0;
        subintervalLength = (b - a)/double(numInterval);
        
        for (int i = 0; i < numInterval; i++){
            integrand_value += subintervalLength * func.Evaluate((subintervalLength/2) + a + i*subintervalLength);
        }
        return integrand_value;
    }
    
    double trapezoid_rule(functions &func){
        
        //Trapezoid rule is: T = subintervalLength/2 * [f(x_0) + 2f(x_1)+...+2f(x_n-1) + f(x_n)]
        integrand_value = 0;
        subintervalLength = (b - a)/double(numInterval);
        integrand_value = func.Evaluate(a); //The first function value
        for (int i = 1; i<numInterval; i++){
            integrand_value += 2*func.Evaluate(i*subintervalLength + a);
        }
        integrand_value += func.Evaluate(b);
        integrand_value = integrand_value*(subintervalLength/2);
        
        return integrand_value;
    }
    
    double simpsons_rule(functions &func){
        integrand_value = 0;
        subintervalLength = (b - a)/double(numInterval);
        
        
        return integrand_value;
    }
    
};

int main(){
    test_function f;
    
    integrand i(100,-5.0,4.0);
    
    double value = i.midpoint_rule(f);
    double value_2 = i.trapezoid_rule(f);
    std::cout << value << " " << value_2 << std::endl;
}

```
