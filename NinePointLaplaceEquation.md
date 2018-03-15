# Math 4610 Fundamentals of Computational Mathematics Software Manual Entry

**Routine Name:**  ninePointStencilSolver

**Author:** Colby Wight

**Language:** C++

**Description/Purpose:**  Homework 3, Problem 6: Write a set routines that provides an approximate solution of the Laplace equation
∆ u = sin(x y)
on the unit square in two dimensions. Use homogeneous Dirichlet boundary conditions for this problem. Use the
9-point stencil as discussed in class. Use the following general algorithm to set up and solve the linear system:
1. compute the mesh,
2. initialize the matrix and right hand sides,
3. solve the linear system using an appropriate LU factorization

**Input:** There are multiple functions involved in solving this routine but they are all called by the function "fivePointStencilSolver" which then calls the other neccseary funtions to compute the mesh and sove the matrix equation. The inputs for this funtion are int n, double a, and double b, n is going to be the the number of divisions on the grid and a and b are the boundary points.  

**Output:** The code, after goin through all the funcitons inside, will print the soulution vector.

**Usage/Example:** Here are all of the needed functions and an example of the routine run on the unit square with 5 partitions: 



```C++
     struct MeshPoints{
    double x;
    double y;
};

int main() {
    ninePointStencilSolver(5, 0, 1);
    return 0;
}

Vect initb( MatrixOfPoints A){
    Vect b;
    for (int i = 1; i < A.size() -1; i++){
        for (int j = 1; j < A.size() - 1; j++){
            b.push_back(sin(A[i][j].x * A[i][j].y));
        }
    }
    return b;
}

// gives the points of the square grid with given number of divisions and endpoints
MatrixOfPoints createMeshGrid(int n, double a, double b){
    MatrixOfPoints A(n, vector <MeshPoints> (n)); // or is it n+1??
    double h = (b - a) /n;
    for (int i = 1; i < n; i++){
        for (int j = 1; j < n; j++){
            A[i][j].x = (a + j*h);
            A[i][j].y = (a + j*h);
        }
    }
    return A;
}

// itnitialize the matrix for the nine point schem


```

Output from the lines above:

```C++
     9.6097...
```

**Implementation/Code:** The code is as follows:
```C++
void ninePointStencilSolver(int n, double a, double b){
    // create mesh points
    auto Mesh = createMeshGrid(n, a, b);
    // Initialize the matrix
    Matrix A = ninePointMatrixInitializer(n);
    // Initialize b vector
    Vect vb = initb(Mesh);
    // compute the solution of the system with previous code
    Vect x = luFactor(A, vb);
    printVect(x);
}```
**Last Modified:** March/2018
