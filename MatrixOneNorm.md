
# Software Manual Entry

**Routine Name:**  matrixOneNorm

**Author:** Colby Wight

**Language:** C++

**Description/Purpose:**  This routine will compute the Matrix One norm of a given matrix. The one norm is the same thing as computing the the max column sum and this is what was done for a simple implementation. 

**Input:** The required inputs for this routine are a Matirx in the form of a vector of vectors of the type double, and two integer inputs to specify the dimensions of the matrix.  

**Output:** This routine will return in the form of a double the matrix one norm of the matrix.

**Usage/Example:**

This routine was tested on a simple 3 by 3 matrix. The result is the maximum sum abousolute value of the columsn being {2, 1, 5} transpose.  

```C++
    Matrix matrixB = { {1, 2, 2},
                       {1, 1, 1},
                       {2, 2, 5}};
                       
    cout << matrixOneNorm(matrixB, 3, 3) << endl;
```

Output from the lines above:

```C++
   8
```

**Implementation/Code:** The code is as follows:
```C++
double matrixOneNorm(Matrix matrix, int row, int col){
    // The variable that stores the max column sum
    double maxSum = 0;
    //loop through the columns and rows taking the sum of each 
    for(int j = 0; j < col; j++){
        double sum = 0;
        for (int i = 0; i < row; i++){
            sum+= abs(matrix[i][j]);
        }
        if (sum > maxSum){
            maxSum = sum;
        }
    }
    return maxSum;
}
```
**Last Modified:** Febuary/2018
