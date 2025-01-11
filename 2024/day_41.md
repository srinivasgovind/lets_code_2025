
# 📅 Day 41: 2024-09-20

## 🚀 Problems Solved

---

### 🧩 Problem 1: Length of longest consecutive ones
Given a binary string A. It is allowed to do at most one swap between any 0 and 1. Find and return the length of the longest consecutive 1’s that can be achieved.
- **Approach 1: Bruteforce**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int solve(String A) {
  int maxAns=0;
  int ones=0;
  for(int i=0;i<A.length();i++){
    char ch=A.charAt(i);
    if(ch=='1'){
      ones++;
    }
  }
  if(ones==A.length()){
    return ones;
  }
  for(int i=0;i<A.length();i++){
    char ch=A.charAt(i);
    int left=0;
    int right=0;
    if(ch=='0'){
      for(int j=i-1;j>=0;j--){
        char ch1=A.charAt(j);
        if(ch1=='1'){
          ++left;
        }else{
          break;
        }
      }
      for(int j=i+1;j<A.length();j++){
        char ch1=A.charAt(j);
        if(ch1=='1'){
          ++right;
        }else{
          break;
        }
      }
      int sum=left+right;
      if (sum < ones)
        maxAns = Math.max(maxAns, sum + 1);

      else
        maxAns = Math.max(maxAns, sum);

    }

  }
  return maxAns;
}
```

- **Approach 2: Optimized**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 1
public int solve(String A) {

  int n = A.length();

  int left[] = new int[n];
  int right[] = new int[n];

  if(A.charAt(0)=='1'){
    left[0] = 1;

  }else{
    left[0] = 0;
  }

  if(A.charAt(n-1)== '1'){
    right[n-1] = 1;
  }else{
    right[n-1] = 0;
  }

  for(int i=1; i<n; i++){
    if(A.charAt(i) == '1'){
      left[i] = left[i-1]+1;
    }
    else{
      left[i] = 0;
    }
  }
  for(int i = n-2; i>=0; i--){
    if(A.charAt(i) == '1'){
      right[i] = right[i+1]+1;
    }else{
      right[i] = 0;
    }
  }
  int max_count = 0;
  int sum = 0;
  int total_ones = 0;
  for(int i = 0; i < n; i++){
    max_count = Math.max(max_count, left[i]);
    if(A.charAt(i) == '1'){
      total_ones++;
    }
  }

  for(int j = 1; j < n-1; j++){
    if(A.charAt(j)=='0'){
      sum = left[j-1]+right[j+1];
      if(sum<total_ones){
        sum+=1;
      }
      max_count = Math.max(max_count, sum);
    }
  }
  return max_count;

}
```

---

### 🧩 Problem 2: 
Given an array of integers A, every element appears twice except for one. Find that integer that occurs once.

NOTE: Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?
- **Approach 1: Bruteforce**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 2
public int singleNumber(final int[] A) {
  Map<Integer, Integer> map = new HashMap<>();
  for(int i = 0; i < A.length; i++){
    if(map.containsKey(A[i])){
      map.put(A[i], 2);
    }else{
      map.put(A[i],1);
    }
  }

  for(Map.Entry<Integer,Integer> item: map.entrySet()){
    if(item.getValue() == 1){
      return item.getKey();
    }
  }
  return -1;
}
```

- **Approach 2: Optimized**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 2
public int singleNumber(final int[] A) {

  int ans = 0;
  for(int i = 0; i < A.length; i++){
    ans = ans ^ A[i];
  }
  return ans;
}
```

---

### 🧩 Problem 3: 
Write a function that takes an integer and returns the number of 1 bits present in its binary representation.
- **Approach 1: Bruteforce**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(logn)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 3
public int numSetBits(int A) {
  int noOfOnes = 0;

  while(A > 0){

    noOfOnes += A %2;
    A = A/2;

  }
  return noOfOnes;
}
```

- **Approach 2: Optimized**
  - *The number of iterations of the while loop depends on how many set bits are in the binary representation of A.

In the worst case, if all bits of A are set (e.g., for a number like 1111...1111), the number of iterations would be equal to the number of bits in A.

For a 32-bit integer, the loop will run at most 32 times (if all bits are 1s).

Therefore, the time complexity of the function is O(number of set bits in A), which in the worst case is O(log A) for an integer A, because the number of bits required to represent A in binary is proportional to log A.*
- **⏳ Time Complexity:** `O(logA)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 3
public int numSetBits(int A) {
  int noOfOnes = 0;

  while(A != 0){
    A = A & (A - 1);
    noOfOnes += 1;

  }
  return noOfOnes;
}
```

---

