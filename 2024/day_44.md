
# 📅 Day 44: 2024-09-23

## 🚀 Problems Solved

---

### 🧩 Problem 1: 
Given an array of positive integers A, two integers appear only once, and all the other integers appear twice.
Find the two integers that appear only once.

Note: Return the two numbers in ascending order.

- **Approach 2: Optimized**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int[] solve(int[] A) {
  int xorele = 0;

  for(int i = 0; i < A.length; i++){
    xorele = xorele ^ A[i];
  }

  int mask = (xorele & (xorele -1)) ^ xorele;

  int eleA = 0;
  int eleB = 0;

  for(int i = 0; i < A.length; i++){

    if( (mask & A[i]) != 0){
      eleA = eleA ^ A[i];
    }
    else{
      eleB = eleB ^ A[i];
    }
  }
  int result[] = {Math.min(eleA, eleB), Math.max(eleA, eleB)};
  return result;
}
```

---

### 🧩 Problem 2: 
Given an array B of length A with elements 1 or 0. Find the number of subarrays such that the bitwise OR of all the elements present in the subarray is 1.
Note : The answer can be large. So, return type must be long.
- **Approach 1: Bruteforce**
  - *Bruteforce thinking*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 2
public long solve(int A, int[] B) {

  long result = 0;

  for(int i = 0; i < A; i++){
    int tempOR = 0;
    if(B[i] == 1){
      result += A - i;
      continue;
    }
    for(int j = i; j < A; j++){
      tempOR = tempOR | B[j];
      if(tempOR == 1){
        result++;
      }

    }
  }
  return result;
}
```

---

### 🧩 Problem 3: 
Given an integer A. Unset B bits from the right of A in binary.

For example, if A = 93 and B = 4, the binary representation of A is 1011101.
If we unset the rightmost 4 bits, we get the binary number 1010000, which is equal to the decimal value 80.
- **Approach 1: Optimized**
  - *Using Bit manpulation technique like left shift*
- **⏳ Time Complexity:** `O(B)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 3
public long solve(long A, int B) {

  long result = A;

  for(int i = 0; i < B; i++){
    if((A & (1 <<  i)) != 0){
      result  = result - (1 << i);
    }
  }
  return result;
}
```

---

