
# 📅 Day 14: 2025-01-23

## What I Learned
- **Topic: Modular Arithmetic**
- **Details: ADV DSA**
- **Streak Break Reason: No**

## 🚀 Problems Solved

---

### 🧩 Problem 1: 
You are given an integer A which denotes the number of people standing in the queue.



A selection process follows a rule where people standing on even positions are selected. Of the selected people, a queue is formed, and again out of these, only people on even position are selected.

This continues until we are left with one person. Find and return the position of that person in the original queue.
- **Approach 1: Bruteforce**
  - *Take a example and solve for both even and odd number, you can notice max pow of 2 <= A will be ans*
- **⏳ Time Complexity:** `O(1)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int solve(int A) {

  int ans = 1;
  //Find ans which will be max pow of 2 <= A.
  while(ans * 2 <= A){
    ans = ans * 2;
  }
  return ans;
}
```

- **Approach 2: Optimized**
  - *direct way to get power component by doing the logA/log2*
- **⏳ Time Complexity:** `O(1)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int solve(int A) {

  return (int) (Math.pow(2, (int)(Math.log(A)/Math.log(2))));
}
```

---

### 🧩 Problem 2: 
Given an array of integers A, calculate the sum of A [ i ] % A [ j ] for all possible i, j pairs. Return sum % (109 + 7) as an output.
- **Approach 1: Bruteforce**
  - *All Pairs*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 2
public int solve(int[] A) {
  //This created bcz constraints says A[i] between 1 to 1000, so maintaing freq array for repeated elementes
  long sum = 0;
  int n = A.length;
  for(int i = 0; i < n; i++){
    for(int j = 0; j < n; j++){
      int value = (A[i] % A[j]);
      sum = ((sum % MOD) + (value % MOD)) % MOD;
    }
  }
  return (int) sum;
}
```

- **Approach 2: Optimized**
  - *Remove calculations for duplicate elements, by calculating only for unique elements through freq array*
- **⏳ Time Complexity:** `O(k*k)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 2
public class Solution {
  private static int MOD = 1_000_000_007;
  public int solve(int[] A) {
    //This created bcz constraints says A[i] between 1 to 1000, so maintaing freq array for repeated elementes
    int[] freq = new int[1001];
    for(int ele : A){
      freq[ele]++;
    }
    long sum = 0;
    int n = A.length;
    for(int i = 1; i <= 1000; i++){
      for(int j = 1; j <= 1000; j++){
        int value = (freq[i] * freq[j] * (i % j));
        sum = ((sum % MOD) + (value % MOD)) % MOD;
      }
    }
    return (int) sum;
  }
}
// 1%1 1%2 1%3
//2%1 2%2 2%3
//3%1 3%2 3%3
//1%1 1%2 1%3 (repeated)
//2%1 2%2 2%3
//freq[0, 2, 2, 1]
```

---

### 🧩 Problem 3: 
Given an integer A, return the number of trailing zeroes in A! i.e., factorial of A.






Note: Your solution should run in logarithmic time complexity.
- **Approach 1: Bruteforce**
  - *Straightforward
- **⏳ Time Complexity:** `O(n+ logn)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 3
[Write your Java code here]
//Wite Fact fn , which iterates n times , the result of fact , do right shifts and check zeros count.
//This code fails for small numberrs bcz ex fact(11) = 39916800, overflow  can't be controlled.
```

- **Approach 2: Optimized**
  - *There is lot of things need to understand behind this logic, please refer notes while doing revision*
- **⏳ Time Complexity:** `O(log5(n))`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 3
public int trailingZeroes(int A) {
  // This intution to this problem is quite tricky.. revise notes to get full understnding why we do below Solution

  int no_of_zeros = 0;
  int power = 5;
  while( A/power > 0){
    no_of_zeros += A /power;
    power *= 5;
  }
  return no_of_zeros;
}
```

---

