
# 📅 Day 36: 2024-09-15

## 🚀 Problems Solved

---

### 🧩 Problem 1: 
  You are given a 2D integer matrix A, return a 1D integer array containing column-wise sums of original matrix.
- **Approach 1: Bruteforce**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int[] solve(int[][] A) {

  int[] result = new int[A[0].length];

  for(int j = 0; j < A[0].length; j++){
    int sum = 0;
    for(int i = 0; i < A.length; i++){
      sum += A[i][j];
    }
    result[j] = sum;
  }
  return result;
}
```
---

### 🧩 Problem 2: 
Matrix Multiplication
You are given two integer matrices A(having M X N size) and B(having N X P). You have to multiply matrix A with B and return the resultant matrix. (i.e. return the matrix AB).

- **Approach 1: Bruteforce**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(m*n*P)`
- **💾 Space Complexity:** `O(m*p)`

```java
// Code implementation for Problem 2
public int[][] solve(int[][] A, int[][] B) {

  int m = A.length;
  int n = A[0].length;
  int p = B[0].length;
  int[][] result = new int[m][p];

  for(int i = 0; i < m; i++){
    for(int j = 0; j < p; j++){

      for(int k = 0; k < n; k++){
        result[i][j] = result[i][j] + A[i][k]*B[k][j];
      }
    }
  }
  return result;

}
```
---

### 🧩 Problem 3: Matrix Subraction
You are given two integer matrices A and B having same size(Both having same number of rows (N) and columns (M). You have to subtract matrix B from A and return the resultant matrix. (i.e. return the matrix A - B).

If A and B are two matrices of the same order (same dimensions). Then A - B is a matrix of the same order as A and B and its elements are obtained by doing an element wise subtraction of A from B.
- **Approach 1: Bruteforce**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(m*n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 3
public int[][] solve(int[][] A, int[][] B) {
  int[][] result = new int[A.length][A[0].length];

  for(int i = 0; i < A.length; i++){
    for(int j = 0; j < A[0].length; j++){
      result[i][j] = A[i][j] - B[i][j];
    }
  }
  return result;
}
```
---

