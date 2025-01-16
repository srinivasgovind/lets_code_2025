
# 📅 Day 4: 2025-01-13

## What I Learned
- **Topic: ADV DSA**
- **Details: Arrays 2**
- **Streak Break Reason: No**

## 🚀 Problems Solved

---

### 🧩 Problem 1: 
Given a matrix of integers A of size N x M and multiple queries Q, for each query, find and return the submatrix sum.




Inputs to queries are top left (b, c) and bottom right (d, e) indexes of submatrix whose sum is to find out.

NOTE:

Rows are numbered from top to bottom, and columns are numbered from left to right.
The sum may be large, so return the answer mod 109 + 7.
Also, select the data type carefully, if you want to store the addition of some elements.
Indexing given in B, C, D, and E arrays is 1-based.
Top Left 0-based index = (B[i] - 1, C[i] - 1)
Bottom Right 0-based index = (D[i] - 1, E[i] - 1)
- **Approach 1: Bruteforce**
  - *Construct Prefix of Matrix and ans queries using pf matrix, calculate submartix formula on paper*
- **⏳ Time Complexity:** `O(n^m)`
- **💾 Space Complexity:** `O(n^m)`

```java
// Code implementation for Problem 1
public static int MOD = 1000_000_007;
public int[] solve(int[][] A, int[] B, int[] C, int[] D, int[] E) {


  //BUILD A PREFIX MATRIX
  int n = A.length;
  int m = A[0].length;
  int[][] pf = new int [n][m];

  //row-wise PREFIX
  for(int i = 0; i < n; i++){
    for(int j = 0; j < m; j++){
      if(j == 0){
        pf[i][j] = A[i][j];
        continue;
      }
      pf[i][j] = pf[i][j-1] + A[i][j];
      pf[i][j] = ((pf[i][j] % MOD) + MOD) % MOD;
    }
  }

  //column-wise PREFIX
  for(int j = 0; j < m; j++){
    for(int i = 1; i < n; i++){
      pf[i][j] = pf[i-1][j] + pf[i][j];
      pf[i][j] = ((pf[i][j] % MOD) + MOD) % MOD;
    }
  }

  //ans
  int[] result = new int[B.length];

  //Queries
  for(int q = 0; q < B.length; q++){
    int topleft_i = B[q] - 1;
    int topleft_j = C[q] - 1;
    int bottomright_i = D[q] - 1;
    int bottomright_j= E[q] - 1;

    long ans = ((pf[bottomright_i][bottomright_j] % MOD) + MOD) % MOD;
    if(topleft_j > 0){
      ans = ((ans - pf[bottomright_i][topleft_j-1] % MOD) + MOD) % MOD;
    }
    if(topleft_i > 0){
      ans = ((ans - pf[topleft_i-1][bottomright_j] % MOD) + MOD) % MOD;
    }
    if(topleft_i > 0 && topleft_j > 0){
      ans = ((ans + pf[topleft_i-1][topleft_j-1] % MOD) + MOD) % MOD;
    }
    result[q] = (int) ans;

  }
  return result;
}
```

- **Approach 2: Optimized**
  - *Removed mulitple Mod operation , and prefix array calculation in single iteration*
- **⏳ Time Complexity:** `O(n^m)`
- **💾 Space Complexity:** `O(n^m)`

```java
// Code implementation for Problem 1
public static int MOD = 1000_000_007;
public int[] solve(int[][] A, int[] B, int[] C, int[] D, int[] E) {


  //BUILD A PREFIX MATRIX
  int n = A.length;
  int m = A[0].length;
  int[][] pf = new int [n][m];

  //row-wise PREFIX
  for(int i = 0; i < n; i++){
    for(int j = 0; j < m; j++){
      pf[i][j] = A[i][j];
      if(j > 0){
        pf[i][j] += pf[i][j-1];
      }
      if(i > 0){
        pf[i][j] += pf[i-1][j];
      }
      if(i > 0 && j > 0){
        pf[i][j] -= pf[i-1][j-1];
      }
      pf[i][j] = (pf[i][j]) % MOD;
    }
  }


  //ans
  int[] result = new int[B.length];

  //Queries
  for(int q = 0; q < B.length; q++){
    int topleft_i = B[q] - 1;
    int topleft_j = C[q] - 1;
    int bottomright_i = D[q] - 1;
    int bottomright_j= E[q] - 1;

    long ans = pf[bottomright_i][bottomright_j];
    if(topleft_j > 0){
      ans = ans - pf[bottomright_i][topleft_j-1];
    }
    if(topleft_i > 0){
      ans = ans - pf[topleft_i-1][bottomright_j];
    }
    if(topleft_i > 0 && topleft_j > 0){
      ans = ans + pf[topleft_i-1][topleft_j-1];
    }
    result[q] = (int) ((ans % MOD) + MOD) % MOD;

  }
  return result;
}
```

---

### 🧩 Problem 2: 
Given a 2D integer matrix A of size N x N, find a B x B submatrix where B<= N and B>= 1, such that the sum of all the elements in the submatrix is maximum.
- **Approach 1: Bruteforce**
  - *Create Prefix Matrix and Iterate all submatrices of given size B*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(n^2)`

```java
// Code implementation for Problem 2
public int solve(int[][] A, int B) {

  int n = A.length;

  int[][] pf = new int[n][n];

  //prefix matrix
  for(int i = 0; i < n; i++){
    for(int j = 0; j < n; j++){
      pf[i][j] = A[i][j];

      if(i > 0){
        pf[i][j] += pf[i-1][j];
      }
      if(j > 0){
        pf[i][j] += pf[i][j-1];
      }
      if(i > 0 && j > 0){
        pf[i][j] -= pf[i-1][j-1];
      }
    }
  }
  //ans
  int max_ans = Integer.MIN_VALUE;

  //Iterate all submatrices of size B
  for(int i = 0; i <= n-B; i++){
    for(int j = 0; j <= n - B; j++){

      //A(i,j)

      //B(p,q)
      int p  = i + B - 1;
      int q  = j + B - 1;
      int value = pf[p][q];
      if(i > 0){
        value -= pf[i-1][q];
      }

      if(j > 0){
        value -= pf[p][j-1];
      }
      if( i > 0 && j > 0){
        value += pf[i-1][j-1];
      }

      max_ans = Math.max(max_ans, value);

    }
  }
  return max_ans;
}
```
---

### 🧩 Problem 3: 
You are given a n x n 2D matrix A representing an image.

Rotate the image by 90 degrees (clockwise).

You need to do this in place.

Note: If you end up using an additional array, you will only receive partial score.
[
[1, 2, 3],
[4, 5, 6],
[7, 8, 9]
]

o/p
[
[7, 4, 1],
[8, 5, 2],
[9, 6, 3]
]

- **Approach 1: Bruteforce**
  - *Transpose A and compare with the result, you will know how to solve this*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 3
public void solve(int[][] A) {

  for(int i = 0; i < A.length; i++){
    for(int j = i; j < A[0].length; j++){

      if(i != j){
        int temp = A[i][j];
        A[i][j] = A[j][i];
        A[j][i] = temp;
      }
    }
  }
  int last_col = A[0].length - 1;
  for(int j = 0; j < A[0].length/2; j++){
    for(int i = 0; i < A.length; i++){
      int temp = A[i][j];
      A[i][j] = A[i][last_col];
      A[i][last_col] = temp;

    }
    last_col--;
  }


}
```

- **Approach 2: Optimized**
  - *Did cleanup and removed extra variable*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 3
public void solve(int[][] A) {
  int n = A.length;
  for(int i = 0; i < n; i++){
    for(int j = i; j < n; j++){

      if(i != j){
        int temp = A[i][j];
        A[i][j] = A[j][i];
        A[j][i] = temp;
      }
    }
  }

  for(int j = 0; j < n/2; j++){
    for(int i = 0; i < n; i++){
      int temp = A[i][j];
      A[i][j] = A[i][n-j-1];
      A[i][n-j-1] = temp;

    }
  }


}
```

---

