
# 📅 Day 37: 2024-09-16

## 🚀 Problems Solved

---

### 🧩 Problem 1: 
Given a 2D integer array A, return the transpose of A.

The transpose of a matrix is the matrix flipped over its main diagonal, switching the matrix's row and column indices.
- **Approach 1: Bruteforce**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int[][] solve(int[][] A) {
  int n = A.length;
  int m = A[0].length;
  int[][] result = new int[m][n];
  for(int i = 0; i < n; i++){
    for(int j = 0; j < m; j++){
      result[j][i] = A[i][j];
    }
  }
  return result;
}
```
---

### 🧩 Problem 2: Spiral Order Matrix II
Given an integer A, generate a square matrix filled with elements from 1 to A2 in spiral order and return the generated square matrix.
- **Approach 1: Bruteforce**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(A^2)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 2
public int[][] generateMatrix(int A) {
  int result[][] = new int[A][A];
  int row = 0;
  int col = 0;
  int value = 1;
  while(A > 1){

    // left -> right
    for(int i = 1; i < A; i++){
      result[row][col] = value;
      value++;
      col++;
    }

    // top -> bottom

    for(int i = 1; i < A; i++){
      result[row][col] = value;
      value++;
      row++;
    }

    // right -> left
    for(int i = 1; i < A; i++){
      result[row][col] = value;
      value++;
      col--;
    }

    // bottom -> top
    for(int i = 1; i < A; i++){
      result[row][col] = value;
      value++;
      row--;
    }
    row++;
    col++;
    A = A - 2;
  }

  if(A == 1){
    result[row][col] = value;
  }

  return result;
}
```
---

### 🧩 Problem 3: Rotate Matrix
You are given a n x n 2D matrix A representing an image.

Rotate the image by 90 degrees (clockwise).

You need to do this in place.

Note: If you end up using an additional array, you will only receive partial score.

- **Approach 1: Bruteforce**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 3
public void solve(int[][] A) {

  // Rotate Matrix = Transpose + Reverse


  // Transpose

  for(int i = 0; i < A.length; i++){
    for(int j = i+1; j < A[0].length; j++){

      int temp = A[i][j];
      A[i][j] = A[j][i];
      A[j][i] = temp;
    }
  }

  // Reverse

  for(int i = 0; i < A.length; i++){
    int start = 0; int end = A[0].length-1;

    while(start < end ){
      int temp = A[i][start];
      A[i][start] = A[i][end];
      A[i][end] = temp;
      start++;
      end--;
    }
  }

}
```

---

