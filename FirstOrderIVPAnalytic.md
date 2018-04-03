# Software Manual Entry

**Routine Name:**  firstOrderIVPAnalyticSolution

**Author:** Colby Wight

**Language:** C++

**Description/Purpose:**  This routine computes the anlytic solution for the initial value problem u' = lambda u with initial condition u(0) = alpha. We want to be abel to get a value for the exact solution for the problems at any point in the domain of interest. 

**Input:** This method will take in thre parameters: alpha, t, and lambda. alpha and lambda can be set to any value and then t is where we want to evaluate at. 

**Output:** This method outputs a value in the form of a double. This value denotes the exact solution for the problem at any poin in the domain of interest. 

**Usage/Example:** 

```C++
     int main() {
    cout << "First order IVP: " << firstOrderIVPAnalyticSolution(1, 2, -1) << endl;
    return 0;
    }
```

Sample Output:

```C++
     First order IVP: 0.135335
```

**Implementation/Code:** The code is as follows:
```C++
 // Homework 5 Problem 1
// First order IVP
double firstOrderIVPAnalyticSolution(double alpha, double t, double lambda){
    return alpha * exp(lambda * t);
}
```
**Last Modified:** April/2018
