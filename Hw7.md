This is a write up for homework 7.

Problem 1: Write a code that will compute the solution of the heat equation using the explicit Euler method
for time-stepping and the usual second order spatial discretization as discussed in class. Make sure the time step
honors the stability condition for parabolic problems

The code software manual entry can be found [here.](./ExplicitEuler.md)

The following was run with the results below:

```C++
// heat equation example
    explicitEuler(1, 1, 2, .001, "heatEqn");
    explicitEuler(1, 1, 3.5, .001, "heatEqn");
    
    Approximation of the Soultion of heatEqn at 2: 4.2505
    Approximation of the Soultion of heatEqn at 3.5: 15.7047
```

Problem 2: Repeat the work in Problem 1 using your implicit Euler method. Compare the results to those in
Problem 1

```C++
// heat equation example
    implicitEuler(1, 1, 2, .001, "heatEqn");
    implicitEuler(1, 1, 3.5, .001, "heatEqn");
    
    Approximation of the Soultion of heatEqn at 2: 4.0124
    Approximation of the Soultion of heatEqn at 3.5: 14.5039
```

Problem 3: Instead of using the step 10−3
in your implicit Euler method, try increasing the size of the step to
10−2 and so on. What happens to the accuracy of your results?

```C++

 // heat equation with different h values
    explicitEuler(1, 1, 2, .01, "heatEqn");
    explicitEuler(1, 1, 3.5, .01, "heatEqn");
    cout << endl;

    explicitEuler(1, 1, 2, .1, "heatEqn");
    explicitEuler(1, 1, 3.5, .1, "heatEqn");
    
    Approximation of the Soultion of heatEqn at 2: 4.18052
    Approximation of the Soultion of heatEqn at 3.5: 15.5629

    Approximation of the Soultion of heatEqn at 2: 3.59981
    Approximation of the Soultion of heatEqn at 3.5: 13.3257
```

Problem 4: Use the predictor-corrector method you developed in Homework 5 on the same problems as in
Problem 1. Compare your results to the results from the implicit and explicit Euler methods.

```C++
  // heat equation example
    predictorCorrector(1, 1, 2, .001, "heatEqn");
    predictorCorrector(1, 1, 3.5, .001, "heatEqn");
    
    Approximation of the Soultion of heatEqn at 2: 4.0012
    Approximation of the Soultion of heatEqn at 3.5: 14.4018
```

The results are better still.

Problem 5: Use the fourth order Runge Kutta method you developed earlier in class to try the same problems.
Compare the results and also determine the difference in time needed to use the Runge Kutta method of order
four.

```C++
  // heat equation example
    rk4(1, 1, 2, .001, "heatEqn");
    rk4(1, 1, 3.5, .001, "heatEqn");
    
    Approximation of the Soultion of heatEqn at 2: 4.0012
    Approximation of the Soultion of heatEqn at 3.5: 14.4018
```
