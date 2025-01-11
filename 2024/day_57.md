
# 📅 Day 57: 2024-10-06

## 🚀 Problems Solved

---

### 🧩 Problem 1: 
Given an array of integers A, find and return whether the given array contains a non-empty subarray with a sum equal to 0.

If the given array contains a sub-array with sum zero return 1, else return 0.
- **Approach 1: Bruteforce**
  - *bruteforce way, gets TLE*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int solve(int[] A) {

  for(int i = 0; i < A.length; i++){

    int sum = 0;

    for(int j = i; j < A.length; j++){

      sum += A[j];

      if(sum == 0){
        return 1;
      }
    }
  }
  return 0;
}
```

- **Approach 2: Optimized**
  - *Use Prefix Sum Technique same as day_56 3rd problem*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 1
public int solve(int[] A) {

  HashSet<Long> prevSum = new HashSet<>();

  long sum = 0;
  for(int i = 0; i < A.length; i++){
    sum += A[i];

    if(prevSum.contains(sum) || sum == 0){
      return 1;
    }
    else{
      prevSum.add(sum);
    }



  }
  return 0;
}
```

---

### 🧩 Problem 2: 
Shaggy has an array A consisting of N elements. We call a pair of distinct indices in that array a special if elements at those indices in the array are equal.


Shaggy wants you to find a special pair such that the distance between that pair is minimum. Distance between two indices is defined as |i-j|. If there is no special pair in the array, then return -1.


- **Approach 1: Bruteforce**
  - *Bruteforce way thinking*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 2
public int solve(int[] A) {

  HashMap<Integer, Integer> hm = new HashMap<>();

  int min_dis = Integer.MAX_VALUE;

  for(int i = 0; i < A.length; i++){

    if(hm.containsKey(A[i])){
      int dis = Math.abs(i-hm.get(A[i]));
      if(dis < min_dis){
        min_dis = dis;
      }
    }
    hm.put(A[i], i);
    
  }

  if(min_dis == Integer.MAX_VALUE){
    return -1;
  }

  return min_dis;
}
```
---

### 🧩 Problem 3: 
Groot has N trees lined up in front of him where the height of the i'th tree is denoted by H[i].

He wants to select some trees to replace his broken branches.

But he wants uniformity in his selection of trees.

So he picks only those trees whose heights have frequency B.

He then sums up the heights that occur B times. (He adds the height only once to the sum and not B times).

But the sum he ended up getting was huge so he prints it modulo 10^9+7.

In case no such cluster exists, Groot becomes sad and prints -1.

- **Approach 1: Bruteforce**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 3
public int getSum(int A, int B, int[] C) {

  double sum = 0;
  boolean flag = true;
  double mod = Math.pow(10,9) + 7;

  HashMap<Integer, Integer> hm = new HashMap<>();

  for(int i = 0; i < A; i++){
    hm.put(C[i], hm.getOrDefault(C[i],0)+1);

  }

  for(Integer ele : hm.keySet()){
    if(hm.get(ele) == B){
      sum = (sum + ele) % mod;
      flag = false;
    }
  }
  if(flag){
    return -1;
  }
  return (int) sum;
}
```
---

