---
layout: default
title: Simple Monte Carlo Simulator in C++
parent: Computational Methods
nav_order: 2
---
# Simple Monte Carlo Simulator
We build a simple simulator for a Geometric Brownian Motion. We first start with a class family of processes that we want to use in simulation. This will be a simple simulator, where all parameters will be constant.
The structure will be simple:
1. We create a family of classes for our processes. The process class will be initiated with the required parameters such that we do not have to pass these into the simulator class.

We create the following base and derived classes for a GBM and CEV process:

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
        
        dS = mean * dt * S + sigma * pow(S, alpha) * sqrt(dt) * dW;
        return dS;
    }};
```
We can use Virtual function here because the only thing that we need to pass that will change over time will be the actual underlying value - this is possible because the rest of the parameters are constant. 

We then create our simulator class:

``` c++
class monteCarlo_simulator
{
private:
    double initialS;
    double simN;
    double numChanges; //How many price changes we are simulating
    
    std::vector<std::vector<double>> priceChange; //Holds the change values
    std::vector<std::vector<double>> priceValue; //Holds the actual values
    
    std::vector <double> tempPriceChange; //These are temporary arrays that we push into the above matrices
    std::vector <double> tempPriceValue;
    
    processType &process;
    
public:
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
```

When initiated, we will pass all the important parameters to the class, such as the starting value, the number of simulations, the number of intervals between the start and end of the time period as well as a reference to what specific price process we are using. This is great because we can define what process we want in our main function and just pass it into this class, so that this class does not have to be specific to each process, and can be used for any (as long as we only need to pass the underlying value for evaluation).

Our sample main class will look like the following:
``` c++
int main(){
    
    double mean = 0.2;
    double T = 1;
    double sigma = 0.2;
    double S_0 = 20;
    double intervalNum = 10;
    double dt = T/intervalNum;
    int n = 100;
    
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
            simulationPaths.width (10); simulationPaths << priceMatrix[i][j];
        }
        simulationPaths << std::endl;
    }
}
```
