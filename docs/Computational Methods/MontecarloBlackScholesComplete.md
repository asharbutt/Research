---
layout: default
title: Monte Carlo & Black Scholes Complete Code
parent: Computational Methods
nav_order: 3
---
# Monte Carlo and Black Scholes
We finalise by including a Black Scholes function for comparison. The normal CDF is calculated using our own integration class from the previous section. We do not include dividends in the code, however, this can easily be added in - we subtract a dividend yield (if continious) from the mean in the stochastic process, and multiply the initial stock price by $$e^{-qT}$$ in the black scholes class. For a discrete dividend, if known, we can calculate the present value and subtract from the initial stock price to adjust.

``` c++
//
//  Monte Carlo Simulator.cpp
//  Github C++ code
//
//  Created by Ashar Butt on 31/07/2023.
//

#include "Monte Carlo Simulator.hpp"
#include <iostream>
#include <numeric>
#include <iterator>
#include <algorithm>
#include <iomanip>
#include <math.h>
#include <vector>
#include <ctime>
#include <fstream>
#include <cstdlib>
#include <chrono>
#include <limits>
#include <random>
#include <map>
#include <cmath>
#include <limits>
#include <iomanip>
#include <sstream>

class Integrand
{
public:
    virtual double Evaluate (double x) = 0;
};

class normalCDF: public Integrand
{
public:
    virtual double Evaluate (double x){
        return 1/sqrt(2*M_PI)*exp(-(x*x)*0.5);
    }
};

class integration
{
private:
    int numInterval;
    double subintervalLength;
    double b;
    double a;
    double integrand_value;
public:
    integration (int n, double a_,double b_):numInterval(n), b(b_), a(a_){}
    
    double midpoint_rule(Integrand &func){
        
        integrand_value = 0;
        subintervalLength = (b - a)/double(numInterval);
        
        for (int i = 0; i < numInterval; i++){
            integrand_value += subintervalLength * func.Evaluate((subintervalLength/2) + a + i*subintervalLength);
        }
        return integrand_value;
    }
    
    double trapezoid_rule(Integrand &func){
        
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
};

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
        
        dS = mean * dt * S + sigma * pow(S, alpha) * sqrt(dt) * dW;
        return dS;
    }};



class monteCarlo_simulator
{
private:
    std::vector<std::vector<double>> priceChange; //Holds the change values
    std::vector<std::vector<double>> priceValue; //Holds the actual values
    
    std::vector <double> tempPriceChange; //These are temporary arrays that we push into the above matrices
    std::vector <double> tempPriceValue;
    
    processType &process;
    
public:
    double initialS;
    double simN;
    double numChanges; //How many price changes we are simulating
    
    monteCarlo_simulator(double S_0, double n, double intervalNum ,processType &process_): initialS(S_0), simN(n), process(process_), numChanges(intervalNum){}
    double simulate(){
        //Set the first value of the matrix to be
        for (int i = 0; i < simN; i++){
            tempPriceChange.push_back(0);
            tempPriceValue.push_back(initialS);
            
            for (int j = 1; j <= numChanges; j++){ //start from index 1 because the first index (0) is already populated
                double changeVal = process.Evaluate(tempPriceValue[j-1]);
                double newValue = tempPriceValue[j-1] + changeVal;
                
                tempPriceChange.push_back(changeVal);
                tempPriceValue.push_back(newValue);
            }
            priceChange.push_back(tempPriceChange);
            priceValue.push_back(tempPriceValue);
            
            tempPriceChange.clear();
            tempPriceValue.clear();
        }
        return 0;
    }
    std::vector<std::vector<double>> returnSim(){
        return priceValue;
    }
};

class monteCarlo__European_OptionPricer
{
private:
    monteCarlo_simulator f;

    std::vector<double> finalPrices;
    std::vector<double> callPayoff;
    std::vector<double> putPayoff;
    std::vector<std::vector<double>> priceMatrix;
    
    double callPrice;
    double putPrice;
    double k;
public:
    monteCarlo__European_OptionPricer(monteCarlo_simulator &f_, double strike): f(f_), k(strike){
        priceMatrix = f.returnSim();
        for (int i = 0; i < f.simN; i++){
            finalPrices.push_back(priceMatrix[i].back());
        }
    };
    double callOption(){
        for (int i = 0; i < finalPrices.size(); i++){
            callPayoff.push_back(std::max((finalPrices[i] - k), 0.0));
        }
        callPrice =  std::accumulate(callPayoff.begin(), callPayoff.end(), 0.0) / callPayoff.size();
        return callPrice;
    }
    double putOption(){
        for (int i = 0; i < finalPrices.size(); i++){
            putPayoff.push_back(std::max((k - finalPrices[i]), 0.0));
        }
        putPrice =  std::accumulate(putPayoff.begin(), putPayoff.end(), 0.0) / putPayoff.size();
        return putPrice;
    }
};

class blackScholes
{
private:
    double S_0; double k; double r; double sigma; double T;
public:
    blackScholes(double S_0_, double k_, double r_, double sigma_, double T_):S_0(S_0_), k(k_), r(r_), sigma(sigma_), T(T_){}
    double callOption(){
        double d1 = (log(S_0/k) + (r + sigma*sigma*0.5)*T)/(sigma * sqrt(T));
        double d2 = d1 - sigma*sqrt(T);
        
        normalCDF c;
        integration d1_(10000, 0, d1);
        integration d2_(10000, 0, d2);
        
        double Nd1 = 0.5 + d1_.trapezoid_rule(c);
        double Nd2 = 0.5 + d2_.trapezoid_rule(c);
        
        double callValue = S_0 * Nd1 - k*exp(-r*T)*Nd2;
        return callValue;
    }
    double putOption(){
        double d1 = (log(S_0/k) + (r + sigma*sigma*0.5)*T)/(sigma * sqrt(T));
        double d2 = d1 - sigma*sqrt(T);
        
        normalCDF c;
        integration d1_(10000, 0, d1);
        integration d2_(10000, 0, d2);
        
        double Nd1 = 0.5 + d1_.trapezoid_rule(c);
        double Nd2 = 0.5 + d2_.trapezoid_rule(c);
        
        double callValue = k*exp(-r*T)*(1.0 - Nd2) - S_0*(1.0 - Nd1);
        return callValue;
    }
    
};

int main(){
    
    double mean = 0.02;
    double T = 1.0;
    double sigma = 0.2;
    double S_0 = 20.0;
    double intervalNum = 50.0;
    double dt = T/intervalNum;
    int n = 10000;
    double K = 25.0;
    double r = 0.03;
    
    GBM_process p(mean, sigma, dt);
    monteCarlo_simulator f(S_0, n, intervalNum, p);
    f.simulate();
    
    //retrives the price matrix from the class
    std::vector <std::vector<double>> priceMatrix = f.returnSim();
    
    //Outputs the matrix to a txt file
    std::ofstream simulationPaths;
    simulationPaths.open ("SimulationPaths.txt");
    
    for (int i = 0; i < intervalNum; i++){
        for (int j = 0; j < n; j++){
            simulationPaths.width (10); simulationPaths << priceMatrix[j][i];
        }
        simulationPaths << std::endl;
    }
    
    monteCarlo__European_OptionPricer a(f, K);
    double callprice = a.callOption();
    double putprice = a.putOption();
    
    blackScholes d(S_0, K, r, sigma, T);
    double blackScholesCall = d.callOption();
    double blackScholesPut = d.putOption();
    std::cout << "Monte Carlo Simulation Call Price: " << callprice << " Black Scholes Call Price: " << blackScholesCall << std::endl;
}


```
