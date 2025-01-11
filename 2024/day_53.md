
# 📅 Day 53: 2024-10-02

## 🚀 Problems Solved

---

### 🧩 Problem 1: 
Given a string A, you are asked to reverse the string and return the reversed string.
- **Approach 1: Bruteforce**
  - *Bruteforce way *
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 1
public String solve(String A) {

  char[] charArray = A.toCharArray();

  int i = 0;
  int j = A.length() - 1;

  while(i < j){
    char temp = charArray[i];
    charArray[i] = charArray[j];
    charArray[j] = temp;
    i++;
    j--;
  }
  return new String(charArray);
}
```
---

### 🧩 Problem 2: 
you are given a string A of size N.


Return the string A after reversing the string word by word.

NOTE:

A sequence of non-space characters constitutes a word.
Your reversed string should not contain leading or trailing spaces, even if it is present in the input string.
If there are multiple spaces between words, reduce them to a single space in the reversed string.
- **Approach 1: Optimized**
  - *think the problem and divide it *
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 2
public String solve(String A) {
  char[]  charArray = A.toCharArray();
  int i = 0;
  int j = 0;

  reverse( charArray, i , A.length() -1);

  while(j < A.length()){
    while(j < A.length() && charArray[j] != ' '){
      j++;
    }
    reverse(charArray, i, j-1);

    j++;
    i = j;
  }
  return cleanString(charArray);
}

void reverse(char[] charArray, int x , int y){

  while(x < y){
    char temp = charArray[x];
    charArray[x] = charArray[y];
    charArray[y] = temp;
    x++;
    y--;
  }
}

String cleanString(char[] arr){
  int i = 0;
  int j = 0;
  int n = arr.length;
  while(j < n ){

    while(j<n && arr[j] == ' '){
      j++;
    }

    while(j<n && arr[j] != ' '){
      arr[i] = arr[j];
      i++;
      j++;
    }
    while(j<n && arr[j] == ' '){
      j++;
    }
    if(j<n){
      arr[i] = ' ';
      i++;
    }
  }
  return new String(arr, 0, i);
}

```
---

### 🧩 Problem 3: You are given a string S, and you have to find all the amazing substrings of S.

An amazing Substring is one that starts with a vowel (a, e, i, o, u, A, E, I, O, U).

Input
- **Approach 1: Bruteforce**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 3
public int solve(String A) {

  int result = 0;

  int n = A.length() - 1;
  for(int i = 0; i < A.length(); i++){
    if(A.charAt(i) == 'a' || A.charAt(i) == 'e' || A.charAt(i) == 'i' || A.charAt(i) == 'o' || A.charAt(i) == 'u' || A.charAt(i) == 'A' ||
            A.charAt(i) == 'E' || A.charAt(i) == 'I'|| A.charAt(i) == 'O'|| A.charAt(i) == 'U'){
      result  =  (result + (n - i + 1)) % 10003;
    }
  }
  return result;
}
```
---

