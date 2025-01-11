
# 📅 Day 31: 2024-09-10

## 🚀 Problems Solved

---

### 🧩 Problem 1: A wire connects N light bulbs.

Each bulb has a switch associated with it; however, due to faulty wiring, a switch also changes the state of all the bulbs to the right of the current bulb.

Given an initial state of all bulbs, find the minimum number of switches you have to press to turn on all the bulbs.

You can press the same switch multiple times.

Note: 0 represents the bulb is off and 1 represents the bulb is on.
- **Approach:Bruteforce**
  - *Bruteforce way of thinking*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(1)`

```java
public int bulbs(int[] A) {

  int count = 0;

  for(int i = 0 ; i < A.length; i++){
    if(A[i] == 0){
      count++;
      for(int j = i+1; j < A.length; j++){
        A[j] = 1 - A[j];
      }
    }
  }
  return count;
}
```

- **Approach: Optimized**
  - *Tricky by observation of input toggling figured out event count have orginal array , while odd count toggles the array*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(1)`

```java
public int bulbs(int[] A) {

  int count = 0;

  for(int i = 0 ; i < A.length; i++){
    int state = A[i];

    if(count % 2 == 0){
      state = A[i];
    }else{
      state = 1 - A[i];
    }

    if(state == 0){
      count++;
    }
  }
  return count;
}
```

---

### 🧩 Problem 2: 
You have given a string A having Uppercase English letters.

You have to find how many times subsequence "AG" is there in the given string.

NOTE: Return the answer modulo 109 + 7 as the answer can be very large.


- **Approach1: Bruteforc**
  - *Bruteforce thinking*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(1)`

```java
public int solve(String A) {

  long count = 0;

  for(int i = 0; i < A.length(); i++){

    if(A.charAt(i) == 'A'){
        for(int j = i+1; j < A.length(); j++){
            if(A.charAt(j) == 'G'){
                count++;
            }
        }
    }
  }
  return count;
}
```

- **Approach2: Optimized**
  - * Observation of iterating and maintaing g count from backwards, another approach to solve this maitain suffix array of G's think about it*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(1)`

```java
public int solve(String A) {

  long count = 0;
  long ans = 0;
  int mod = 1000 * 1000 * 1000 + 7;

  for(int i = A.length() - 1; i >= 0 ; i--){

    if(A.charAt(i) == 'G'){
      count++;
    }
    else if(A.charAt(i) == 'A'){
      ans = ans + count;
      ans = ans % mod;
    }
  }
  return (int) ans;
}
```

---

### 🧩 Problem 3: 
Given an array A, find the size of the smallest subarray such that it contains at least one occurrence of the maximum value of the array

and at least one occurrence of the minimum value of the array.
- **Approach 1: Bruteforce**
  - *Bruteforce thinking*
- **⏳ Time Complexity:** `[e.g., O(n), O(log n)]`
- **💾 Space Complexity:** `[e.g., O(1), O(n)]`

```java
// Code implementation for Problem 3
public int solve(int[] A){
  int min = A[0];
  int max = A[0];
  for(int i = 0; i < A.length; i++){
    min = Math.min(min, A[i]);
    max = Math.max(max, A[i]);
  }
  if(min == max){
    return 1;
  }
  
  for(int i = 0; i < A.length; i++){
      if(A[i] == min){
          
          for(int j = i+1; j < A.length; j++){
              if(A[j] == min) break;
            if(A[j] == max){
                  ans = Math.min(ans, j-i+1);
                  break;
              }
          }
      }
   else if(A[i] == max){

      for(int j = i+1; j < A.length; j++){
        if(A[j] == max) break;
        if(A[j] == min){
          ans = Math.min(ans, j-i+1);
          break;
        }
      }
    }
  }
  return ans;
}
```

- **Approach 2: Optimized**
  - *Carry Backward*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 3
public int solve(int[] A) {

  int min = A[0];
  int max = A[0];
  for(int i = 0; i < A.length; i++){
    min = Math.min(min, A[i]);
    max = Math.max(max, A[i]);
  }
  if(min == max){
    return 1;
  }
  int min_i = -1;
  int max_i = -1;
  int ans = Integer.MAX_VALUE;
  for(int i = A.length -1; i >= 0; i--){
    if(A[i] == min){
      min_i = i;
      if(max_i != -1){
        ans = Math.min(ans, max_i - min_i + 1);
      }
    }
    else if(A[i] == max){
      max_i = i;
      if(min_i != -1){
        ans = Math.min(ans, min_i - max_i + 1);
      }
    }
  }
  return ans;
}
```

---

