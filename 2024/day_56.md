
# 📅 Day 56: 2024-10-05

## 🚀 Problems Solved

---

### 🧩 Problem 1: 
Given two integer arrays, A and B of size N and M, respectively. Your task is to find all the common elements in both the array.


NOTE:


Each element in the result should appear as many times as it appears in both arrays.
The result can be in any order.
- **Approach 1: Bruteforce(This code is better than below optimized code)**
  - *Bruteforce way of thinking*
- **⏳ Time Complexity:** `O(n+m)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 1
public int[] solve(int[] A, int[] B) {

  HashMap<Integer, Integer> hm = new HashMap<>();
  List<Integer> res = new ArrayList<>();

  // add A array into hash map
  for(int i = 0; i <A.length; i++){

//    if(hm.containsKey(A[i])){
//      int val = hm.get(A[i]);
//      hm.put(A[i], ++val);
//    }else{
//      hm.put(A[i], 1);
//    }
    hm.put(A[i], hm.getOrDefault(A[i], 0)+1);
  }

  //iterate B array and compare and store result accordingly
  for(int i = 0; i <B.length; i++){
    if(hm.containsKey(B[i]) && hm.get(B[i]) >= 1){
      res.add(B[i]);
      int val = hm.get(B[i]) - 1;
      hm.put(B[i], val);
    }
  }
  
  //list to array conversion
  return res.stream().mapToInt(i -> i).toArray();

}
```

- **Approach 2: Optimized**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(n+m)`
- **💾 Space Complexity:** `O(n+m)`

```java
import java.util.HashMap;// Code implementation for Problem 1
public int[] solve(int[] A, int[] B) {

  HashMap<Integer, Integer> hma = new HashMap<>();
  HashMap<Integer, Integer> hmb = new HashMap<>();

  List<Integer> res = new ArrayList<>();

  for(int x: A){
      hma.put(x, hma.getOrDefault(x, 0)+1);
  }
  
  for(int x: B){
      hmb.put(x, hmb.getOrDefault(x, 0)+1);
  }
  
  for(int k : hma.keySet()){
      if(hmb.containsKey(k)){
          
          for(int i = 0; i < Math.min(a.get(k), b.get(k)); i++){
              res.add(k);
          }
      }
  }
  return res.stream().mapToInt(i -> i).toArray();

}
```

---

### 🧩 Problem 2: 
Given an integer array A of size N, find the first repeating element in it.






We need to find the element that occurs more than once and whose index of the first occurrence is the smallest.

If there is no repeating element, return -1.
- **Approach 1: Bruteforce**
  - *Bruteforce thinking*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 2
public int solve(int[] A) {
  HashMap<Integer, Integer> hm = new HashMap<>();

  for(int ele : A){
    hm.put(ele, hm.getOrDefault(ele, 0) + 1);

  }
  for(int ele : A){
    if(hm.get(ele) > 1){
      return ele;
    }
  }
  return -1;
}
```

- **Approach 2: Optimized**
  - *This is interesting way to think, same soln but iterating in reverse will be solved in one iteration*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 2
public int solve(int[] A) {
  HashMap<Integer, Integer> hm = new HashMap<>();
  int ans = -1;
  for(int i = A.length - 1; i >= 0; i--){

    if(hm.containsKey(A[i])){
      ans = A[i];
    }
    else{
      hm.put(A[i], 1);
    }

  }

  return ans;
}
```

---

### 🧩 Problem 3: 
Given an array A of N integers.

Find the largest continuous sequence in a array which sums to zero.
- **Approach 1: Bruteforce**
  - *Subarray Bruteforce*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 3
public int[] lszero(int[] A) {

  int max_i = 0;
  int max_j = -1;

  int max_len = 0;


  for(int i = 0; i < A.length; i++){
    int sum = 0;
    for(int j = i; j < A.length; j++){
      sum += A[j];

      if(sum == 0 && max_len < j - i + 1){
        max_len = j - i + 1;
        max_i = i;
        max_j = j;
      }


    }
  }
  if(max_len == 0){
    return new int[0];
  }
  int[] result = new int[max_j-max_i+1];
  int ptr = 0;
  for(int k = max_i; k <=max_j; k++){
    result[ptr] = A[k];
    ptr++;
  }

  return result;
}
```

- **Approach 2: Optimized**
  - *create prefix sum and observe it, if ele in prefix sum repeats, then element between their sum is zero*
  - length = (i−(prevIndex+1))+1 = i−prevIndex
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 3
public int[] lszero(int[] A) {

  int max_i = 0;
  int max_j = -1;

  int max_len = 0;

  HashMap<Integer, Integer> prevSum = new HashMap<>();

  prevSum.put(0, -1);

  int sum = 0;

  for(int i = 0; i < A.length; i++){
    sum += A[i];

    if(prevSum.containsKey(sum)){
      int prev_index = prevSum.get(sum);
      int len = i - prev_index;
      if( len > max_len){
        max_len = len;
        max_i = prev_index + 1;
        max_j = i;
      }
    }
    else{
      prevSum.put(sum, i);
    }

  }
  if(max_len == 0){
    return new int[0];
  }
  int[] result = new int[max_j-max_i+1];
  for(int k = max_i; k <=max_j; k++){
    result[k - max_i] = A[k];
  }

  return result;
}
```

---

