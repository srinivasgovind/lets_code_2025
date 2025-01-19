
# 📅 Day 7: 2025-01-16

## What I Learned
- **Topic:**
- **Details:**
- **Streak Break Reason: No**

## 🚀 Problems Solved

---

### 🧩 Problem 1: 
Given an array of non-negative integers A where each element represents your maximum jump length at that position.
The initial position is the first index of the array, and the goal is to reach the last index of the array with the minimum number of jumps.





Note: If it is not possible to reach the last index, return -1 instead.
- **Approach 1: Bruteforce**
  - *This approach check at every index min jumps required.. min_jumps[i] = min_jumps of prev j= 0 to i -1 + 1*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 1
public int solve(int[] A) {
  int n = A.length;
  int[] min_jumps = new int[n];


  for(int k = 0; k < n; k++){
    min_jumps[k] = Integer.MAX_VALUE;
  }
  min_jumps[0] = 0;
  for(int i = 1; i < n; i++){
    for(int j = 0; j <i; j++){
      if(A[j]+j >= i && min_jumps[j] != Integer.MAX_VALUE){
        min_jumps[i] = Math.min(min_jumps[i], min_jumps[j] + 1);

      }
    }
  }
  return min_jumps[n-1] == Integer.MAX_VALUE ? -1 : min_jumps[n-1];
}
```

- **Approach 2: Optimized**
  - *Greedy Approach*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int solve(int[] A) {

  int curr_far = 0;
  int farthest = 0;
  int jumps = 0;

  for(int i = 0; i < A.length-1; i++){
    if(curr_far < i){
      return -1;
    }
    farthest = Math.max(farthest, i+A[i]);

    if(curr_far == i){
      jumps++;
      curr_far = farthest;

      if(curr_far >= A.length-1){
        return jumps;
      }
    }
  }
  return -1;
}
```

---

### 🧩 Problem 2: 
You have a set of non-overlapping intervals. You are given a new interval [start, end], insert this new interval into the set of intervals (merge if necessary).

You may assume that the intervals were initially sorted according to their start times.
- **Approach 1: Bruteforce**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(nlogn)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 2
public ArrayList<Interval> insert(ArrayList<Interval> intervals, Interval newInterval) {
  //bruteforce apprach 
  intervals.add(newInterval);
  intervals.sort((a, b) -> a.start - b.start);

  ArrayList<Interval> result = new ArrayList<>();

  Interval prev = intervals.get(0);

  for(int i = 1; i < intervals.size(); i++){
    Interval current = intervals.get(i);
    if(current.start <= prev.end){
      prev.end = Math.max(prev.end, current.end);
    }else{
      result.add(prev);
      prev = current;
    }
  }

  // Add the last interval
  result.add(prev);

  return result;
}
```

- **Approach 2: Optimized**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 2
[Write your Java code here]
```

---

### 🧩 Problem 3: [Problem Title or Description]
- **Approach 1: Bruteforce**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 3
[Write your Java code here]
```

- **Approach 2: Optimized**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 3
[Write your Java code here]
```

---

