This is the write up for homework 6.

Problem 1: Replicate the numerical experiments in Examples 7.1, 7.2, and 7.3 on pages 149 through 152. Note
that in the third example, you should run the same step sizes as in the book in your Explicit Euler method.

The code software manual entry can be found [here.](./ExplicitEuler.md)

The following was run with the results below:

```C++
   // evaluate for pi/2
    explicitEuler(0, 1, 1.57, .001, "f7.1");
    // evaluate for pi
    explicitEuler(0, 1, 3.14, .001, "f7.1");
    // evaluate for 3pi/2
    explicitEuler(0, 1, 4.7124, .001, "f7.1");
    // evaluate for 2pi
    explicitEuler(0, 1, 6.283185, .001, "f7.1");

    cout << endl;

    // evaluate for pi/2
    explicitEuler(0, 1, 1.57, .001, "f7.2");
    // evaluate for pi
    explicitEuler(0, 1, 3.14, .001, "f7.2");
    // evaluate for 3pi/2
    explicitEuler(0, 1, 4.7124, .001, "f7.2");
    // evaluate for 2pi
    explicitEuler(0, 1, 6.283185, .001, "f7.2");

    cout << endl;

    // evaluate for pi/2
    explicitEuler(0, 1, 1.57, .001, "f7.3");
    // evaluate for pi
    explicitEuler(0, 1, 3.14, .001, "f7.3");
    // evaluate for 3pi/2
    explicitEuler(0, 1, 4.7124, .001, "f7.3");
    // evaluate for 2pi
    explicitEuler(0, 1, 6.283185, .001, "f7.3");
    
    Approximation of the Soultion of f7.1 at 1.57: 0.00129641
    Approximation of the Soultion of f7.1 at 3.14: -0.999998
    Approximation of the Soultion of f7.1 at 4.7124: -0.000888897
    Approximation of the Soultion of f7.1 at 6.28318: 1

    Approximation of the Soultion of f7.2 at 1.57: 0.00224641
    Approximation of the Soultion of f7.2 at 3.14: -0.993983
    Approximation of the Soultion of f7.2 at 4.7124: 0.0271051
    Approximation of the Soultion of f7.2 at 6.28318: 1.13313

    Approximation of the Soultion of f7.3 at 1.57: -2.30816e+58
    Approximation of the Soultion of f7.3 at 3.14: -2.2376e+123
    Approximation of the Soultion of f7.3 at 4.7124: -2.62472e+188
    Approximation of the Soultion of f7.3 at 6.28318: 2.79893e+253
   
```

We see that the method works very well for 7.1 and 7.2 the more simple trig functions. but when we use a lambda value of -2100 in 7.3 we get huge answers

Problem 2: Repeat the work in Problem 1 using your implicit Euler method. Compare the results to those in
Problem 1.

The code software manual entry can be found [here.](./ImplicitEuler.md)

The following was run with the results below:

```C++
 
    // evaluate for pi
    implicitEuler(0, 1, 3.14, .001, "f7.1");
    
    cout << endl;

    // evaluate for pi
    implicitEuler(0, 1, 3.14, .001, "f7.2");

    cout << endl;

    // evaluate for pi
    explicitEuler(0, 1, 3.14, .001, "f7.3");
  
    
   
    Approximation of the Soultion of f7.1 at 3.14: -0.99999

    Approximation of the Soultion of f7.2 at 3.14: -0.996785

    Approximation of the Soultion of f7.3 at 3.14: -1.09789
   
```

We see here both implicit euler works as well as euler on the easy problems and does much better on the harder. 

Problem 3: Instead of using the step 10−3
in your implicit Euler method, try increasing the size of the step to
10−2 and so on. What happens to the accuracy of your results?

```C++
    // now use larger step size
    // evaluate for pi/2
    explicitEuler(0, 1, 1.57, .01, "f7.1");
    // evaluate for pi
    explicitEuler(0, 1, 3.14, .01, "f7.1");

    // evaluate for pi/2
    explicitEuler(0, 1, 1.57, .1, "f7.1");
    // evaluate for pi
    explicitEuler(0, 1, 3.14, .1, "f7.1");
    
    Approximation of the Soultion of f7.1 at 1.57: 0.0158041
    Approximation of the Soultion of f7.1 at 3.14: -0.999974
    Approximation of the Soultion of f7.1 at 1.57: 0.121386
    Approximation of the Soultion of f7.1 at 3.14: -0.99539
    
```
As we increase the step size we lose accuracy. It is interesting to note that the accuracy for the pi/2 value is worse.


