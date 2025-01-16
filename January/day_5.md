
# 📅 Day 5: 2025-01-14

## What I Learned
- **Topic: Arrays 2**
- **Details: ADV DSA**
- **Streak Break Reason: No**

## 🚀 Problems Solved

---

### 🧩 Problem 1: 
You have given a string A having Uppercase English letters.

You have to find how many times subsequence "AG" is there in the given string.

NOTE: Return the answer modulo 109 + 7 as the answer can be very large.
- **Approach 1: Optimized**
  - *Solved this problem earlier*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public static int MOD = 1_000_000_007;
public int solve(String A) {

  int ans = 0;
  int g_count = 0;

  for(int i = A.length() - 1; i >= 0; i--){
    char ch = A.charAt(i);
    if(ch == 'G'){
      g_count++;
    }
    if(ch == 'A'){
      ans = (ans + g_count) % MOD;
    }
  }
  return ans;
}
```
---

### 🧩 Problem 2: 
Spiral Order Matrix II
Given an integer A, generate a square matrix filled with elements from 1 to A2 in spiral order and return the generated square matrix.
- **Approach 1: Bruteforce**
  - *Follow the code, it's basically understanding how the flow is going*
- **⏳ Time Complexity:** `O(n*n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 2
public int[][] generateMatrix(int A) {
  int orgA = A;
  if( A == 1){
    return new int[][]{{1}};
  }
  //result matrix size A * A
  int[][] result = new int[A][A];

  int counter = 1;

  //row const
  int left = 0;

  //col const
  int bottom = A - 1;

  //row const
  int right = A - 1;

  //col const
  int top = 0;
  while(A > 0 ){

    // left to right
    for(int j = left; j < right; j++){
      result[left][j] = counter;
      counter++;
    }


    //top to bottom
    for(int i = top; i < bottom; i++){
      result[i][bottom] = counter;
      counter++;
    }


    //right to left
    for(int j = right; j > left; j-- ){
      result[right][j] = counter;
      counter++;
    }


    //bottom to top
    for(int i = bottom; i > top; i--){
      result[i][top] = counter;
      counter++;
    }

    top++;
    bottom--;
    left++;
    right--;

    A = A - 2;
  }
  if( orgA % 2  == 1){
    result[orgA/2][orgA/2] = counter;
  }
  return result;
}
```
- **Approach 2: Optimized**
  - *Code is more readable, less variables and easy to understand*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 3
public int[][] generateMatrix(int A) {
  int orgA = A;
  if( A == 1){
    return new int[][]{{1}};
  }
  //result matrix size A * A
  int[][] result = new int[A][A];

  int counter = 1;
  int r = 0;
  int c = 0;

  while(A > 1){

    //left to right
    for(int i = 0; i < A - 1; i++){
      result[r][c] = counter;
      counter++;
      c++;
    }

    //top to bottom
    for(int i = 0; i < A - 1; i++){
      result[r][c] = counter;
      r++;
      counter++;
    }

    //right to left
    for(int i = 0; i < A - 1; i++){
      result[r][c] = counter;
      c--;
      counter++;
    }

    //bottom to top
    for(int i = 0; i < A - 1; i++){
      result[r][c] = counter;
      r--;
      counter++;
    }

    r++;
    c++;
    A -= 2;
  }
  if( A == 1){
    result[r][c] = counter;
  }
  return result;
}
```
---

### 🧩 Problem 3: 
Given an array of integers A and an integer B, find and return the minimum number of swaps required to bring all the numbers less than or equal to B together.

Note: It is possible to swap any two elements, not necessarily consecutive.
- **Approach 1: Bruteforce(TLE)**
  - *If we understand the qn correctly, we need element < B together (consective).. it doesn't need to be at beginning.. idea is find total no of element < B  that will be our window size we should check how many min swaps required*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 3
public int solve(int[] A, int B) {

  //count required
  int windowsize = 0;
  for(int ele : A){
    if(ele <= B){
      windowsize++;
    }
  }

  //ans
  int minswaps = Integer.MAX_VALUE;

  for(int i = 0; i <= A.length- windowsize; i+=1){
    int swaps = 0;
    for(int j = i; j < i + windowsize && j < A.length; j++){
      if(A[j] > B){
        swaps++;
      }
    }
    minswaps = Math.min(minswaps, swaps);

  }
  return minswaps;

}
```

- **Approach 2: Optimized(Recommended)**
  - *Using sliding window, instead of iterating the window each time, just check the entering element and leaving element of the window*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 3
public int solve(int[] A, int B) {

  //count required
  int windowsize = 0;
  for(int ele : A){
    if(ele <= B){
      windowsize++;
    }
  }

  //ans
  int badelement = 0;
  int ans = Integer.MAX_VALUE;

  for(int i = 0; i < windowsize; i++){
    if(A[i] > B){
      badelement++;
    }

  }
  ans = Math.min(ans, badelement);

  for(int i = 1; i <= A.length - windowsize; i++){
    if(A[i-1] > B){
      badelement--;
    }
    if(A[i + windowsize - 1] > B){
      badelement++;
    }
    ans = Math.min(ans, badelement);
  }


  return ans;
}
```

---

