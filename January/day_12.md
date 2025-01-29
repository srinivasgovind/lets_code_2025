
# 📅 Day 12: 2025-01-21

## What I Learned
- **Topic: Maths Modular Arithmetic**
- **Details: ADV DSA 1**
- **Streak Break Reason: No**

## 🚀 Problems Solved

---

### 🧩 Problem 1: 
Given two integers A and B, find the greatest possible positive integer M, such that A % M = B % M.

- **Approach 2: Optimized**
  - *Explantion lies in comments of code*
- **⏳ Time Complexity:** `O(1)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int solve(int A, int B) {
  // a%m = b%m
  // a%m - b%m = 0
  // (a%m - b%m ) % m = 0 % m
  // (a-b) % m = 0
  // HERE M VALUES ARE FACTORS OF (A-B), M VALUES LIES IN [1, A-B]
  // QUESTION IS TO FIND MAXIMUM M VALUE, WHICH IS (A-B)


  return Math.abs(A - B);
}
```

---

### 🧩 Problem 2: 
Given two integers A and B. Find the value of A-1 mod B where B is a prime number and gcd(A, B) = 1.

A-1 mod B is also known as modular multiplicative inverse of A under modulo B.
- **Approach 1: Bruteforce**
  - *A inverese mod p => we have cond (A inv p-1  mod p = 1, add A inverse on both sides, A pow p-2  mod P = A inverse  mod p*
- **⏳ Time Complexity:** `O(B)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 2
public int solve(int A, int B) {
//A ^ -1 % P = A^ (P-2) % P
  int temp_A = 1;
  for(int i = 1; i <=B-2; i++){
    temp_A = (temp_A * A) % B;
  }

  return (temp_A % B);
}
```

- **Approach 2: Optimized**
  - *Optimized the power fn from n to logn, revisit the power fn code is bit tricky*
- **⏳ Time Complexity:** `O(logB)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 2
public int solve(int A, int B) {


  return ((int) power(A, B-2, B) % B);
}
private long power(long A, long n, long B){
  long result = 1;

  while(n > 0){
    if((n & 1) == 1){
      result = (result * A) % B;
    }

    A = (A * A) % B;
    n >>= 1;
  }

  return result;
}
```

---

### 🧩 Problem 3: 
Given an array of integers A and an integer B, find and return the number of pairs in A whose sum is divisible by B.

Since the answer may be large, return the answer modulo (109 + 7).

Note: Ensure to handle integer overflow when performing the calculations.
- **Approach 1: Bruteforce**
  - *this is still optimized code, need to understand the logic, it's bit complex.. *
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 3
private static int MOD = 1_000_000_007;
public int solve(int[] A, int B) {

  HashMap<Integer, Integer> hm = new HashMap<>();

  for(int ele : A){
    int val = hm.containsKey(ele % B) ? hm.get(ele % B) : 0;
    hm.put(ele % B, ++val);
  }
  long count = hm.containsKey(0) ? hm.get(0) : 0;
  count = (count * (count - 1))/2;
  int i = 1;
  int j = B - 1;
  while(i < j){
    int p = hm.containsKey(i) ? hm.get(i) : 0;
    int q = hm.containsKey(j) ? hm.get(j) : 0;
    if((i+j) % B == 0){
      count = (count + (long)(p * q)) % MOD;
    }
    i++;
    j--;
  }
  if(i == j){
    int p = hm.containsKey(i) ? hm.get(i) : 0;
    int q = hm.containsKey(j) ? hm.get(j) : 0;
    long ncr= ((long)p * (p - 1))/2;
    count = (count + ncr) % MOD;
  }

  return (int) (count + MOD) % MOD;
```

- **Approach 2: Optimized**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(n+B)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 3
private static int MOD = 1_000_000_007;
public int solve(int[] A, int B) {

  long count[] = new long[B];


  for(int ele : A){
    count[ele % B]++;
  }


  long result = (count[0] * (count[0] - 1))/2;
  int i = 1;
  int j = B - 1;
  while(i <= j){
    if(i == j){
      long ncr= (count[i] * (count[i] - 1))/2;
      result = (result + ncr) % MOD;
      break;
    }

    result = (result + (count[i] * count[j])) % MOD;

    i++;
    j--;
  }


  return (int) (result) % MOD;
}
```

---

