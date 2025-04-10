
# 📅 Day 6: 2025-01-15

## What I Learned
- **Topic: Arrays 2 & 3**
- **Details: ADV DSA**
- **Streak Break Reason: No**

## 🚀 Problems Solved

---

### 🧩 Problem 1: 
Given an array of integers A of size N that is a permutation of [0, 1, 2, ..., (N-1)].

It is allowed to swap any two elements (not necessarily consecutive).



Find the minimum number of swaps required to sort the array in ascending order.
- **Approach 1: Bruteforce**
  - *Iterate the array, find no of cycles can be formed*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 1
public int solve(int[] A) {

  //Find no of cycles exists, for every cycle swaps = cyclesize - 1 & add all swaps

  boolean[] visited = new boolean[A.length];
  int minswaps = 0;

  for(int i = 0; i < A.length; i++){
    if(A[i] == i || visited[i]){
      continue;
    }

    int current = i;
    int cycle_size = 0;
    while(!visited[current]){
      visited[current] = true;
      current = A[current];
      cycle_size++;
    }
    if(cycle_size > 1){
      minswaps += cycle_size -1;
    }
  }
  return minswaps;
}

```

- **Approach 2: Optimized**
  - *It's very tricky, need to solve again in free time.*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int solve(int[] A) {
    
    //Here instead of cycles finding we swap directly in the cycle 
  int swaps = 0;

  for(int i = 0; i < A.length; i++){
    if(A[i] == i){
      continue;
    }

    while(A[i] != i){
      int temp = A[i];
      A[i] = A[temp];
      A[temp] = temp;
      swaps++;
    }
  }
  return swaps;
}
```

---

### 🧩 Problem 2: 
Given an integer A, find and return the total number of digit 1 appearing in all non-negative integers less than or equal to A.
- **Approach 1: Bruteforce**
  - *Basic Intution, use recursion, below solution gives stack overflow. It works only for small inputs(not recommended.*
- **⏳ Time Complexity:** `O(no of digits * A)`
- **💾 Space Complexity:** `O(A)`

```java
// Code implementation for Problem 2
public int solve(int A) {
  // this fn returns no of ones in A
  //lets write recursive
  if(A <= 0){
    return 0;
  }

  if(A <= 9){
    return 1;
  }
  int digits = 0;
  int num = A;
  while (num > 0){
    int last = num % 10;
    if(last == 1){
      digits++;
    }
    num = num/10;
  }
  return digits + solve(A - 1);

}
```
- **Approach 2: Bruteforce 2**
  - *Same logic but eliminates stack overfloow, but iterative works fine , but TLE (*
- **⏳ Time Complexity:** `O(n * 1og10(A))`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 2
public int solve(int A) {
  // this fn returns no of ones in A
  //lets write recursive

  int digits = 0;
  for(int i= 1; i <= A; i++){
    int num = i;
    while (num > 0){
      int last = num % 10;
      if(last == 1){
        digits++;
      }
      num = num/10;
    }


  }
  return digits;
}
```

- **Approach 2: Optimized**
  - *Placeholder, couldn't able to solve this, its leetcode hard couldn't able to grasp the intution*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 2
[Write your Java code here]
```

---

### 🧩 Problem 3: 
Given an unsorted integer array, A of size N. Find the first missing positive integer.





Note: Your algorithm should run in O(n) time and use constant space.
- **Approach 1: Bruteforce**
  - *Here we're using O(n) space to store input ele in hashset, with O(1) time checking whether 1 to N+1 elements are in hs*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 3
public int firstMissingPositive(int[] A) {
  int n = A.length;
  HashSet<Integer> hs =new HashSet<>();

  for(int ele : A){
    hs.add(ele);
  }

  for(int i = 1; i <= n+1; i++){
    if(!hs.contains(i)){
      return i;
    }
  }
  return -1;
}
```

- **Approach 2: Optimized**
  - *Any element should be in their i+1 position, if they're not swap to their right position then iterate once to get the first missing element, TC is complex to understand, as we have inner loop as well... but the thing every swap through while loop make element in their right position. so loops runs only n-1 times to place every element in their right position.*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 3
public int firstMissingPositive(int[] A) {
  int n = A.length;
  //swap the array in place to its correct position any ith position should have i+1 as a value in it.

  for(int i = 0; i < n; i++){

    while(A[i] > 0 && A[i] <= n && A[i] != A[A[i] -1]){
      int temp = A[i];
      A[i] = A[temp - 1];
      A[temp - 1] = temp;
    }
  }

  for(int i = 0; i < n; i++){
    if(A[i] != i+1){
      return i+1;
    }
  }
  return n + 1;
}
```

---

