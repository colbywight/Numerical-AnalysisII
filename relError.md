# Solution to Differential Equations Software Manual Entry


**Routine Name:**           relError

**Author:** Colby Wight

**Language:** C++

**Description/Purpose:** This routine will compute the relative error between the exact number solution to a math problem and its approximation.

**Input:** xBar and x: These are both input as double for precision. xBar is a number represting the exact solution of some math problem. x is some approximation of xBar.

**Output:** This routine returns a double precision value of the relative error in the approximation.

**Usage/Example:** This routine was run on two sets of numbers to represent the concept of relative error. Once on a set of numbers close to one, one once on a set of larger numbers. A condition of relative error is that we must know the exact solution to a problem and that it must not be equal to zero. The tested code and output: 

```C++
    cout << "Relative error in 1 and 1.1: " << relError(1, 1.1) << endl;
    cout << "Relative error in 100 and 100.1: " << relError(100, 100.1) << endl;
```

Output from the lines above:
```C++
    Relative error in 1 and 1.1: 0.1
    Relative error in 100 and 100.1: 0.001
```
Thus as we can calculate, these two sets of numbers will have the same absolute error (absolute difference), but the relative error is much less in the second set of larger numbers. 

**Implementation/Code:** The following is the code for relError():

```C++

    // This function in C++ will return the relative error in a number and
    // it's approximation
    // Inputs:
    // xBar - a number represting the exact solution of some math problem
    /// x - some approximation of xBar
    double relError(double xBar, double x){
    return ( abs(x - xBar) / abs(xBar));
    }
```

**Last Modified:** January/2018
