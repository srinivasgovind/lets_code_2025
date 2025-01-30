
# 📅 Day 11: 2025-01-22

## What I Learned
- **Topic: Modular Arithmetic**
- **Details: ADV DSA**
- **Streak Break Reason: No**

## 🚀 Problems Solved

---

### 🧩 Problem 1:
Given an integer A, find and return the Ath magic number.

A magic number is defined as a number that can be expressed as a power of 5 or a sum of unique powers of 5.

First few magic numbers are 5, 25, 30(5 + 25), 125, 130(125 + 5), ….
- **Approach 1: Bruteforce**
  - *Observation needed A binary and the sequence in 5 powers, you will see a pattern*
- **⏳ Time Complexity:** `O(logn)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int solve(int A) {

  int result = 0;
  int power = 5;
  while( A > 0){
    if((A & 1) == 1){
      result += power;
    }
    A >>= 1;

    power = power * 5;
  }
  return result;
}

```

- **Approach 2: Optimized**
  - *Easy understanding*
- **⏳ Time Complexity:** `O(logn)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int solve(int A) {

  int result = 0;
  int power = 1;
  while( A > 0){
    power *= 5;
    if((A & 1) == 1){
      result += power;
    }
    A >>= 1;
  }
  return result;
}

```

---

### 🧩 Problem 2: 
Given two Integers A, B. You have to calculate (A ^ (B!)) % (1e9 + 7).

"^" means power,
"%" means mod, and
"!" means factorial.

Note: Ensure to handle integer overflow when performing the calculations.

- **Approach 2: Optimized Only**
  - *Bruteforce not possible, need to revisit, this is solved using fermatts theorm, added steps in comments of code*
- **⏳ Time Complexity:** `O(B + log(MOD))`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 2
public class Solution {
  private static int MOD = 1_000_000_007;
  public int solve(int A, int B) {
    //Fermatts Therom
    // A ^ (p - 1) = 1 % p , where p is prime number
    //MOD is prime no
    // In our case p = MOD (imp)
    //A^B! % p can be written as (A^p-1 * A^p-1 ... A^x) % p
    //so, we need to find only A^x % p
    // what is x ? x = B! % (p-1)
    //so final calculation is A ^(B! % (p -1 ) % p
    //TC is O(B + log(p)) where B iteration for cal of B! , log p is A^p cal in logarthimic using fast exponenation
    long fact = 1;
    for(int i = 2; i <=B; i++){
      fact = (fact * (long)i) % (MOD-1);
    }
    return (int) power(A, fact, MOD);
  }

  public long power(long A, long fact, int MOD){
    long result = 1;
    while(fact > 0){
      if((fact & 1) == 1){
        result = (result * A) % MOD;
      }
      A = ( A * A ) % MOD;
      fact >>= 1;
    }
    return result;
  }
}

```

---

### 🧩 Problem 3: [Problem Title or Description]
- **Approach 1: Bruteforce**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 3
[Write your Java code here]
```

- **Approach 2: Optimized**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 3
[Write your Java code here]
```

---

