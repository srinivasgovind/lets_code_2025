
# 📅 Day 2: 2025-01-11

## What I Learned
- **Topic:**
- **Details:**
- **Streak Break Reason: No**

## 🚀 Problems Solved

---

### 🧩 Problem 1: 
You are given an array of N integers, A1, A2, .... AN.

Return the maximum value of f(i, j) for all 1 ≤ i, j ≤ N. f(i, j) is defined as |A[i] - A[j]| + |i - j|, where |x| denotes absolute value of x.
- **Approach 1: Bruteforce**
  - *Iterate all subarrays*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int maxArr(int[] A) {

  int max_value = 0;

  for(int i = 0; i < A.length; i++){

    for(int j = i; j < A.length;j++){
      max_value =Math.max(max_value, Math.abs(A[i] - A[j]) + Math.abs(i  - j));
    }
  }

  return max_value;
}
```

- **Approach 2: Optimized**
  - *solve the eqn ans simplify the terms, to understand the solution, its math. |a-b| is (a-b) or (b-a)*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int maxArr(int[] A) {

  int max_value = 0;

  int max_ai_plus_i = Integer.MIN_VALUE;
  int min_ai_plus_i = Integer.MAX_VALUE;
  int max_ai_minus_i = Integer.MIN_VALUE;
  int min_ai_minus_i = Integer.MAX_VALUE;
  for(int i = 0; i < A.length; i++){
    max_ai_plus_i = Math.max(max_ai_plus_i , A[i] + i);
    min_ai_plus_i = Math.min(min_ai_plus_i , A[i] + i);

    max_ai_minus_i = Math.max(max_ai_minus_i, A[i] - i);
    min_ai_minus_i = Math.min(min_ai_minus_i, A[i] - i);

  }

  return Math.max(max_ai_plus_i - min_ai_plus_i, max_ai_minus_i - min_ai_minus_i);
}
```

---

### 🧩 Problem 2: 
Given a non-negative number represented as an array of digits, add 1 to the number ( increment the number represented by the digits ).






The digits are stored such that the most significant digit is at the head of the list.

NOTE: Certain things are intentionally left unclear in this question which you should practice asking the interviewer. For example: for this problem, the following are some good questions to ask :

Q: Can the input have 0's before the most significant digit. Or, in other words, is 0 1 2 3 a valid input?
A: For the purpose of this question, YES
Q: Can the output have 0's before the most significant digit? Or, in other words, is 0 1 2 4 a valid output?
A: For the purpose of this question, NO. Even if the input has zeroes before the most significant digit.
- **Approach 1: Bruteforce**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 2
public int[] plusOne(int[] A) {

  int start =0;
  //remove leading spaces
  while(start < A.length && A[start] == 0){
    start++;
  }
  //create new input array
  int[] modifiedInput = Arrays.copyOfRange(A, start, A.length);
  int carry = 1;
  int n = modifiedInput.length;

  int[] result  = new int[n];

  for(int i = n- 1; i >= 0; i--){
    result[i] = (carry + modifiedInput[i]) % 10;
    carry = (carry + modifiedInput[i]) / 10;

  }
  
  // if any carry left 
  if(carry == 1){
    int res[] = new int[n+1];
    res[0] = 1;
    System.arraycopy(result,0, res,1, result.length);
    return res;
  }

  return result;


}
```

---

### 🧩 Problem 3: 
You are given an array A of integers of size N.

Your task is to find the equilibrium index of the given array

The equilibrium index of an array is an index such that the sum of elements at lower indexes is equal to the sum of elements at higher indexes.

If there are no elements that are at lower indexes or at higher indexes, then the corresponding sum of elements is considered as 0.

Note:

Array indexing starts from 0.
If there is no equilibrium index then return -1.
If there are more than one equilibrium indexes then return the minimum index.

- **Approach 1: Bruteforce**
  - *Observation, left prefix calculate and right prefix , you can notice both have index which has same value, that is the point left part of the array and right part of the array both are same , that is called equilibruim index*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 3
public int solve(int[] A) {

  int n = A.length;
  int[] left_prefix = new int[A.length];
  int[] right_prefix = new int[A.length];

  left_prefix[0] = A[0];
  for(int i = 1; i < A.length; i++){
    left_prefix[i] = left_prefix[i-1] + A[i];
  }

  right_prefix[n-1] = A[n-1];

  for(int j = n -2; j >= 0; j--){
    right_prefix[j] = right_prefix[j+1] + A[j];
  }

  for(int i = 0; i < A.length; i++){
    if(left_prefix[i] == right_prefix[i]){
      return i;
    }
  }
  return -1;
}
```

- **Approach 2: Optimized**
  - *Eliminated Prefix Array, Just went with Suffix Array*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 3
public int solve(int[] A) {

  int n = A.length;
  int[] right_prefix = new int[A.length];


  right_prefix[n-1] = A[n-1];

  for(int j = n -2; j >= 0; j--){
    right_prefix[j] = right_prefix[j+1] + A[j];
  }
  int left_sum = 0;
  for(int i = 0; i < A.length; i++){
    left_sum += A[i];
    if(left_sum == right_prefix[i]){
      return i;
    }
  }
  return -1;
}

```

- **Approach 3: Optimized**
  - *Without extra space, bit confusing dry run with example to understand the flow*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 3
public class Solution {
  public int solve(int[] A) {

    int n = A.length;
    int total_sum = 0;

    for(int i = 0; i < n; i++){
      total_sum += A[i];
    }
    int prefix_sum = 0;
    for(int i = 0; i < A.length; i++){
      total_sum -= A[i];
      if(total_sum == prefix_sum){
        return i;
      }
      prefix_sum += A[i];
    }
    return -1;
  }

}

```
---

