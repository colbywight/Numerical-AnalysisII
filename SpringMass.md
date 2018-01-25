# Software Manual Entry

**Routine Name:**  springMass()

**Author:** Colby Wight

**Language:** C++

**Description/Purpose:**  This code will take the initial conditions as input and produce the value of the solution at an arbitrary point, t. This function will be used to test other numberical methods.

**Input:** This function requries many input varibables. Including v0 and y0. After solving the charicteristic equation r1 and r2. And also t, the time parameter.   

**Output:** This will output the solution at an arbitrary point t.  

**Usage/Example:** 

```C++
    cout << springMass(2, 4, 1, 1, 3);

```

Sample Output:

```C++
      3.54864
```

**Implementation/Code:** The code is as follows:
```C++
    // spring mass equation with parameters
    double springMass(double v0, double y0, double t, double r1, double r2){
    return ((v0 - r2*y0)/(r1 - r2))* pow(e, r1*t) + ((r1*y0 -r2)/(r1-r2))*pow(e, r2*t);
    }
```
**Last Modified:** January/2018
