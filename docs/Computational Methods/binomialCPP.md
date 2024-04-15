---
layout: default
title: Binomial Tree Option Pricing (IN PROGRESS)
parent: Mini Projects C++
nav_order: 1
---
# Binomial Tree Option Pricing
The below is the code to price American and European options using a CRR method (binomial tree):

## C++ Code for matrix:
``` c++


#define _USE_MATH_DEFINES
#ifndef MATRIX_H // the 'include guard'
#define MATRIX_H

#include <iostream>
#include <math.h>
#include <vector>
#include <cmath>

#include <vector>

// Class that represents a matrix
class Matrix
{
public:
    Matrix() : nRows(0), nCols(0) {}
    Matrix(int n, int m, double x = 0) : nRows(n), nCols(m), A(n* m, x) {}

    Matrix& operator=(double x)
    {
        for (unsigned i = 0; i < nRows * nCols; i++) A[i] = x;
        return *this;
    }

    // access element, indexed by (row, column)
    double operator()(int i, int j) const
    {
        return A[j + i * nCols];
    }
    //Resizing matrix, dont forget to update the private variables!!
    void resize(int i, int j)
    {
        A.resize(i * j, 0);
        nRows = i;
        nCols = j;
    }
    // access element, indexed by (row, column) 
    double& operator()(int i, int j)
    {
        return A[j + i * nCols];
    }
    //Return column of matrix:
    std::vector <double> returnCol(int n){
        std::vector <double> Column;
        for (int i = 0; i < nRows; i++) {
            Column.push_back(A[n + i * nCols]);
        }
        return Column;
    }

    std::vector <double> returnRow(int m) {
        std::vector <double> Row;
        for (int i = 0; i < nRows; i++) {
            Row.push_back(A[i + m * nCols]);
        }
        return Row;
    }
    int Rows() const { return nRows; }
    int Cols() const { return nCols; }

private:
    unsigned int nRows, nCols;
    std::vector<double> A;
};

```

## C++ Code for matrix:
``` c++
class binomialPricer
{
private:
    int timeSteps;
    double T;
    double r;
    double S_0;
    double sigma;
    double deltaT;
    double strike;

    double up;
    double down;
    double p;

    Matrix underlyingValue;
    Matrix europeanOptionValueCall;
    Matrix europeanOptionValuePut;
    Matrix americanOptionValueCall;
    Matrix americanOptionValuePut;

public:
    binomialPricer(int timeSteps_, double T_, double r_, double S_0_, double sigma_, double strike_) : timeSteps(timeSteps_), T(T_), r(r_), S_0(S_0_), sigma(sigma_), strike(strike_) {
        deltaT = T / timeSteps;
        up = std::exp(sigma * sqrt(deltaT));
        down = std::exp(-sigma * sqrt(deltaT));
        p = (std::exp(r * deltaT) - down) / (up - down);

        std::cout << "Initializing Tee..." << std::endl;
        initializeTree();
    }

    void initializeTree() { //Initialize the tree and fill underlying values

        underlyingValue.resize(timeSteps + 1, timeSteps + 1);
        int counter = 0; //Additional counter for odd positions in the lattice

        underlyingValue(0,0) = S_0;
        //Fill the underlying value matrix with the stock values:
        //With vector matrices, the first index selects the initial vector, so the column, and the second index selects an element from that vector, i.e. the row!!!
        for (int n = 1; n <= timeSteps; n++) {
            counter = 0;
            for (int m = 0; m <= n; m++) {
                if (m < n) {
                    underlyingValue(m, n) = underlyingValue(m,n-1) * up;
                }if (m == n) {
                    underlyingValue(m, n) = underlyingValue(m-1,n-1) * down;
                }
            }
        }
        std::cout << "Tree Initialization complete!" << std::endl;
    }

    double priceEuropeanCall() {
        europeanOptionValueCall.resize(timeSteps + 1, timeSteps + 1);

        //Have to work backwards on the tree here instead of forwards
        //Initialize the final payoff:
        for (int i = 0; i <= timeSteps; i++) {
            europeanOptionValueCall(i, timeSteps) = std::max(underlyingValue(i, timeSteps) - strike, 0.0);
        }
        std::cout << "Final Option Payoff complete!" << std::endl;
        for (int i = timeSteps - 1; i >= 0; i--) {
            if (i == 0) {
                europeanOptionValueCall(0, 0) = std::exp(-r * deltaT) * (europeanOptionValueCall(0, i+1) * p + europeanOptionValueCall(1, i+1) * (1 - p));

            }
            else {
                for (int j = 0; j < timeSteps; j++) {
                    europeanOptionValueCall(j,i) = std::exp(-r * deltaT) * (europeanOptionValueCall(j, i+1) * p + europeanOptionValueCall(j+1, i+1) * (1 - p));
                }
            }
        }
        std::cout << "Call Option Tree Completed!" << std::endl;
        return europeanOptionValueCall(0,0);
    }

    double priceEuropeanPut() {
        europeanOptionValuePut.resize(timeSteps + 1, timeSteps + 1);
        //Have to work backwards on the tree here instead of forwards!!
        //Initialize the final payoff:
        for (int i = 0; i <= timeSteps; i++) {
           europeanOptionValuePut(i, timeSteps) = std::max(strike - underlyingValue(i, timeSteps), 0.0);
        }
        std::cout << "Final Option Payoff complete!" << std::endl;
        for (int i = timeSteps - 1; i >= 0; i--) {
            if (i == 0) {
                europeanOptionValuePut(0,0) = std::exp(-r * deltaT) * (europeanOptionValuePut(0, i + 1) * p + europeanOptionValuePut(1, i + 1) * (1 - p));

            }
            else {
                for (int j = 0; j < timeSteps; j++) {
                    europeanOptionValuePut(j, i) = std::exp(-r * deltaT) * (europeanOptionValuePut(j, i + 1) * p + europeanOptionValuePut(j+1, i+1) * (1 - p));
                }
            }
        }
        std::cout << "Put Option Tree Completed!" << std::endl;
        return europeanOptionValuePut(0,0);
    }

    double priceAmericanCall() {
        americanOptionValueCall.resize(timeSteps + 1, timeSteps + 1);

        //Have to work backwards on the tree here instead of forwards!!
        //Initialize the final payoff:
        for (int i = 0; i <= timeSteps; i++) {
            americanOptionValueCall(i, timeSteps) = std::max(underlyingValue(i, timeSteps) - strike, 0.0);
        }
        std::cout << "Final Option Payoff complete!" << std::endl;
        for (int i = timeSteps - 1; i >= 0; i--) {
            if (i == 0) {
               americanOptionValueCall(0,0) = std::max(std::exp(-r * deltaT) * (americanOptionValueCall(0, i+1) * p + americanOptionValueCall(1, i+1) * (1 - p)), std::max(underlyingValue(0,0) - strike, 0.0));

            }
            else {
                for (int j = 0; j < timeSteps; j++) {
                    americanOptionValueCall(j,i) = std::max(std::exp(-r * deltaT) * (americanOptionValueCall(j, i+1) * p + americanOptionValueCall(j+1,i+1) * (1 - p)), std::max(underlyingValue(j,i) - strike, 0.0));
                }
            }
        }
        std::cout << "Call Option Tree Completed!" << std::endl;
        return americanOptionValueCall(0,0);
    }

    double priceAmericanPut() {
        americanOptionValuePut.resize(timeSteps + 1, timeSteps + 1);
        //Have to work backwards on the tree here instead of forwards!!
        //Initialize the final payoff:
        for (int i = 0; i <= timeSteps; i++) {
            americanOptionValuePut(i, timeSteps) = std::max(strike - underlyingValue(i, timeSteps), 0.0);
        }
        std::cout << "Final Option Payoff complete!" << std::endl;
        for (int i = timeSteps - 1; i >= 0; i--) {
            if (i == 0) {
                americanOptionValuePut (0,0) = std::max(std::exp(-r * deltaT) * (americanOptionValuePut(0, i + 1) * p + americanOptionValuePut(1, i + 1) * (1 - p)), std::max(strike - underlyingValue(0, 0), 0.0));

            }
            else {
                for (int j = 0; j < timeSteps; j++) {
                    americanOptionValuePut(j,i) = std::max(std::exp(-r * deltaT) * (americanOptionValuePut(j, i+1) * p + americanOptionValuePut(j+1,i+1) * (1 - p)), std::max(strike - underlyingValue(j,i), 0.0));
                }
            }
        }
        std::cout << "Put Option Tree Completed!" << std::endl;
        return americanOptionValuePut(0,0);
    }


};
```

You can call this class using the following:
``` c++
int main() {

    int timeSteps = 10;
    double T = 1;
    double r = 0.01;
    double S_0 = 100;
    double sigma = 0.2;
    double strike = 95.0;

    binomialPricer option(timeSteps, T, r, S_0, sigma, strike);
    std::cout << "Option Value is: " << european.priceAmericanPut() << std::endl;

    return 0;
}
```
