
# 📅 Day 13: 2025-01-19

## What I Learned
- **Topic: Bit Manpulation 1**
- **Details: ADV DSA**
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

### 🧩 Problem 3: 
Given an array of positive integers A, two integers appear only once, and all the other integers appear twice.
Find the two integers that appear only once.

Note: Return the two numbers in ascending order.

- **Approach 2: Optimized**
  - *Easy to grasp the concept, xor of same element is zero, so if we do xor of all elements we left with xor of unique elements, we need to sepeate them out somehow, find a bit pos which seperates them out, that mean xor result where bit pos is set that mean both elements are differ by that bit. so div the array into buckets based on set and unset for that pos, and do xor of those buckets we get two unique elements seperated out*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 3
public int[] solve(int[] A) {
  //xor of entire array
  int xor = 0;
  for(int i = 0; i < A.length; i++){
    xor ^= A[i];
  }

  //Find pos where bit is set, that tells both element will be different by one this bit.

  int pos = 0;

  while(xor > 0){
    if((xor & 1) == 1){
      break;
    }
    pos++;
    xor >>= 1;
  }

  //Divide the entire array whether pos bit set or unset groups, and xor of the group respectively. we get two unique elements.
  int set = 0;
  int unset = 0;
  for(int i = 0; i < A.length; i++){
    if((A[i] & (1 << pos)) != 0){
      //bit is set in A[i]
      set ^= A[i];
    }
    else{
      //bit is unset in A[i]
      unset ^= A[i];
    }
  }
  return new int [] { unset < set ? unset: set, unset > set ? unset : set};
}
```

---

