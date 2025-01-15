
# 📅 Day 3: 2025-01-12

## What I Learned
- **Topic: ADV DSA**
- **Details: Array 1**
- **Streak Break Reason: No**

## 🚀 Problems Solved

---

### 🧩 Problem 1: 
Given an array A, find the size of the smallest subarray such that it contains at least one occurrence of the maximum value of the array

and at least one occurrence of the minimum value of the array.
- **Approach 1: Bruteforce**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(n^3)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int solve(int[] A) {

  int min = A[0];
  int max = A[0];
  for(int i = 0; i < A.length; i++){
    min = Math.min(min, A[i]);
    max = Math.max(max, A[i]);
  }
  int min_len = Integer.MAX_VALUE;
  for(int i = 0; i < A.length; i++){

    for(int j = i; j < A.length; j++){
      boolean minFound = false;
      boolean maxFound = false;

      for(int k = i; k <=j; k++){
        if(A[k] == min){
          minFound = true;

        }
        if(A[k] == max){
          maxFound = true;
        }
      }
      if(minFound && maxFound){
        min_len = Math.min(min_len, j-i+1);
      }
    }
  }
  return min_len;
}
```

- **Approach 2: Optimized**
  - *We just need to find min index and max index and their distance, till we get min distance.. do we really neeed to iterate all subarrays, I don't think so*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int solve(int[] A) {

  int min = A[0];
  int max = A[0];
  for(int i = 0; i < A.length; i++){
    min = Math.min(min, A[i]);
    max = Math.max(max, A[i]);
  }
  int min_len = Integer.MAX_VALUE;

  boolean minFound = false;
  boolean maxFound = false;
  int min_pos = 0;
  int max_pos = 0;
  for(int i = 0; i < A.length; i++){

    if(A[i] == min){
      minFound = true;
      min_pos = i;
    }

    if(A[i] == max){
      maxFound = true;
      max_pos = i;
    }
    if(minFound && maxFound){
      min_len = Math.min(min_len, Math.abs(max_pos - min_pos)+1);
    }
  }

  return min_len;
}
```

- **Approach 3: Optimized**
  - *Small modifications, core logic changes new approach*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int solve(int[] A) {

  int min = A[0];
  int max = A[0];
  for(int ele : A){
    min = Math.min(min, ele);
    max = Math.max(max, ele);
  }
  int min_len = Integer.MAX_VALUE;


  int min_pos = -1;
  int max_pos = -1;
  for(int i = 0; i < A.length; i++){

    if(A[i] == min ){
      min_pos = i;
      if(max_pos != -1)
        min_len = Math.min(min_len, min_pos - max_pos+1);
    }

    if(A[i] == max){
      max_pos = i;
      if(min_pos != -1)
        min_len = Math.min(min_len, max_pos - min_pos+1);
    }

  }

  return min_len;
}
```
---

### 🧩 Problem 2: 
Given 4 array of integers A, B, C and D of same size, find and return the maximum value of | A [ i ] - A [ j ] | + | B [ i ] - B [ j ] | + | C [ i ] - C [ j ] | + | D [ i ] - D [ j ] | + | i - j| where i != j and |x| denotes the absolute value of x.
- **Approach 1: Bruteforce**
  - *Iterate all pair as per expression*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 2
public int solve(int[] A, int[] B, int[] C, int[] D) {

  int max_left = Integer.MIN_VALUE;
  int min_right = Integer.MAX_VALUE;
  int max_ans = Integer.MIN_VALUE;
  for(int i = 0; i < A.length; i++){
    for(int j = 0; j < A.length; j++){
      if(i != j){
        int sum = Math.abs(A[i] - A[j]);
        sum += Math.abs(B[i] - B[j]);
        sum += Math.abs(C[i] - C[j]);
        sum += Math.abs(D[i] - D[j]);
        sum += i - j;
        max_ans = Math.max(max_ans, sum);
      }
    }
  }

  return max_ans;
}
```

- **Approach 2: Optimized**
  - *Write the eqns, by expanding abs function, if you calculate there will 32 possible expressions.. ABCDE binary represenation of signs *
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 2
public int solve(int[] A, int[] B, int[] C, int[] D) {


  int[] sign = new int[5];
  int max_ans = Integer.MIN_VALUE;

  for(int i =0; i < 32; i++){

    for(int j = 0; j < 5; j++){
      sign[j] = (i >> j) & 1;
      sign[j] = sign[j] == 0 ? -1 : 1;
    }
    int min = Integer.MAX_VALUE;
    int max = Integer.MIN_VALUE;
    for(int k = 0; k < A.length; k++){
      int value = (A[k]* sign[0])+ (B[k] + sign[1]) + (C[k] * sign[2]) + (D[k] * sign[3]) + (k) * (sign[4]);
      min = Math.min(min, value);
      max = Math.max(max, value);
    }

    max_ans = Math.max(max_ans, max-min);

  }
  return max_ans;
}
```

---

### 🧩 Problem 3: 
Given a 2D Matrix A of dimensions N*N, we need to return the sum of all possible submatrices.
- **Approach 1: Bruteforce**
  - *Created Prefix Matrix, generated all submatrices and calculated sum using prefix matrix*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 3
public int solve(int[][] A) {
  int n = A.length;
  int [][] pf = new int[n][n];

  //row-wise prefix    
  for(int i = 0; i < n; i++){
    for(int j = 0; j < n; j++){
      if(j == 0){
        pf[i][j] = A[i][j];
        continue;
      }
      pf[i][j] = pf[i][j-1] + A[i][j];
    }
  }

  //column-wise prefix
  for(int j = 0; j < n; j++){
    for(int i = 1; i < n; i++){

      pf[i][j] = pf[i-1][j] + pf[i][j];
    }
  }

  //caculate all submatrices sum
  int max_ans = 0;

  for(int i = 0; i < n; i++){
    for(int j = 0; j < n; j++){
      //A(i,j)

      for(int k = i; k < n; k++){

        for(int l = j; l < n; l++){

          //B(k, l)
          int sum = pf[k][l];
          if(j > 0){
            sum -= pf[k][j-1];
          }
          if(i > 0){
            sum -= pf[i-1][l];
          }
          if( i > 0 && j  > 0){
            sum += pf[i-1][j-1];
          }
          max_ans += sum;
        }
      }
    }
  }

  return max_ans;
}
```

- **Approach 2: Optimized**
  - *Contribution Technique*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 3
public int solve(int[][] A) {
  int n = A.length;
  int ans = 0;

  for(int i = 0; i < n; i++){
    for(int j = 0; j < n; j++){
      ans += A[i][j] * ((i+1) * (j+ 1) * (n - i) *( n - j));
    }
  }

  return ans;
}
```

---

