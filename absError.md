# Solution to Differential Equations Software Manual Entry


**Routine Name:**           absError

**Author:** Colby Wight

**Language:** C++

**Description/Purpose:** This routine will compute the absolute error between the exact number solution to a math problem and its approximation.

**Input:** xBar and x: These are both input as double for precision. xBar is a number represting the exact solution of some math problem. x is some approximation of xBar.

**Output:** This routine returns a double precision value of the absolute error in the approximation.

**Usage/Example:** This routine was run on two sets of numbers to represent the concept of absolute error. Once on a set of numbers close to one, and once on a set of larger numbers. The tested code and output: 

```C++
    cout << "Absolute error in 1 and 1.1: " << absError(1, 1.1) << endl;
    cout << "Absolute error in 100 and 100.1: " << absError(100, 100.1) << endl;
```

Output from the lines above:
```C++
    Absolute error in 1 and 1.1: 0.1
    Absolute error in 100 and 100.1: 0.1
```
Thus as we see that the absolute error in both number is the same. It is noted that the relative error is not. 

**Implementation/Code:** The following is the code for absError():

```C++
    // This function in C++ will return the absolute error in a number and
    // it's approximation
    // Inputs:
    // xBar - a number represting the exact solution of some math problem
    // x - some approximation of xBar
    double absError(double xBar, double x){
    return abs(x - xBar);
    }
```

**Last Modified:** January/2018
