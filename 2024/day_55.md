
# 📅 Day 55: 2024-10-04

## 🚀 Problems Solved

---

### 🧩 Problem 1: 
Given the array of strings A, you need to find the longest string S, which is the prefix of ALL the strings in the array.


The longest common prefix for a pair of strings S1 and S2 is the longest string S which is the prefix of both S1 and S2.

Example: the longest common prefix of "abcdefgh" and "abcefgh" is "abc".
- **Approach 1: Bruteforce**
  - * easy problem, needs little bit observations*
- **⏳ Time Complexity:** `O(min_len_str * n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public String longestCommonPrefix(String[] A) {

  String min_length = A[0];

  //finding min_length string
  for(int i = 1; i < A.length; i++){
    if(A[i].length() < min_length.length()){
      min_length = A[i];
    }
  }
  // ans variable to store final ans
  String ans = "";


  //actual logic to find common prefix
  for(int i = 0; i < min_length.length(); i++){

    char ch = min_length.charAt(i);
    boolean isQualified = true;

    for(int j = 0; j < A.length; j++){

      if(A[j].charAt(i) != ch){
        isQualified = false;
        break;
      }
    }

    if(isQualified){
      ans += ch;
    }
    else{
      return ans;
    }
  }
  return ans;

}
```

- **Approach 2: Optimized**
  - *small changes which improves coding style*
- **⏳ Time Complexity:** `O(min_len_str * n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public String longestCommonPrefix(String[] A) {

  int min_length = Integer.MAX_VALUE;

  //finding min_length string
  for(int i = 0; i < A.length; i++){
    if(A[i].length() < min_length){
      min_length = A[i].length();
    }
  }
  // ans variable to store final ans
  String ans = "";


  //actual logic to find common prefix
  for(int i = 0; i < min_length; i++){

    char ch = A[0].charAt(i);
    boolean isQualified = true;

    for(int j = 1; j < A.length; j++){

      if(A[j].charAt(i) != ch){
        isQualified = false;
        break;
      }
    }

    if(isQualified){
      ans += ch;
    }
    else{
      return ans;
    }
  }
  return ans;

}
```

---

### 🧩 Problem 2: 
Given a string A of size N, find and return the longest palindromic substring in A.

Substring of string A is A[i...j] where 0 <= i <= j < len(A)

Palindrome string:
A string which reads the same backwards. More formally, A is palindrome if reverse(A) = A.

Incase of conflict, return the substring which occurs first ( with the least starting index).

- **Approach 1: Bruteforce**
  - *Iterate over all substrings and check whether they are palidromes and keep a track of longest one*
- **⏳ Time Complexity:** `O(n^3)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 2
public String longestPalindrome(String A) {

  int max_i = 0;
  int max_j = 0;
  int max_len = 1;

  for(int i = 0; i < A.length(); i++){

    for(int j = i;  j < A.length(); j++){

      boolean check = isPalindrome(A, i, j);

      // if it is a isPalindrome
      if(check){
        int len = j - i + 1;
        if(len > max_len){
          max_len = len;
          max_i = i;
          max_j = j;
        }
      }
    }
  }

  //ans will be max_i to max_j
  String ans = "";
  for(int k = max_i; k <= max_j; k++){
    ans += A.charAt(k);
  }
  return ans;
}

//Palindrome check
boolean isPalindrome(String A, int i , int j){

  while(i < j){
    if(A.charAt(i) != A.charAt(j)){
      return false;
    }
    i++;
    j--;
  }
  return true;
}
```

- **Approach 2: Optimized**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 2
public String longestPalindrome(String A) {

  int max_i = 0;
  int max_j = 0;
  int max_len = 1;
  //odd length substring
  for(int mid = 0; mid < A.length(); mid++){
    int i = mid;
    int j = mid;
    while(i >= 0 && j < A.length() && A.charAt(i) == A.charAt(j)){
      i--;
      j++;
    }

    int len = j - i - 1;
    if(len > max_len){
      max_len = len;
      max_i = i+1;
      max_j = j-1;
    }
  }

  //even length substring
  for(int mid = 0; mid < A.length() - 1; mid++){
    int i = mid;
    int j = mid+1;
    while(i >= 0 && j < A.length() && A.charAt(i) == A.charAt(j)){
      i--;
      j++;
    }

    int len = j - i - 1;
    if(len > max_len){
      max_len = len;
      max_i = i+1;
      max_j = j-1;
    }
  }


  //ans will be max_i to max_j

  String ans = "";
  for(int k = max_i; k <= max_j; k++){
    ans += A.charAt(k);
  }
  return ans;
}

```

---

### 🧩 Problem 3: 
In a country where everyone wants a boy, each family continues having babies till they have a boy. After a long time, what is the proportion of boys to girls in the country? (Assuming probability of having a boy or a girl is the same) > Round off your answer to two decimal places and output the answer as I.xx where I is the integer part of your answer, and xx is the first two decimal places of the rounded-off answer.
- **Approach 1:  Take 16 families ,  8 families will have only 1 boy, 8 families will have a girl, then they again continue, resulting 4 families will have boy and 4 will have girl, 4 girl again contineu so 2 boys and 2 girls, 2 girls to 1 boy and 1 girl. calculate total no of boys vs girls. it should be almost equal ratio 1:1. for larger input this holds true as well.**

---

