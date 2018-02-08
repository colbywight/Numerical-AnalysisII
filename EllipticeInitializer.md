# Solution to Differential Equations Software Manual Entry


**Routine Name:**         ellipticFunctInit()

**Author:** Colby Wight

**Language:** C++

**Description/Purpose:** Write a routine that will initialize the information needed for the elliptic ordinary differential equation with initial conditions. This function will return a structure of vectors that denote the elemnts of the matrix and soultion vector. 

**Input:** The inputs are f, a, b, ua, ub, and n. For f we take in a string which will specify which function we are using. a and b are our bondaries and where we evaluate the solution at. ua and ub are the evaluations of u at the points a and b. Finally, n is our mesh partition size. 

**Output:** This function will return a structure of vectors that denote the elemnts of the matrix and soultion vector. 

**Usage/Example:** Here is an example of running the routine that is outputting the needed vectors to run a linear solver on: 

```C++
    struct EllipticInitializer{
    Vect diag;
    Vect super;
    Vect lower;
    Vect b;
    };
    EllipticInitializer test;
    test = ellipticFunctInit("f1", 0, 1, 2.5, 5, 3);
    printVect(test.super);
    printVect(test.diag);
    printVect(test.lower);
    printVect(test.b);
```

Output from the lines above:
```C++
    {1, 1}
    {-2, -2, -2}
    {1, 1}
    {-2.5, 0, -4.99982}
```

**Implementation/Code:** The following is the code for absError():

```C++
    EllipticInitializer ellipticFunctInit( string f, double a, double b,
                                      double ua, double ub, int n) {
    EllipticInitializer result;
    Vect superDiagVect(n-1, 1);
    result.super = superDiagVect;
    Vect diagonalVect(n, -2);
    result.diag = diagonalVect;
    Vect lowerDiagVect(n-1, 1);
    result.lower = lowerDiagVect;

    Vect bVect(n);
    double h = (b - a) / n;
    bVect[0] = h* h*funct(f, a) - ua;

    for (int i = 1; i < n - 2; i++) {
        bVect[i] = h*h*funct(f, a + (i+1) * h);
    }
    bVect[n-1] = h*h*funct(f, b)  - ub;
    result.b = bVect;

    return result;
    }
```

**Last Modified:** January/2018
