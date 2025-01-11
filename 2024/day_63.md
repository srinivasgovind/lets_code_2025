
# 📅 Day 63: 2024-10-12

## 🚀 Problems Solved

---

### 🧩 Problem 1: 
Given a number A, check if it is a magic number or not.

A number is said to be a magic number if the sum of its digits is calculated till a single digit recursively by adding the sum of the digits after every addition. If the single digit comes out to be 1, then the number is a magic number.
- **Approach 1: Optimized**
  - *Recursion*
- **⏳ Time Complexity:** `O(logA * logA)`
- **💾 Space Complexity:** `O(log A)`

```java
// Code implementation for Problem 1
public int solve(int A) {
  if(A <= 9){
    return A == 1 ? 1 : 0;
  }

  int digit_sum = 0;

  while(A != 0){
    digit_sum += A % 10;
    A = A/10;
  }
  return solve(digit_sum);
}
```
---

### 🧩 Problem 2: 
On the first row, we write a 0. Now in every subsequent row, we look at the previous row and replace each occurrence of 0 with 01, and each occurrence of 1 with 10.

Given row number A and index B, return the Bth indexed symbol in row A. (The values of B are 1-indexed.).

- **Approach 1: Optmized(tough)**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(A)`
- **💾 Space Complexity:** `O(A)`

```java
// Code implementation for Problem 2
public int solve(int A, int B) {
  if(A == 1){
    return 0;
  }

  int length = 1 << (A - 1);

  int mid = length/2;
  if(B <= mid){
    return solve(A-1, B);
  }
  else{
    return 1 - solve(A-1, B - mid);
  }
}
```
---

### 🧩 Problem 3: 
The gray code is a binary numeral system where two successive values differ in only one bit.

Given a non-negative integer A representing the total number of bits in the code, print the sequence of gray code.

A gray code sequence must begin with 0.

- **Approach 1: Optimized(Recursion) Tough Problem**
  - *Solve everytime using pen and paper for better understanding, tc: at each level we're doing 2^A-1 operations, A * 2^A-1, sc: at each level, 2^A array size, so A* 2^A*
- **⏳ Time Complexity:** `O(A * 2^A)`
- **💾 Space Complexity:** `O(A * 2^A)`

```java
// Code implementation for Problem 3
public int[] grayCode(int A) {

  if(A == 1){
    int[] base = new int[2];
    base[0] = 0;
    base[1] = 1;
    return base;
  }

  int[] prevGrayCode = grayCode(A-1);

  int[] currentResult = new int[1 << A];

  int append_value = 1 << (A - 1);

  int mid = (1 << A) / 2;
  //append 0 to prevGrayCode
  for(int i = 0; i < mid; i++){
    currentResult[i] = prevGrayCode[i];
  }

  for(int i = prevGrayCode.length - 1 ; i >= 0; i--){
    currentResult[mid] = append_value + prevGrayCode[i];
    mid++;
  }
  return currentResult;
}
```
---
















