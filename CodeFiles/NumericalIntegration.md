//
//  IntegrationImplementation.cpp
//  Github C++ code
//
//  Created by Ashar Butt on 21/07/2023.
//

#include "IntegrationImplementation.hpp"
#include <math.h>
#include <iostream>

class functions
{
public:
    virtual double Evaluate(double x) = 0;
private:
    double x;
};
class standardNormalDensityFunc:public functions
{
private:
public:
    virtual double Evaluate (double x){
        return 1/sqrt(2*M_PI) * exp(-0.5*x*x);
    }
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
class test_function:public functions
{
public:
    virtual double Evaluate(double x){
        return (x*x + 4*x);
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


double test_evaluate(functions &f){
    double value = 0;
    
    value = f.Evaluate(2);
    
    std::cout << value << std::endl;
    return value;
}

int main(){
    test_function f;
    
    integrand i(100,-5.0,4.0);
    
    double value = i.midpoint_rule(f);
    double value_2 = i.trapezoid_rule(f);
    std::cout << value << " " << value_2 << std::endl;
    
    
}
