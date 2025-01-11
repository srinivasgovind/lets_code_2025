
# 📅 Day 34: 2024-09-13

## 🚀 Problems Solved

---

### 🧩 Problem 1: Given an array A of size N, find the subarray of size B with the least average.
- **Approach 1: Bruteforce**
  - *Sliding window*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int solve(int[] A, int B) {

  int min_index = 0;
  int min_sum = Integer.MAX_VALUE;
  int sum = 0;
  int i = 0;
  int j = B;

  for(int k = 0; k<B; k++){
    sum += A[k];
  }

  min_sum = sum;


  while(j < A.length ){
    sum = sum + A[j] - A[i];
    if(sum < min_sum){
      min_sum = sum;
      min_index = j - B + 1;
    }
    i++;
    j++;
  }
  return min_index;
}
```

- **Approach 2: Optimized**
  - *Another approach but same complexity*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int solve(int[] A, int B) {

  int min_index = 0;
  int min_sum = Integer.MAX_VALUE;
  int sum = 0;

  for(int k = 0; k<B; k++){
    sum += A[k];
  }

  min_sum = sum;

  for(int i = B; i < A.length ;i++){
    sum = sum + A[i] - A[i - B];

    if(sum < min_sum){
      min_sum = sum;
      min_index = i - B + 1;
    }
  }
  return min_index;
}
```

---

### 🧩 Problem 2: 
Given an array A of N non-negative numbers and a non-negative number B,
you need to find the number of subarrays in A with a sum less than B.
We may assume that there is no overflow.
- **Approach 1: Bruteforce**
  - *Carry Forward Prefix Sum*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int solve(int[] A, int B) {

  int count = 0;

  for(int i = 0; i < A.length; i++){
    int sum = 0;
    for(int j = i; j < A.length; j++){
      sum += A[j];
      if(sum < B){
        count++;

      }
      else{
        break;
      }
    }
  }
  return count;
}
```

- **Approach 2: Prefix Sum**
  - *Another way of thinking but same complexity*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int solve(int[] A, int B) {

  int count = 0;
  int[] prefix = new int[A.length];
  prefix[0] = A[0];
  for(int i = 1; i < A.length; i++){
    prefix[i] = prefix[i-1] + A[i];
  }
  for(int i = 0; i < A.length; i++){
    for(int j = i; j < A.length; j++){
      int val = prefix[j];
      if(i > 0){
        val -= prefix[i-1];
      }
      if(val < B){
        count++;

      }
    }
  }
  return count;
}
```

---

### 🧩 Problem 3: 
Given an array of integers A, a subarray of an array is said to be good if it fulfills any one of the criteria:
1. Length of the subarray is be even, and the sum of all the elements of the subarray must be less than B.
2. Length of the subarray is be odd, and the sum of all the elements of the subarray must be greater than B.
   Your task is to find the count of good subarrays in A.

- **Approach 1: Bruteforce**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int solve(int[] A, int B) {

  int count = 0;

  for(int i = 0; i < A.length; i++){
    int sum = 0;

    for(int j = i; j < A.length; j++){
      sum += A[j];
      if((j-i+1) % 2 == 0 && sum < B){
        count++;
      }
      else if((j-i+1) % 2 != 0 && sum > B){
        count++;
      }
    }

  }
  return count;
}
```

- **Approach 2: Other approach**
  - *Using Prefix Sum*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int solve(int[] A, int B) {

  int count = 0;
  int sum = 0;
  int[] prefix = new int[A.length];
  prefix[0] = A[0];

  for(int i = 1; i < A.length; i++){
    prefix[i] = prefix[i-1] + A[i];
  }
  for(int i = 0; i < A.length; i++){
    for(int j = i; j < A.length; j++){
      if(i == 0){
        sum = prefix[j];
      }
      else{
        sum = prefix[j] - prefix[i-1];
      }


      if((j-i+1) % 2 == 0 && sum < B){
        count++;
      }
      else if((j-i+1) % 2 != 0 && sum > B){
        count++;
      }
    }

  }
  return count;
}
```

---

