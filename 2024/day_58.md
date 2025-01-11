
# 📅 Day 58: 2024-10-07

## 🚀 Problems Solved

---

### 🧩 Problem 1: 
Given a string A consisting of lowercase characters.

Check if characters of the given string can be rearranged to form a palindrome.

Return 1 if it is possible to rearrange the characters of the string A such that it becomes a palindrome else return 0.
- **Approach 1: Bruteforce**
  - *Bruteforce thinking*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 1
public int solve(String A) {

  Map<Character, Integer> hm = new HashMap<>();

  for(int i = 0; i < A.length(); i++){
    char ch = A.charAt(i);
    hm.put(ch, hm.getOrDefault(ch, 0) + 1);
  }

  int count = 0;

  for(Character key : hm.keySet()){
    if(hm.get(key) % 2 != 0){
      count++;
    }
  }
  if(A.length() % 2 == 0 && count == 0){
    return 1;
  }
  else if(A.length() % 2 != 0 && count == 1){
    return 1;
  }

  return 0;
}
```

- **Approach 2: Optimized**
  - *used freq array instead of hashmap*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 1
public int solve(String A) {

  int[] freq = new int[26];

  for(int i = 0; i < A.length(); i++){
    char ch = A.charAt(i);
    freq[ch - 97]++;
  }

  int count = 0;

  for(int ele: freq){
    if(ele % 2 != 0){
      count++;
    }
  }
  if(count > 1){
    return 0;
  }

  return 1;
}
```

---

### 🧩 Problem 2: 
Given a number A, find if it is COLORFUL number or not.

If number A is a COLORFUL number return 1 else, return 0.

What is a COLORFUL Number:

A number can be broken into different consecutive sequence of digits.
The number 3245 can be broken into sequences like 3, 2, 4, 5, 32, 24, 45, 324, 245 and 3245.
This number is a COLORFUL number, since the product of every consecutive sequence of digits is different

- **Approach 1: Bruteforce**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(n^2)`

```java
// Code implementation for Problem 2
public int colorful(int A) {

  List<Integer> ls = new ArrayList<>();
  HashSet<Integer> hs = new HashSet<>();
  while( A > 0){
    ls.add(A%10);
    A = A/10;
  }



  for(int i = 0; i < ls.size(); i++){
    int prod = 1;
    for(int j = i; j < ls.size(); j++){

      prod *= ls.get(j);
      if(hs.contains(prod)){
        return 0;
      }
      hs.add(prod);
    }
  }

  return 1;
}
```
---

### 🧩 Problem 3: 
Given an array of positive integers A and an integer B, find and return first continuous subarray which adds to B.






If the answer does not exist return an array with a single integer "-1".

First sub-array means the sub-array for which starting index in minimum
- **Approach 1: Bruteforce(TLE)**
  - *All subarrays iterate and find B*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 3
public int[] solve(int[] A, int B) {

  int res_i = 0;
  int res_j = -1;
  boolean found = false;

  for(int i = 0; i < A.length; i++){

    long current_sum = 0;

    for(int j = i; j < A.length; j++){

      current_sum += A[j];

      if(current_sum == B){
        res_i = i;
        res_j = j;
        found = true;
        break;
      }
    }
    if (found){
      break;
    }
  }

  int[] result = new int[res_j - res_i + 1];

  if(!found){
    return new int[]{-1};
  }

  for(int k = res_i; k <= res_j; k++){
    result[k- res_i] = A[k];
  }
  return result;
}
```

- **Approach 2: Optimized**
  - *Optimized using prev sum hashmap, solved similar kind of problem but this intution is very imp*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 3
public int[] solve(int[] A, int B) {

  Map<Long, Integer> prevSum = new HashMap<>();
  prevSum.put(0L, -1);

  int res_i = -1;
  int res_j = -1;
  long sum = 0;

  for(int i = 0; i < A.length; i++){

    sum += A[i];

    if(prevSum.containsKey(sum-B)){
      res_i = prevSum.get(sum-B)+1;
      res_j = i;
      break;
    }
    prevSum.put(sum, i);
  }

  int[] result = new int[res_j - res_i + 1];

  if(res_i == -1){
    return new int[]{-1};
  }

  for(int k = res_i; k <= res_j; k++){
    result[k- res_i] = A[k];
  }
  return result;
}

```

---

