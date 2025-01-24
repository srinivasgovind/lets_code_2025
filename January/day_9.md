
# 📅 Day 9: 2025-01-18

## What I Learned
- **Topic: Arrays**
- **Details: ADV DSA**
- **Streak Break Reason: No**

## 🚀 Problems Solved

---

### 🧩 Problem 1: Given two binary strings A and B. Return their sum (also a binary string).
- **Approach 1: Bruteforce**
  - *Iterate the strings, just perform binary sum of two numbers on paper, that's the intution*
- **⏳ Time Complexity:** `O(Max(A,B))`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public String addBinary(String A, String B) {

  int i = A.length() - 1;
  int j = B.length() - 1;
  int carry = 0;
  StringBuilder sb = new StringBuilder();

  while(i >= 0 && j >= 0){
    int x = A.charAt(i) - 48;
    int y = B.charAt(j) - 48;
    int sum = (x + y + carry) % 2;
    carry = (x + y + carry) / 2;
    sb.append(sum);
    i--;
    j--;
  }

  while(i >= 0){
    int x = A.charAt(i) - 48;
    int sum = (x + carry) % 2;
    carry = (x + carry ) / 2;
    sb.append(sum);
    i--;
  }
  while(j >= 0){
    int x = B.charAt(j) - 48;
    int sum = (x + carry) % 2;
    carry = (x + carry ) / 2;
    sb.append(sum);
    j--;
  }
  if(carry == 1){
    sb.append(carry);
  }
  return sb.reverse().toString();
}
```

- **Approach 2: Optimized**
  - *Optimized the code duplicate*
- **⏳ Time Complexity:** `O(max(A.length, B.length))`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public String addBinary(String A, String B) {

  int i = A.length() - 1;
  int j = B.length() - 1;
  int carry = 0;
  StringBuilder sb = new StringBuilder();

  while(i >= 0 || j >= 0){
    int x = i >= 0 ? A.charAt(i) - 48 : 0;
    int y = j >= 0 ? B.charAt(j) - 48 : 0;
    int sum = (x + y + carry) % 2;
    carry = (x + y + carry) / 2;
    sb.append(sum);
    i--;
    j--;
  }

  if(carry == 1){
    sb.append(carry);
  }
  return sb.reverse().toString();
}
```

---

### 🧩 Problem 2: 
Given an array of integers A, every element appears twice except for one. Find that integer that occurs once.

NOTE: Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

- **Approach 1: Bruteforce**
  - *Linear Search*
- **⏳ Time Complexity:** `O(nlogn)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 2
public int singleNumber(final List<Integer> A) {
  //sort takes nlogn 
  A.sort((a,b) -> a - b);

  int n = A.size();

  for(int i = 0; i < n; i++){
    int ele = A.get(i);
    if((i == 0 || ele != A.get(i-1)) && (i == n-1 || ele != A.get(i+1))){
      return ele;
    }
  }
  return -1;
}
```


- **Approach 2: Optimized**
  - *properties tell a^a = 0 and a^0 = a*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 2
public int singleNumber(final List<Integer> A) {

  int result = 0;

  for(int ele : A){
    result ^= ele;
  }
  return result;

}
```

---

### 🧩 Problem 3: 
You have an array A with N elements. We have two types of operation available on this array :
We can split an element B into two elements, C and D, such that B = C + D.
We can merge two elements, P and Q, to one element, R, such that R = P ^ Q i.e., XOR of P and Q.
You have to determine whether it is possible to convert array A to size 1, containing a single element equal to 0 after several splits and/or merge?

- **Approach 2: Optimized**
  - *Observations, 1. if element is even we can cosider as zero, bcz through split and xor 2. xor of odd numbers is even, xor of even and odd number is odd. conclusion if we do xor of all elements if there is odd count of odd numbers means "no" otherwise "yes". we will get result as odd ony if we have odd count of odd numbers, otherwise we get even result*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 3
public String solve(ArrayList<Integer> A) {
  int result = 0;
  for(int i = 0; i < A.size(); i++){
    result = ele ^ A.get(i);
  }

  if(result %2  == 0){
    return "Yes";
  }
  return "No";
}
```

---

