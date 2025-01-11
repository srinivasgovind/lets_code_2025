
# 📅 Day 33: 2024-09-12

## 🚀 Problems Solved

---

### 🧩 Problem 1: Find the maximum sum of contiguous non-empty subarray within an array A of length N.
- **Approach 1: Bruteforce**
  - *CarryForware this is not actual bruteforce, actual brute force is to iterate over all subarrays*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int maxSubArray(final int[] A) {
  int result = Integer.MIN_VALUE;

  for(int i = 0; i < A.length; i++){
    int sum = 0;
    for(int j = i; j < A.length; j++){
      sum += A[j];
      result = Math.max(result, sum);

    }
  }
  return result;
}
```

- **Approach 2: Optimized**
  - *Intution is hard to get, tricky solution*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int maxSubArray(final int[] A) {
  int result = Integer.MIN_VALUE;
  int sum = 0;
  for(int i = 0; i < A.length; i++){
    sum = sum + A[i];
    sum = Math.max(sum, A[i]);
    result = Math.max(result, sum);
  }
  return result;
}
```

---

### 🧩 Problem 2: 
You are given an integer array A of length N.
You have to find the sum of all subarray sums of A.
More formally, a subarray is defined as a contiguous part of an array which we can obtain by deleting zero or more elements from either end of the array.
A subarray sum denotes the sum of all the elements of that subarray.

Note : Be careful of integer overflow issues while calculations. Use appropriate datatypes.
- **Approach 1: Bruteforce**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 2
public long subarraySum(int[] A) {

  int result = 0;
  for(int i = 0; i < A.length; i++){
    int sum = 0;
    for(int j = i; j < A.length; j++){

      sum = sum + A[j];
      result += sum;
    }


  }

  return result;
}
```

- **Approach 2: Optimized**
  - *Calculate every index contribution and add up those*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 2
public long subarraySum(int[] A) {

  long result = 0;
  for(int i = 0; i < A.length; i++){

    long itotal = (long)(A.length - i) * (i + 1);
    long ithsum = itotal * A[i];
    result += ithsum;

  }

  return result;
}
```

---

### 🧩 Problem 3: 
You are given an integer array C of size A. Now you need to find a subarray (contiguous elements) so that the sum of contiguous elements is maximum.
But the sum must not exceed B.

- **Approach 1: Bruteforce**
  - *Caryforward thinking instead of bruteforce of iterating all subarrays*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 3
public int maxSubarray(int A, int B, int[] C) {

  int maxsum = 0;

  for(int i = 0; i < A; i++){

    int sum  = 0;

    for(int j = i; j < A; j++){

      sum += C[j];
      if(sum <= B){
        maxsum = Math.max(maxsum, sum);
      }
      else{
          break;  // this statements is needed bcz input array contains postive numbers only
      }
    }
  }
  return maxsum;
}

```

---

