
# 📅 Day 8: 2025-01-17

## What I Learned
- **Topic:*Arrays 2*
- **Details:*ADV DSA*
- **Streak Break Reason: No**

## 🚀 Problems Solved

---

### 🧩 Problem 1: 
Implement the next permutation, which rearranges numbers into the numerically next greater permutation of numbers for a given array A of size N.



If such arrangement is not possible, it must be rearranged as the lowest possible order, i.e., sorted in ascending order.

NOTE:



The replacement must be in-place, do not allocate extra memory.
DO NOT USE LIBRARY FUNCTION FOR NEXT PERMUTATION. Use of Library functions will disqualify your submission retroactively and will give you penalty points.
- **Approach 1: Bruteforce**
  - *This algorithm can be understood by forming all permutations*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public ArrayList<Integer> nextPermutation(ArrayList<Integer> A) {
  int n = A.size();
  if(n == 1){
    return A;
  }

  // Find first decreasing element
  int i = n - 2;
  while(i >= 0 && A.get(i+1) <= A.get(i)){
    i--;
  }
  //smallest element greater than A[i]
  if(i >= 0){
    int  j = n -1;
    while(A.get(j) <= A.get(i)){
      j--;
    }
    //swap(i,j)
    int temp = A.get(i);
    A.set(i, A.get(j));
    A.set(j, temp);
  }
  //reverse everything after position i
  int start = i+1;
  int end = n - 1;
  while(start < end){
    int temp = A.get(start);
    A.set(start, A.get(end));
    A.set(end, temp);
    start++;
    end--;
  }

  return A;

}
```
---

### 🧩 Problem 2: 

Imagine a histogram where the bars' heights are given by the array A. Each bar is of uniform width, which is 1 unit. When it rains, water will accumulate in the valleys between the bars.

Your task is to calculate the total amount of water that can be trapped in these valleys.

Example:

The Array A = [5, 4, 1, 4, 3, 2, 7] is visualized as below. The total amount of rain water trapped in A is 11.
- **Approach 1: Bruteforce**
  - *At every index left max boundary and right max boundary decides how much water is trapped, for every index we need to know their left max and right max boundaries to calculate water trapeed at that index*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 2
public int trap(final List<Integer> A) {
  int n = A.size();
  int[] suffix_max = new int[n];
  int ans = 0;
  suffix_max[n-1] = A.get(n-1);
  for(int i = n-2; i>=0; i--){
    suffix_max[i] = Math.max(A.get(i),suffix_max[i+1]);
  }

  int left_max = A.get(0);
  for(int i = 1; i < n; i++){
    ans += Math.max(0, Math.min(left_max,suffix_max[i])-A.get(i));
    left_max = Math.max(left_max, A.get(i));
  }
  return ans;
}
```

- **Approach 2: Optimized**
  - *At Index find max left index and max right index*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 2
public int trap(final List<Integer> A) {
  int n = A.size();
  int left_max = A.get(0);
  int right_max = A.get(n-1);
  int ans = 0;
  int i = 1;
  int j = n-2;
  while(i <= j){
    if(left_max <= right_max){
      ans += Math.max(0, left_max - A.get(i));
      left_max = Math.max(left_max, A.get(i));
      i++;
    }
    else{
      ans += Math.max(0, right_max - A.get(j));
      right_max = Math.max(A.get(j), right_max);
      j--;
    }




  }
  return ans;
}
```

---

### 🧩 Problem 3: Write a function that takes an integer and returns the number of 1 bits present in its binary representation.
- **Approach 1: Bruteforce**
  - *check last bit is set or not and Right Shift*
- **⏳ Time Complexity:** `O(log2(A))`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 3
public int numSetBits(int A) {
  int setBits = 0;
  while(A > 0){
    setBits += (A & 1) == 1 ? 1 : 0;
    A = A >> 1;
  }
  return setBits;
}
```

- **Approach 2: Optimized**
  - *Syntax Optimization*
- **⏳ Time Complexity:** `O(log2(A))`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 3
public int numSetBits(int A) {
  int setBits = 0;
  while(A > 0){
    setBits += (A & 1);
    A >>=1;
  }
  return setBits;
}
```

---

