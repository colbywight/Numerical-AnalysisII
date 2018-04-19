# Solution to Differential Equations Software Manual Entry


**Routine Name:**      implicitEuler

**Author:** Colby Wight

**Language:** C++

**Description/Purpose:** This is a routine for sovling a ordinary differential equation with initial values. This is a first order Runge-Kutta method. For this method we do ne reuqire a linear sovler. It is very simple to code. h is the width of our interval. This rouitne is similar to the Explicit Euler excepth that we use the current y value. We used a secant method routine inside the function. 

**Input:** We have two inputs for the initial condition x0 and y0, then we also take in the parameter x where we want to evaluate it at. Then we used two inputs tol and maxIter to break us out of the loop. For homewokr 6 we added another parmeter to run our routine for different values lambda for the fucntion. 

**Output:** This routine returns a double precision value of the apporximation to the solution at the given value.

**Usage/Example:** This routine was run on the differential equation dydx = x + y with the following inputs and we get a approximation to the solution. We then modified the code for Homework 6 test problems and tested the routine for different vlaues of lambda. here are the results: 

```C++
   int main() {
   implicitEuler(0, -1, .4, .1, "f1", "df1", .0001, 500);
    cout << " value for lambda = 1: ";
    implicitEuler(0, 1, 1, .001, .001, "f1", "df1", 1000, 1);
    cout << " value for lambda = -1: ";
    implicitEuler(0, 1, 1, .001, .001, "f1", "df1", 1000, -1);
    cout << " value for lambda = 100: ";
    implicitEuler(0, 1, 1, .001, .001, "f1", "df1", 1000, 100);

   return 0;
   }
```

Output from the lines above:
```C++
   Approximation of the Solution at the given value: -1.4
   value for lambda = 1: Approximation of the Solution at the given value: 1.4985
   value for lambda = -1: Approximation of the Solution at the given value: 0.501499
   value for lambda = 100: Approximation of the Solution at the given value: 50.8501
```

**Implementation/Code:** The following is the code:

```C++
 

void implicitEuler(double x0, double y0, double x, double deltat, string f, string df, double tol, int maxIter){
    int n=0;
    while (fabs(x - x0) > tol && n < maxIter){
        x0 = x0 + deltat;
        double y1a = newtsMeth(y0, f, df, tol, maxIter);
        y0 = y0 + deltat * func2(x0, y1a, f);
        n++;
    }
    cout << "Approximation of the Solution at the given value: " << y0 << endl;
}
```

**Last Modified:** March/2018
