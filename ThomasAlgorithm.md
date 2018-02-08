# Solution to Differential Equations Software Manual Entry


**Routine Name:**          thomasAlg()

**Author:** Colby Wight

**Language:** C++

**Description/Purpose:** The Thomas Algorthim is, in essence, Gaussian ellimination applied to a tridiagonal matrix. We will use this routine to help us in solving differential equations. 

``

**Input:** xBar and x: The inputs are four vectors. The upper and lower diagonal componets of the vector are denoted by s and l. The diagonal component is denoted by d. Our b vector is denoted by b. 

**Output:** This routine will return the solution x vector. 

**Usage/Example:** This routine was run on a simple tri digonal matrix input as vecotrs and the results follow:

```C++
    Vect d1 = {2, 2, 2, 2};
    Vect s1 = {1, 1, 1};
    Vect l1 = {1, 1, 1};
    Vect b1 = {1, 1, 1, 1};
    Vect u1 = thomasAlg(d1, s1, l1, b1);
    printVect(u1);
```

Output from the lines above:
```C++
    {1.16667, -0.166667, 0.666667, 0.5}
```

**Implementation/Code:** The following is the code for thomasAlg():

```C++
   Vect thomasAlg(Vect d, Vect s, Vect l, Vect b ){

    int n = d.size(); // or is it n - 1
    // apply gausian elimination to necessary components
    for (int i = 1; i < n-1; i++){
        d[i] = d[i] - s[i-1]*l[i-1]/d[i-1];
        b[i] = b[i] - b[i-1]*l[i-1]/d[i-1];
    }
    Vect u(n);
    u[n-1] = b[n-1] / d[n-1];
    //perform backward substitution
    for (int i = n-2; i >= 0; i-- ){
        u[i] = b[i] - u[i+1] * s[i+1];
    }
    return u;
    }
```

**Last Modified:** Febuary/2018
