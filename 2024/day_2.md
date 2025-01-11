
# 📅 Day 2: 2024-08-12

## 🚀 Problems Solved

---

### 🧩 Problem 1: TWO SUM
- **Approach1:**
  - * Iterate through inner loop and compare all the cases*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int[] twoSum(int[] nums, int target) {

  int[]  result = new int[2];
  for(int i = 0 ; i < nums.length -1; i++){
      for(int j = i + 1; j < nums.length; j++){
          if(nums[i] + nums[j] == target){
              result[0] = i;
              result[j] = j;
          }
      }

  }

  return result;
}

```

- **Approach2:**
  - *Using HashMap store prev inputs and their ith location*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 1
public int[] twoSum(int[] nums, int target) {

  Map<Integer,Integer> hm = new HashMap<>();

  int[]  result = new int[2];
  for(int i = 0 ; i < nums.length; i++){

    if(hm.containsKey(target-nums[i])){
      result[0] = i;
      result[1] = hm.get(target-nums[i]);
    }
    else{
      hm.put(nums[i],i);
    }

  }

  return result;
}
```

---

### 🧩 Problem 2: Contains Duplicate
- **Approach1:**
  - * Sort the array and compare prev element with current( 2 pointers)*
- **⏳ Time Complexity:** `O(nlogn)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 2
public boolean containsDuplicate(int[] nums) {
  Arrays.sort(nums);
  int prev = 0;
  for(int i = 1; i < nums.length ; i++){
    if(nums[i] == nums[prev]){
      return true;
    }
    prev++;
  }
  return false;
}
```

- **Approach2:**
  - * Set to store the elements and find duplicates with Set*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 2
public boolean containsDuplicate(int[] nums) {
  Set<Integer> hs = new HashSet<>();

  for(int num : nums){
    if(hs.contains(num)){
      return true;
    }
    hs.add(num);
  }
  return false;
}
```
---

### 🧩 Problem 3: Valid Anagram
- **Approach1:**
  - * Store both strings in two hashmaps and compare both values are same*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 3
public boolean isAnagram(String s, String t) {

  if(s.length() != t.length()){
    return false;
  }

  Map<Character, Integer> hm1 = new HashMap<>();
  Map<Character, Integer> hm2 = new HashMap<>();
  
  for(char ch : s.toCharArray()){
    hm1.put(ch,hm1.getOrDefault(ch,0)+1);
  }

  for(char ch : t.toCharArray()){
    hm2.put(ch, hm2.getOrDefault(ch,0)+1);
  }

  for(char ch : s.toCharArray()){
    if( !hm2.containsKey(ch) || !hm1.get(ch).equals(hm2.get(ch))){
      return false;
    }
  }
  return true;
}
```

- **Approach2:**
  - * Using Single Hashmap to manpulate both strings count*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 3
public boolean isAnagram(String s, String t) {

  if(s.length() != t.length()){
    return false;
  }

  Map<Character, Integer> hm = new HashMap<>();

  for(char ch : s.toCharArray()){
    hm.put(ch,hm.getOrDefault(ch,0)+1);
  }

  for(char ch : t.toCharArray()){
    hm.put(ch, hm.getOrDefault(ch,0)-1);
  }

  for(char ch : hm.keySet()){
    if(hm.get(ch) != 0){
      return false;
    }
  }
  return true;
}
```

- **Approach:3**
  - * HashTable using Array*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 3
public boolean isAnagram(String s, String t) {

  int[] charMap = new int[26];

  for(char ch : s.toCharArray()){
    charMap[ch-97]++; //count[x - 'a']++;
  }


  for(char ch : t.toCharArray()){
    charMap[ch-97]--; //count[x - 'a']--;
  }

  for(int count: charMap){
    if(count != 0){
      return false;
    }
  }
  return true;
}
```
---

