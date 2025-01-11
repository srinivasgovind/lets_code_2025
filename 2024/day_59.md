
# 📅 Day 59: 2024-10-08

## 🚀 Problems Solved

---

### 🧩 Problem 1: 
Given an array A of integers and another non negative integer B .

Find if there exists 2 indices i and j such that A[i] - A[j] = B and i != j.
- **Approach 1: Bruteforce**
  - *only thing i din't understood is why A[i]+B need to checked*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 1
public int diffPossible(final int[] A, int B) {

  Set<Integer>  hs =new HashSet<>();


  for(int i = 0; i < A.length; i++){

    if(hs.contains(A[i] - B) || hs.contains(A[i] + B)){
      return 1;
    }
    hs.add(A[i]);
  }
  return 0;
}
```

---

### 🧩 Problem 2: 
You are given an array of N integers, A1, A2 ,..., AN and an integer B. Return the of count of distinct numbers in all windows of size B.

Formally, return an array of size N-B+1 where i'th element in this array contains number of distinct elements in sequence Ai, Ai+1 ,..., Ai+B-1.

NOTE: if B > N, return an empty array.

- **Approach 1: Bruteforce**
  - *HashMap with sliding window concept, this is not bruteforce. Bruteforce can be like iterating through all windows and check unqiue elements or many other ways we can solve bruteforce this problems*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 2
public int[] dNums(int[] A, int B) {

  if(B > A.length){
    return new int[0];
  }
  
  int[] result = new int[A.length - B + 1];

  HashMap<Integer, Integer> hm = new HashMap<>();

  for(int i = 0; i < B; i++){
    hm.put(A[i], hm.getOrDefault(A[i],0)+1);
  }

  result[0] = hm.size();

  for(int i = B; i < A.length; i++){

    hm.put(A[i-B], hm.get(A[i-B])-1);

    if(hm.get(A[i-B]) <= 0){
      hm.remove(A[i-B]);
    }

    hm.put(A[i], hm.getOrDefault(A[i], 0)+1);
    result[i-B+1] = hm.size();
  }



  return result;
}
```
---

### 🧩 Problem 3: 
Given an array of integers, find two numbers such that they add up to a specific target number.

The function twoSum should return indices of the two numbers such that they add up to the target, where index1 < index2. Please note that your returned answers (both index1 and index2 ) are not zero-based. Put both these numbers in order in an array and return the array from your function ( Looking at the function signature will make things clearer ). Note that, if no pair exists, return empty list.

If multiple solutions exist, output the one where index2 is minimum. If there are multiple solutions with the minimum index2, choose the one with minimum index1 out of them.
- **Approach 1: Optmized**
  - *Using HashMap*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 3
public int[] twoSum(final int[] A, int B) {

  int[] result = new int[2];

  Map<Integer, Integer> hm = new HashMap<>();

  for(int i = 0; i < A.length; i++){

    int x = A[i];
    int y = B - A[i];

    if(hm.containsKey(y)){
      result[0] = hm.get(y)+1;
      result[1] = i+1;
      return result;
    }
    if(!hm.containsKey(x)){
      hm.put(x, i);
    }

  }

  return new int[0];

}

```
---

