
# 📅 Day 13: 2025-01-22

## What I Learned
- **Topic:**
- **Details:**
- **Streak Break Reason: No**

## 🚀 Problems Solved

---

### 🧩 Problem 1: 
Divide two integers without using multiplication, division and mod operator.

Return the floor of the result of the division.

Also, consider if there can be overflow cases i.e output is greater than INT_MAX, return INT_MAX.

NOTE: INT_MAX = 2^31 - 1

- **Approach 2: Optimized(need to solve again)**
  - *This is mathematical understanding how division works, subract dividend with divisor until becomes <= divisor, hom many times we do is k, k is the ans. but instead of doing it dividend = dividend - divisor multiple times, dividend = divident - divisor\*2^k, so that we can able to do it less times that is the idea. tricky to understand*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 1
public int divide(int A, int B) {
  if (A == Integer.MIN_VALUE && B == -1) {
    return Integer.MAX_VALUE;
  }
  boolean isNegative = (A > 0) ^ (B > 0);
  long dividend = Math.abs((long)A);
  long divisor = Math.abs((long)B);
  long ans = 0;
  for(int i = 31; i >= 0; i--){
    if(dividend >= (divisor << i)){
      dividend -= (divisor << i);
      ans += (1 << i);
    }
  }
  if(ans > Integer.MAX_VALUE){
    return Integer.MAX_VALUE;
  }

  if(isNegative){
    return -1 * (int)ans;
  }
  return (int)ans;
}
```

---

### 🧩 Problem 2: 
We define f(X, Y) as the number of different corresponding bits in the binary representation of X and Y.
For example, f(2, 7) = 2, since the binary representation of 2 and 7 are 010 and 111, respectively. The first and the third bit differ, so f(2, 7) = 2.

You are given an array of N positive integers, A1, A2,..., AN. Find sum of f(Ai, Aj) for all pairs (i, j) such that 1 ≤ i, j ≤ N. Return the answer modulo 109+7.



- **Approach 1: Bruteforce**
  - *Easy to understand, read the question, they asked need to count no of different bits in a & b(which is xor) and count ones in the result*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 2
public int cntBits(int[] A) {
  int count = 0;

  for(int i = 0; i < A.length; i++){
    for(int j = i; j < A.length; j++){
      int a = A[i];
      int b = A[j];
      int res = (a ^ b);
      while(res > 0){
        if((res&1) == 1){
          if(i == j){
            count += 1;
          }else{
            count += 2;
          }

        }
        res >>=1;
      }
    }
  }
  return count;
}
```

- **Approach 2: Optimized(revisit)**
  - *Bit contribution technique for overall differnt bit count, trick for intution*
- **⏳ Time Complexity:** `O(n*32)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 2
public static final int MOD = 1_000_000_007;
public int cntBits(int[] A) {
  //final count
  long count = 0;

  //iterate all the bits
  for(int i = 0; i < 31; i++){
    //no of ones at ith bit for the entire array
    int no_of_ones = 0;

    //no of zeros at ith bit for the entire array
    int no_of_zeros = 0;

    for(int j = 0; j < A.length; j++){
      if((A[j] & (1 << i)) != 0){
        no_of_ones++;
      }
    }

    no_of_zeros = A.length - no_of_ones;
    long contribution = ((long) no_of_ones * no_of_zeros * 2) % MOD;
    //contribution of ith bit to total count
    count = (count + contribution) % MOD;


  }
  return (int)count;
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

