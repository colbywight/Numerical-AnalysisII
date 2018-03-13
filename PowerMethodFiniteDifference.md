# Software Manual Entry

**Routine Name:**  inversePowerMethod

**Author:** Colby Wight

**Language:** C++

**Description/Purpose:**  As a final use of the power method, apply the inverse power method to the matrix that arises in
the finite difference method. Use the results to compute an estimate of the condition number of the matrix.
Determine how the condition number varies as the size of the matrix increases.

**Input:** The required inputs for this routine are A, v0, tol and maxIter. Where we have A as a nxn (square) matrix. v0 is the vector guess. As usuall we will use tol and maxIter to break out of a loop when either out desired tolerance level is met or the maximum allowable interations has been tried.

**Output:** This routine will return a struct which holds both the eigenvalue and the eigenvector.  These are both associated with the greateds eigen value.

**Usage/Example:**

This routine was tested using the second order FDM scheme on a 5x5 matrix, the results for this are below, including a discussion on how the size of the matirx affects the smallest eigenvalue. The code used to create the FDM matrix is also provided. 

```C++
     Matrix secondOrderMatrix(int n){
     Matrix A(n, Vect(n));
     for (int i = 0; i < n; i++){
        for ( int j = 0; j < n; j++) {
            if(i-1 == j || i+1 == j ) {A[i][j] = 1;}
            else if(i == j) { A[i][j] = -2;}
            else A[i][j] = 0;
        }
     }
     return A;
     }

     int main() {
      Matrix F5 = secondOrderMatrix(5);
      Vect v05 = makeV0(5);
      cout << "Inverse Power Method Result for Second order FDM 5x5 matirx: ";
      InversePowerMethod(F5, v05, .001, 500 );
     
     return 0;
     }

```

Output from the lines above:

```C++
     Inverse Power Method Result for Second order FDM 5x5 matirx:
     1.47323
```
Results: Above we have the resulting smallest eignenvalue as given by the power method. This same process was run on matricies of increasing size, if we compare them to the condition number using the smalles and largest eigen values we see that the condition number increases for larger matricies as well.

**Implementation/Code:** The code is as follows:
```C++
lambdaVector powerMethod(Matrix A, Vect v0, double tol, int maxIter){
    lambdaVector result;
    int n = v0.size();
    Vect y(n);
    Vect x(n);
    Vect s(n);
    double lambdaNew;
    y = matVectMult(A, n, n, v0);
    double lambdaOld = 0.0;
    double error = tol * 10;
    int cnt = 0;
    double yNorm;
    while (error > tol && cnt < maxIter) {
        lambdaNew = 0;
        yNorm = l2Norm(y);
        x = scalarVect(1/yNorm, y);
        s = matVectMult(A, n, n, x);
        for (int i = 0; i < n; i++) {
            lambdaNew += x[i] + s[i];
        }
        error = abs(lambdaOld - lambdaNew);
        cnt++;
        y = s;
        lambdaOld = lambdaNew;
    }
    result.Lambda = lambdaNew;
    result.x = x;
    return result;

}
Vect matVectMult(Matrix matA, int rowA, int colA, Vect vectB) {

    Vect resultVect(rowA);
    # pragma omp parallel for
    for (int i = 0; i < rowA; i++) {
        resultVect[i] = 0;
        for (int j = 0; j < colA; j++) {
            resultVect[i] = resultVect[i] + matA[i][j] * vectB[j];
        }
    }
    return resultVect;
}

double l2Norm(Vect vector1) {
    int sum = 0;
    for (int i = 0; i < vector1.size(); i++) {
        sum+= abs(pow(vector1[i], 2))
        }
    return sqrt(sum);
}

Vect scalarVect(double a, Vect b) {
    for (int i = 0; i < b.size(); i++){
        b[i] = a * b[i];
    }
    return b;
}
```
**Last Modified:** March/2018
