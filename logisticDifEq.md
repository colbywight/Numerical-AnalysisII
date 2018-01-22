# Software Manual Entry

**Routine Name:**  logDEq()

**Author:** Colby Wight

**Language:** C++

**Description/Purpose:**  This code will take the initial condition, P0, a and b as input and produce the value of the solution at an arbitrary point, t. This function will be used to test other numberical methods.

**Input:** The three inputs are P0, a and b. P0 is our initial condition. a and b are some parameters of the equation. 

**Output:** This will output the solution at an arbitrary point t.  

**Usage/Example:** 

```C++
    cout << logDEq(5, 3, 2) << endl;

```

Sample Output:

```C++
      -8
```

**Implementation/Code:** The code is as follows:
```C++
    // logistic differential equation solution with paramters
    double logDEq(double p0, double a, double b ){

    return (1 - b) * p0 - a;
    }
```
**Last Modified:** January/2018
