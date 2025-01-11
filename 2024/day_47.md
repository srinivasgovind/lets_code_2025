
# 📅 Day 47: 2024-09-26

## 🚀 Problems Solved

---

### 🧩 Problem 1: 
Eight integers A, B, C, D, E, F, G, and H represent two rectangles in a 2D plane.

For the First rectangle,
Bottom left corner is (A, B)
Top right corner is (C, D)
For the Second rectangle,
Bottom left corner is (E, F)
Top right corner is (G, H).
Find and return whether the two rectangles overlap or not.

- **Approach 1: Bruteforce**
  - *Draw all possibilites and check(couldn't able to understand to video help)*
- **⏳ Time Complexity:** `O(1)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int solve(int A, int B, int C, int D, int E, int F, int G, int H) {

  if( (C <= E) || (D <= F) || (B >= H) || (A >= G)){
    return 0;
  }
  return 1;
}
```
---

### 🧩 Problem 2:
Given three 2-digit integers, A, B, and C, find out the minimum number obtained by concatenating them in any order.

Return the minimum result obtained.
- **Approach 1: Bruteforce**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(n^logn)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 2
public int solve(int A, int B, int C) {

  int a[] = {A, B, C};

  Arrays.sort(a);

  return a[0]*10000 + a[1] * 100 + a[2];

}
```

- **Approach 2: Optimized**
  - *Check all possibilities instead of sort*
- **⏳ Time Complexity:** `O(1)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 2
public int solve(int A, int B, int C) {

  if(A <= B && B <= C){
    return A * 10000 + B * 100 + C;
  }
  else if ( A <=C && C <= B){
    return A * 10000 + C * 100 + B;
  }
  else if (B <= A && A <= C){
    return B * 10000 + A * 100 + C;
  }
  else if ( B <= C && C <= A){
    return B * 10000 + C * 100 + A;
  }
  else if (C <= A && A <= B){
    return C * 10000 + A * 100 + B;
  }
  else {
    return C * 10000 + B *100 + A;
  }

}
```

---

### 🧩 Problem 3: 
There are certain problems which are asked in the interview to also check how you take care of overflows in your problem.
This is one of those problems.
Please take extra care to make sure that you are type-casting your ints to long properly and at all places. Try to verify if your solution works if number of elements is as large as 105

Food for thought :

Even though it might not be required in this problem, in some cases, you might be required to order the operations cleverly so that the numbers do not overflow.
For example, if you need to calculate n! / k! where n! is factorial(n), one approach is to calculate factorial(n), factorial(k) and then divide them.
Another approach is to only multiple numbers from k + 1 ... n to calculate the result.
Obviously approach 1 is more susceptible to overflows.
You are given a read only array of n integers from 1 to n.

Each integer appears exactly once except A which appears twice and B which is missing.

Return A and B.

Note: Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

Note that in your output A should precede B.
- **Approach 1: Bruteforce**
  - *Tricky Math Problem*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 3
public int[] repeatedNumber(final int[] A) {

  long array_sum = 0;
  int n = A.length;

  long formula_sum = (long) n * (n + 1) / 2;
  long formula_squares = (long) n *(n+1) * (2*n + 1)/6;

  long square_sum = 0;

  for(int i = 0; i < n; i++){
    array_sum += A[i];
    square_sum += (long) A[i] * A[i];
  }

  long a_b = (long) array_sum - formula_sum;
  long  a_plus_b = (long) (square_sum - formula_squares)/a_b;

  long a = (a_b + a_plus_b )/2;
  long b = a - a_b;

  int result[] ={(int) a, (int) b};

  return result;

}
```
---

