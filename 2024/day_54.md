
# 📅 Day 54: 2024-10-03

## 🚀 Problems Solved

---

### 🧩 Problem 1: 
Find the number of occurrences of bob in string A consisting of lowercase English alphabets.
- **Approach 1: Bruteforce**
  - *Sliding Window Technique*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int solve(String A) {

  if(A.length() < 3){
    return 0;
  }
  int i = 0;
  int j = 2;
  int count = 0;
  while(j < A.length()){

    if(A.charAt(i) == 'b' && A.charAt(i+1) == 'o' && A.charAt(j) == 'b'){
      count++;
    }
    i++;
    j++;
  }
  return count;
}
```
---

### 🧩 Problem 2: 
You are given a string A of size N consisting of lowercase alphabets.
You can change at most B characters in the given string to any other lowercase alphabet such that the number of distinct characters in the string is minimized.

Find the minimum number of distinct characters in the resulting string.
- **Approach 1: **
  - * Freq array, eliminate low freq elements, so min no of unique characters achieved*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 2
public int solve(String A, int B) {
  if(B >= A.length()){
    return 1;
  }
  int[] freq = new int[26];

  for(int i = 0; i < A.length(); i++){
    char ch = A.charAt(i);
    int index = ch - 'a';
    freq[index]++;
  }
  int total_chars = 0;
  for(int i = 0; i < 26; i++){
    if(freq[i] != 0){
      total_chars++;
    }
  }

  Arrays.sort(freq);
  for(int i =0; i < 26; i++){
    if(freq[i] != 0 && B - freq[i] >= 0){
      B = B - freq[i];
      total_chars--;
    }
  }
  return total_chars;
}
```
---

### 🧩 Problem 3:
Akash likes playing with strings. One day he thought of applying following operations on the string in the given order:

Concatenate the string with itself.
Delete all the uppercase letters.
Replace each vowel with '#'.
You are given a string A of size N consisting of lowercase and uppercase alphabets. Return the resultant string after applying the above operations.

NOTE: 'a' , 'e' , 'i' , 'o' , 'u' are defined as vowels.
- **Approach 1: **
  - *Bruteforce thinking*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 3
public String solve(String A) {

  StringBuilder sb = new StringBuilder();

  for(int i = 0; i < A.length(); i++){
    char ch = A.charAt(i);

    if( ch >= 97 && ch <= 122){

      if(ch == 'a' || ch == 'e' || ch == 'i' || ch == 'o' || ch == 'u'){
        sb.append('#');
      }
      else{
        sb.append(ch);
      }

    }
  }
  return sb.toString() + sb.toString();
}
```
```

---

