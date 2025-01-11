
# 📅 Day 42: 2024-09-21

## 🚀 Problems Solved

---

### 🧩 Problem 1: Add Binary Strings
Given two binary strings A and B. Return their sum (also a binary string).
- **Approach 1: Bruteforce**
  - *Bruteforce thinking*
- **⏳ Time Complexity:** `O(max(m,n))`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public String addBinary(String A, String B) {

  StringBuilder sb = new StringBuilder();
  int n1 = A.length();
  int n2 = B.length();
  int i = n1 - 1;
  int j = n2 - 1;
  int sum = 0;
  int carry = 0;
  while( i >= 0 && j >= 0){
    int ld1 = A.charAt(i) - '0';
    int ld2 = (int)B.charAt(j) - '0';
    sum = (ld1+ld2+carry) % 2;
    carry = (ld1+ld2+carry) / 2;
    sb.append(sum);
    i--;
    j--;
  }
  if(n1 > n2){

    while( i>=0){
      int ld1 = (int)A.charAt(i) - '0';
      sum = (ld1+carry) % 2;
      carry = (ld1+carry) / 2;
      sb.append(sum);
      i--;
    }
  }
  else{

    while( j>=0){
      int ld1 =(int) B.charAt(j) - '0';
      sum = (ld1+carry) % 2;
      carry = (ld1+carry) / 2;
      sb.append(sum);
      j--;
    }
  }
  if(carry == 1){
    sb.append(carry);
  }
  return sb.reverse().toString();
}
```

- **Approach 2: Optimized**
  - *Same Logic but clean code with bit modifications*
- **⏳ Time Complexity:** `O(max(m,n))`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public String addBinary(String A, String B) {

  StringBuilder sb = new StringBuilder();
  int n1 = A.length();
  int n2 = B.length();
  int i = n1 - 1;
  int j = n2 - 1;
  int carry = 0;

  while(i>= 0 || j >= 0 || carry == 1){
    int ld1 = (i >= 0)? A.charAt(i) - '0': 0;
    int ld2 = (j >= 0)? B.charAt(j) - '0': 0;
    int sum = ld1 + ld2 + carry;
    sb.append(sum % 2);
    carry = sum/2;
    i--;
    j--;
  }



  return sb.reverse().toString();
}
```

---

### 🧩 Problem 2: 
You have an array A with N elements. We have two types of operation available on this array :
We can split an element B into two elements, C and D, such that B = C + D.
We can merge two elements, P and Q, to one element, R, such that R = P ^ Q i.e., XOR of P and Q.
You have to determine whether it is possible to convert array A to size 1, containing a single element equal to 0 after several splits and/or merge?

- **Approach 2: Optimized**
  - * Observation 1 from the given example if no is even in the array it becomes zero Ex 24 is 12 ^ 12 = 0, Observation 2 if an element is odd then divide the element in 1 and odd-1 element , odd-1 element is even which is zero, 1 will be remaining. observation 3- odd elements gives 1 if we have 3 odd elements xor of those results 1, so we should have odd elements of event length to get 0.*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 2
public String solve(int[] A) {
  int noOfOdds = 0;

  for(int i = 0; i < A.length; i++){
    if(A[i] % 2 != 0){
      noOfOdds++;
    }
  }
  if(noOfOdds % 2 == 0){
    return "Yes";
  }

  return "No";
}
```

---

### 🧩 Problem 3: Reverse the bits of an 32 bit unsigned integer A.
        00000000000000000000000000000011    
        11000000000000000000000000000000
- **Approach 1: Bruteforce**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(logn)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 3
public long reverse(long A) {
  if(A == 0){
    return 0;
  }
  StringBuilder sb = new StringBuilder();

  while(A!=0){
    sb.append((char) (A%2  + '0'));
    A = A/2;
  }
  int remlen = 32 - sb.length();

  for(int i = 0; i < remlen; i++){
    sb.append('0');
  }
  String reversestr = sb.toString();
  long result = 0;
  int k = 0;
  for(int i = reversestr.length()-1; i >= 0; i--){
    result += (reversestr.charAt(i) - '0' )* Math.pow(2, k);
    k++;
  }
  return result;
}
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

