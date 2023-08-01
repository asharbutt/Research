---
layout: default
title: Simple Monte Carlo Simulator in C++
parent: Computational Methods
nav_order: 2
---
# Simple Monte Carlo Simulator
We build a simple simulator for a Geometric Brownian Motion. We first start with a class family of processes that we want to use in simulation. We create the following base and derived classes for a GBM and CEV process:

``` c++
class processType
{
private:
public:
    virtual double Evaluate(double S) = 0;
};

class GBM_process:public processType
{
private:
    double mean; double sigma; double dt;
public:
    GBM_process (double mean_, double dt_, double sigma_): mean(mean_), sigma(sigma_), dt(dt_){}; //Construct the class using the main parameters so we dont have to keep passing them into other classes
    
    virtual double Evaluate(double S){
        double dS = 0;
        
        std::random_device rd;
        std::mt19937 gen(rd());
        
        std::normal_distribution<float> d(0, 1);
        double dW = d(gen);
        
        dS = mean * dt * S + sigma * S * sqrt(dt) * dW;
        return dS;
    }};

class CEV_process:public processType
{
private:
public:
    double Evaluate(double mean, double dt, double sigma, double S, double alpha){
        double dS = 0;
        
        std::random_device rd;
        std::mt19937 gen(rd());
        
        std::normal_distribution<float> d(0, 1);
        double dW = d(gen);
        
        dS = mean * dt * S + sigma * (S^alpha) * sqrt(dt) * dW;
        return dS;
    }};
```
