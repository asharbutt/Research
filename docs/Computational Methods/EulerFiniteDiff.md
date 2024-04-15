---
layout: default
title: Finite Difference Methods - Euler Scheme (IN PROGRESS)
parent: Mini Projects C++
nav_order: 1
---
# Euler Scheme Finite Difference method (IN PROGRESS)
The Euler scheme is a simple method where we discretise the PDE. In our case, we look at the simple second order Black Scholes PDE:

$$\frac{\partial V}{\partial t} + \frac{\partial V}{\partial S}rS + \frac{1}{2}\frac{\partial^2 V}{\partial S^2}\sigma^2 S^2 = rV $$

The scheme is quite unstable for large values of imax and jmax, hence we keep it below 15 for each. Interpolation for final option value to come soon, as well as a Crank-Nicholson implementation
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

## C++ code for Scheme
``` c++
class finiteDiff_EuropeanOption
{
private:
    double T;
    double r;
    double q;
    double sigma;
    double S_0;
    double sMax;
    double sMin;
    double dS;
    double dt;
    double X;

    int imax;
    int jmax;

    Matrix grid_call;
    Matrix grid_put;//Will store all of the grid values -  grid will be huilt backwards, i.e. first vector in this matrix will be at time T
    std::vector<double> previousVector; //This will hold the i+1 vector of values
public:
    finiteDiff_EuropeanOption(double t_, double r_, double q_, double sigma_, double S_0, double i_max_, double j_max_, double s_max, double s_min, double X_) : T(t_), r(r_), q(q_), sigma(sigma_), S_0(S_0), imax(i_max_), jmax(j_max_), sMax(s_max), X(X_), sMin(s_min) {
        dS = (sMax - sMin) / jmax;
        dt = T / imax;
    }

    void evaluateGrid_call() {
        //Resize the grid:
        grid_call.resize(jmax + 1, imax + 1);
        
        //Final vector will be filled using terminal condition: max(S - K)
        for (int j = jmax; j >= 0; j--) {
            grid_call(j, imax ) = std::max((sMin + (dS * j)) - X, 0.00);
        }

        
        for (int i = imax - 1; i >= 0; i--) {
            previousVector = grid_call.returnCol(i + 1);
            double nodeVal = 0.0;
            for (int j = jmax; j >= 0 ; j--) {
                if (j == jmax) { //This if statement checks if we are at a boundary, and then uses boundary condition
                    nodeVal = std::max(sMax - (X * exp(-r *(T-(i)*dt))), 0.0); 
                }
                else if (j == 0) { //This if statement checks if we are at a boundary, and then uses boundary condition
                    nodeVal = std::max(sMin - X, 0.0);
                }
                
                else {
                    double A = 0.5 * sigma * sigma * j * j * dt + 0.5 * r * j * dt;
                    double B = 1. - sigma * sigma * j * j * dt;
                    double C = 0.5 * sigma * sigma * j * j * dt - 0.5 * r * j * dt;
                    nodeVal = ((A * previousVector[j + 1]) + (B * previousVector[j]) + (C * previousVector[j - 1])) * (1.0 / (1.0 + r * dt));
                }

                grid_call(j, i) = nodeVal;
            }
            //end of for loop
        }
        std::vector <double> finalVector;
        finalVector = grid_call.returnCol(0);
        //End of void
    }
    void evaluateGrid_put() {

        for (int i = 0; i < imax; i++) {
            //Temporary vector to hold values of the grid at time i

            if (i == 0) { //First vector will be filled using terminal condition: max(S - K)
                for (int j = 0; j <= jmax; j++) {
                    grid_put(j, imax) = std::max(X - (sMin + (dS * j)), 0.00);

                }
                continue;
            }

            previousVector = grid_put.returnCol(i - 1);
            double nodeVal = 0.0;
            for (int j = 0; j <= jmax; j++) {

                if (j == 0) { //This if statement checks if we are at a boundary, and then forces a boundary condition
                    nodeVal = std::max(sMin - X, 0.0);
                }
                else if (j == jmax) {
                    nodeVal = std::max(sMax - X * exp(-r * (T - (imax - i) * dt)), 0.0);
                }
                else {
                    double A = 0.5 * sigma * sigma * j * j * dt + 0.5 * r * j * dt;
                    double B = 1. - sigma * sigma * j * j * dt;
                    double C = 0.5 * sigma * sigma * j * j * dt - 0.5 * r * j * dt;
                    nodeVal = ((A * previousVector[j + 1]) + (B * previousVector[j]) + (C * previousVector[j - 1])) * (1.0 / (1.0 + r * dt));
                }

                grid_put(j, i) = nodeVal;
            }
            //end of for loop
        }
        //End of void
    }

};
```


You can simply call the above class using the following:

``` c++
double T = 1.0;
double r = 0.05;
double q = 0.00;
double sigma = 0.4;
double S_0 = 20.0;
double S_min = 0.0;
double S_max = 2 * S_0;

int i_max = 10;
int j_max = 20;
double X = 5.0;

finiteDiff_EuropeanOption f(T, r, q, sigma, S_0, i_max, j_max, S_max, S_min, X);
f.evaluateGrid_call();
```
