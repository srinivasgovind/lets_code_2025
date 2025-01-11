
# 📅 Day 60: 2024-10-09

## 🚀 Problems Solved

---

### 🧩 Problem 1: 
Surprisingly, in an alien language, they also use English lowercase letters, but possibly in a different order. The order of the alphabet is some permutation of lowercase letters.




Given an array of words A of size N written in the alien language, and the order of the alphabet denoted by string B of size 26, return 1 if and only if the given words are sorted lexicographically in this alien language else, return 0.
- **Approach 1: Optimized**
  - *Think, space: O(26) which is constant*
- **⏳ Time Complexity:** `O(n * maxlength word)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int solve(String[] A, String B) {
  HashMap<Character, Integer> hm = new HashMap<>();
  for(int i = 0; i < B.length(); i++){
    hm.put(B.charAt(i), i);
  }

  for(int i = 1; i < A.length; i++){
    if(!compare(A[i-1], A[i], hm)){
      return 0;
    }
  }
  return 1;
}

boolean compare(String A, String B, HashMap<Character, Integer> hm){

  int min_length = Math.min(A.length(), B.length());

  for(int i = 0; i < min_length; i++){
    int pos1 = hm.get(A.charAt(i));
    int pos2 = hm.get(B.charAt(i));

    if(pos1 < pos2){
      return true;
    }

    if(pos1 > pos2){
      return false;
    }

  }

  return A.length() <  B.length();
}
```
---

### 🧩 Problem 2: 
Given an integer array A containing N distinct integers.




Find the number of unique pairs of integers in the array whose XOR is equal to B.

NOTE:

Pair (a, b) and (b, a) is considered to be the same and should be counted once.
- **Approach 1: Bruteforce**
  - *All Pairs*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 2
public int solve(int[] A, int B) {
  int count = 0;

  HashSet<Integer> hs = new HashSet<>();

  for(int i = 0; i < A.length; i++){

    for(int j = i+1; j < A.length; j++){

      if((A[i] ^ A[j]) == B){
        count++;
      }
    }
  }

  return count;
}
```

- **Approach 2: Optimized**
  - *Hashset similar to 2 sum approach*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 2
public int solve(int[] A, int B) {
  int count = 0;

  HashSet<Integer> hs = new HashSet<>();

  for(int i = 0; i < A.length; i++){

    int y = A[i] ^ B;

    if(hs.contains(y)){
      count++;
    }
    hs.add(A[i]);
  }

  return count;
}
```

---

### 🧩 Problem 3: 
Determine if a Sudoku is valid, according to: http://sudoku.com.au/TheRules.aspx

The Sudoku board could be partially filled, where empty cells are filled with the character '.'.
- **Approach 1: Bruteforce**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(n*n)`
- **💾 Space Complexity:** `O(n*n)`

```java
// Code implementation for Problem 3
public int isValidSudoku(final String[] A) {

  // create 9*9 matrix

  int[][] matrix = new int[9][9];

  for(int i  = 0; i < matrix.length; i++){

    String current_row = A[i];
    for(int j = 0; j < matrix[0].length; j++){
      char ch = current_row.charAt(j);
      if(ch >= 49 && ch <= 57){
        matrix[i][j] = ch - 48;
      }
    }
  }



  for(int i = 0; i < matrix.length; i++){
    int[] present_row = new int[matrix.length];
    int[] present_col = new int[matrix.length];
    for(int j = 0; j < matrix[0].length; j++){
      present_row[j] = matrix[i][j];
      present_col[j] = matrix[j][i];

    }
    if(!isValidRowOrColumn(present_row) || !isValidRowOrColumn(present_col)){
      return 0;
    }

  }

  for(int i = 0; i < matrix.length; i+=3){

    for(int j = 0; j < matrix.length; j+=3){

      if(!isValidSquare(matrix, i, j)){
        return 0;
      };
    }
  }

  return 1;
}

boolean isValidRowOrColumn(int[] row){

  HashSet<Integer> hs = new HashSet<>();

  for(int i = 0; i < row.length; i++){
    if(hs.contains(row[i]) && row[i] != 0){
      return false;
    }
    hs.add(row[i]);
  }
  return true;
}

boolean isValidSquare(int[][] matrix, int i , int j){
  HashSet<Integer> hs = new HashSet<>();
  for(int m = i; m < i+3; m++){

    for(int n = j; n < j+3; n++){

      if(matrix[m][n]!=0 && hs.contains(matrix[m][n])){
        return false;
      }
      hs.add(matrix[m][n]);
    }
  }
  return true;
}
```

- **Approach 2: Optimized**
  - *Reduced the loops, space still we use Hashset*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 3
public int isValidSudoku(final String[] A) {


  HashSet<Character> hs = new HashSet<>();



  for(int i = 0; i < A.length; i++){
    hs.clear();
    for(int j = 0; j < A[i].length(); j++){

      char ch = A[i].charAt(j);
      if(ch != '.' && hs.contains(ch)){
        return 0;
      }
      hs.add(ch);
    }


  }



  for(int i = 0; i < A.length; i++){
    hs.clear();
    for(int j = 0; j < A[i].length(); j++){

      char ch = A[j].charAt(i);
      if(ch != '.' && hs.contains(ch)){
        return 0;
      }
      hs.add(ch);
    }


  }



  for(int i = 0; i < A.length; i++){

    int x = i/3;
    int y = i%3;
    hs.clear();
    for(int m = x *3; m < x*3+3; m++){

      for(int n = y*3; n < y*3+3; n++){
        char ch = A[m].charAt(n);
        if(ch != '.' && hs.contains(ch)){
          return 0;
        }
        hs.add(ch);
      }
    }


  }

  return 1;
}
```

---

