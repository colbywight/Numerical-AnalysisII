# Solution to Differential Equations Software Manual Entry


**Routine Name:**      explicitEuler

**Author:** Colby Wight

**Language:** C++

**Description/Purpose:** This is a routine for sovling a ordinary differential equation with initial values. This is a first order Runge-Kutta method. For this method we do ne reuqire a linear sovler. It is very simple to code. h is the width of our interval. 

**Input:** We have two inputs for the initial condition x0 and y0, then we also take in the parameter x where we want to evaluate it at. Then we used two inputs tol and maxIter to break us out of the loop.

**Output:** This routine returns a double precision value of the apporximation to the solution at the given value.

**Usage/Example:** This routine was run on the differential equation dydx = x + y with the following inputs and we get a approximation to the solution

```C++
   explicitEuler(0, -1, .4, .1, .0001, 500);

```

Output from the lines above:
```C++
   Approximation of the Solution at the given value: -1.4
```

**Implementation/Code:** The following is the code:

```C++
     void explicitEuler(double x0, double y0, double x, double h, double tol, double maxIter ){

    double y =0;
    int cnt = 0;
    while(fabs(x - x0) > tol && cnt < maxIter){
        y = y0 + (h * dydx1(x0, y0));
                y0 = y;
        x0 = x0 + h;
    }
    cout << "Approximation of the Solution at the given value: " << y << endl;
}
```

**Last Modified:** March/2018
