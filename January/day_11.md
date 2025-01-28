
# 📅 Day 11: 2025-01-20

## What I Learned
- **Topic:**
- **Details:**
- **Streak Break Reason: No**

## 🚀 Problems Solved

---

### 🧩 Problem 1: 
Given an array of integers, every element appears thrice except for one, which occurs once.

Find that element that does not appear thrice.

NOTE: Your algorithm should have a linear runtime complexity.

Could you implement it without using extra memory?

- **Approach 2: Optimized**
  - *Understanding the array in bit wise, if we see bit wise table of the array, at any kth pos no_of_set_bits are multiples of 3 except the unqiue number.*
- **⏳ Time Complexity:** `O(n* 31)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int singleNumber(final int[] A) {

  int ans = 0;

  for(int i = 0; i <= 30; i++){
    //set bit count
    int count = 0;
    for(int j =0; j < A.length; j++){
      if((A[j] & (1 << i)) != 0){
        count++;
      }
    }
    count %= 3;
    ans += (count << i);
  }
  return ans;
}
```

---

### 🧩 Problem 2: 
Given an integer array A of N integers, find the pair of integers in the array which have minimum XOR value. Report the minimum XOR value.
- **Approach 1: Bruteforce**
  - *Bruteforce way, condn i!=j*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 2
public int findMinXor(int[] A) {

  int min = Integer.MAX_VALUE;
  for(int i = 0; i < A.length; i++){
    for(int j = i+1; j < A.length; j++){
        min = Math.min(min, A[i] ^ A[j]);
  
    }
  }
  return min;
}
```

- **Approach 2: Optimized**
  - *If we oberve taking numbers xor, to get min xor, we need same bits at msb and if we want differents bits that should comes lsb, so this way can achieve lower xor value. one more thing if two elements are near then their xor value will be lower. so sorting the array makes elements comes to near..*
- **⏳ Time Complexity:** `O(n^logn)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 2
public int findMinXor(int[] A) {

  int min = Integer.MAX_VALUE;
  Arrays.sort(A);

  for(int i = 1; i < A.length; i++){
    min = Math.min(min, A[i-1] ^ A[i]);
  }
  return min;
}
```

---

### 🧩 Problem 3: 
Given an integer A.
Two numbers, X and Y, are defined as follows:

X is the greatest number smaller than A such that the XOR sum of X and A is the same as the sum of X and A.
Y is the smallest number greater than A, such that the XOR sum of Y and A is the same as the sum of Y and A.
Find and return the XOR of X and Y.

NOTE 1: XOR of X and Y is defined as X ^ Y where '^' is the BITWISE XOR operator.

NOTE 2: Your code will be run against a maximum of 100000 Test Cases.

- **Approach 2: Optimized**
  - *Based on question, x value will be greatest no, but smaller than A, so to satisfy xor and or we need make where 1s in A should be 0 in X. to maximize x we add 1s wherever 0 in A. for y we need smallest greater than A, for that if we set msb+1 and unset every bit then we can achieve it.*
- **⏳ Time Complexity:** `O(1)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 3
public int solve(int A) {

  //Find X
  int x = 0;
  int msb_pos = 0;
  for(int i = 30; i >=0; i--){
    if((A & (1 << i)) != 0){
      msb_pos = i;
      break;
    }
  }
  for(int i = 0; i <= msb_pos; i++){
    if((A & (1 << i)) == 0){
      x |= ( 1<< i);
    }
  }

  //Find Y

  int y = 1<< (msb_pos + 1);

  return (x ^ y);
}
```

---

