
# 📅 Day 1: 2025-01-10

## What I Learned
- **Topic: ADV DSA **
- **Details: HW Problems**
- **Streak Break Reason: No**

## 🚀 Problems Solved

---

### 🧩 Problem 1: Max Sum Contiguous Subarray
- **Approach 1: Bruteforce**
  - *Iterate all subarrays by fixing start point and end point*
- **⏳ Time Complexity:** `O(n^3)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int maxSubArray(final int[] A) {
  int max_sum = Integer.MIN_VALUE;


  for(int startpt = 0; startpt < A.length; startpt++){

    for(int endpt = 0; endpt < A.length; endpt++){

      int sum = 0;
      for(int i = startpt; i <= endpt; i++){
        sum += A[i];
      }
      max_sum = Math.max(max_sum, sum);
    }
  }

  return max_sum;
}
```

- **Approach 2: Optimized**
  - *Carrry Forward Technique, Iterate all subarrays with just two loops(only works for sum*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int maxSubArray(final int[] A) {
  int max_sum = Integer.MIN_VALUE;


  for(int startpt = 0; startpt < A.length; startpt++){
    int sum = 0;
    for(int endpt = startpt; endpt < A.length; endpt++){
      sum += A[endpt];
      max_sum = Math.max(max_sum, sum);
    }
  }

  return max_sum;
}
```

- **Approach 3: Optimized**
  - *Kaden's Algorithm, check the oberseravitons in the class notes of Jan 10th*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
//Kadene's Algorithm
public int maxSubArray(final int[] A) {
  int max_sum = Integer.MIN_VALUE;

  int sum = 0;
  for(int i = 0; i < A.length; i++){
    sum += A[i];

    max_sum = Math.max(max_sum, sum);

    if(sum < 0){
      sum = 0;
    }
  }

  return max_sum;
}
```
---

### 🧩 Problem 2: 
There are A beggars sitting in a row outside a temple. Each beggar initially has an empty pot. When the devotees come to the temple, they donate some amount of coins to these beggars. Each devotee gives a fixed amount of coin(according to their faith and ability) to some K beggars sitting next to each other.

Given the amount P donated by each devotee to the beggars ranging from L to R index, where 1 <= L <= R <= A, find out the final amount of money in each beggar's pot at the end of the day, provided they don't fill their pots by any other means.
For ith devotee B[i][0] = L, B[i][1] = R, B[i][2] = P, given by the 2D array B

- **Approach 1: Bruteforce**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(A*B)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 2
public int[] solve(int A, int[][] B) {

  int[] beggars = new int[A];

  for(int i = 0; i < B.length; i++){

    for(int start_ptr = B[i][0]; start_ptr <= B[i][1]; start_ptr++){
      beggars[start_ptr-1] += B[i][2];
    }
  }
  return beggars;
}
```

- **Approach 2: Optimized**
  - *Arrays Difference Technique, here if we add denoation start point and if we add minus denotation to end+1 point, then if we do dontaion then it becomes balanced because of negative denoation*
- **⏳ Time Complexity:** `O(B+A)`
- **💾 Space Complexity:** `O(A)`

```java
// Code implementation for Problem 2
public int[] solve(int A, int[][] B) {

  int[] beggars = new int[A+1];

  for(int i = 0; i < B.length; i++){

    beggars[B[i][0]-1] += B[i][2];
    beggars[B[i][1]] += -1 * B[i][2];
  }

  for(int i = 1;  i < beggars.length; i++){
    beggars[i] += beggars[i-1];
  }
  return Arrays.stream(beggars).limit(A).toArray();
}
```

---

### 🧩 Problem 3: 
You are given a binary string A(i.e., with characters 0 and 1) consisting of characters A1, A2, ..., AN. In a single operation, you can choose two indices, L and R, such that 1 ≤ L ≤ R ≤ N and flip the characters AL, AL+1, ..., AR. By flipping, we mean changing character 0 to 1 and vice-versa.





Your aim is to perform ATMOST one operation such that in the final string number of 1s is maximized.

If you don't want to perform the operation, return an empty array. Else, return an array consisting of two elements denoting L and R. If there are multiple solutions, return the lexicographically smallest pair of L and R.

NOTE: Pair (a, b) is lexicographically smaller than pair (c, d) if a < c or, if a == c and b < d.
- **Approach 1: Bruteforce**
  - *Here we're iterating through all subarrays and finding max ones ans storing their indexes in result*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 3
public int[] flip(String A) {

  int count = 0;
  int[] result = new int[2];
  boolean all_ones = true;
  for(int i = 0; i < A.length(); i++){
    if(A.charAt(i) != '1'){
      all_ones = false;
    }
  }
  if(all_ones){
    return new int[0];
  }
  for(int i = 0; i < A.length(); i++){

    int flip = 0;

    for(int j = i; j <A.length(); j++){

      int current = (A.charAt(j) == '0') ? 1 : 0;
      flip = current == 1? ++flip : --flip;
      if(flip > count){
        result[0] = i+1;
        result[1] = j+1;
        count = flip;
      }
    }
  }
  return result;
}
```

- **Approach 2: Optimized**
  - *Apply Kanden's Algorithm*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 3
public int[] flip(String A) {

  int input[] = new int[A.length()];
  for(int i=0; i < A.length(); i++){
    input[i] = A.charAt(i) == '1' ? -1 : 1;

  }
  int max_ones = 0;
  int ones = 0;
  int left_ptr = 0;
  int right_ptr = 0;
  int temp_left = 0;
  for(int i = 0; i < A.length(); i++){
    ones += input[i];
    if(ones > max_ones){
      max_ones = ones;
      right_ptr = i;
      left_ptr = temp_left;
    }
    if(ones < 0){
      ones = 0;
      temp_left = i+1;
    }

  }

  if(max_ones == 0){
    return new int[0];
  }
  int[] result = {left_ptr+1, right_ptr+1};
  return result;
}
```

---

