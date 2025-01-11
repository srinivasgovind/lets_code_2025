
# 📅 Day 3: 2024-08-13

## 🚀 Problems Solved

---

### 🧩 Problem 1: Group Anagram
- **Approach:**
  - *Sort the Strings and maintain map of List to group them.*
- **⏳ Time Complexity:** `O(n * klogk)`
- **💾 Space Complexity:** `O(n * k)`

```java
// Code implementation for Problem 1
public List<List<String>> groupAnagrams(String[] strs) {
  Map<String, List<String>>  hm = new HashMap<>();
  List<List<String>> result = new ArrayList<>();
  for(String str: strs){
    char[] chars = str.toCharArray();
    Arrays.sort(chars);
    String sorted = new String(chars);

    if(!hm.containsKey(sorted)){
      hm.put(sorted, new ArrayList<>());
    }
    hm.get(sorted).add(str);
  }
  for(String key : hm.keySet()){
    result.add(hm.get(key));
  }
  return result;
}
```

---

### 🧩 Problem 2: Top K Frequent Elements
- **Approach1:**
  - * Sort the array, store the unique elements and their frequency and iterate k times hashmap to find highest frequent element*
- **⏳ Time Complexity:** `for smaller inputs O(nlogn) otherwise O(n*k)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 2
public int[] topKFrequent(int[] nums, int k) {

  Arrays.sort(nums);

  Map<Integer, Integer> hm = new HashMap<>();

  List<Integer> results = new ArrayList<>();

  for(int num : nums){

    hm.put(num, hm.getOrDefault(num,0)+1);

  }

  for(int i = 0; i < k ;i++){
    int highestKey = -1;
    int highestValue = -1;
    for(Map.Entry<Integer, Integer> key: hm.entrySet()){
      if(key.getValue() > highestValue){
        highestValue = key.getValue();
        highestKey = key.getKey();
      }
    }
    results.add(highestKey);
    hm.put(highestKey, -1);
  }
  int[] resultArray = new int [results.size()];
  for(int i = 0 ;i < results.size();i++){
    resultArray[i] = results.get(i);
  }
  return resultArray;
}
```

- **Approach2:**
  - * This is efficient approach, here we store the arr elements and their freq in hashmap, create a bucket where indexes will act like frequency array value will have List which stores elements having same frequency
    reason behind this intution is frequency will be always [1, N] if we iterate bucket from backwards N-1 index gives key with most frequent* 
- **⏳ Time Complexity:** `for smaller inputs O(nlogn) otherwise O(n*k)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 2
public int[] topKFrequent(int[] nums, int k) {
  Map<Integer, Integer> map = new HashMap<>();
  List<Integer> bucket[] = new List[nums.length + 1];

  for(int num : nums){
    map.put(num, map.getOrDefault(num,0) + 1);
  }

  for(int key : map.keySet()){
    int value = map.get(key);

    if(bucket[value] == null){
      bucket[value] = new ArrayList<>();
    }
    bucket[value].add(key);
  }

  int result[] = new int[k];
  int ptr = 0;

  for(int i = bucket.length - 1; i > 0 ; i--){
    if(bucket[i] != null){
      for(int p = 0; p < bucket[i].size() && k > 0; p++){
        result[ptr] = bucket[i].get(p);
        ptr++;
        k--;
      }
    }
  }
  return result;
}
```

---

