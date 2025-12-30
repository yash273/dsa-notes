# 📌 Problem Overview

**Problem Name:**  Contains Duplicate
**LeetCode #:**  217
**Difficulty:** Easy 
**Category:** Array  
**Core Pattern:** Hashing(set)

---

## 🧠 Problem Restatement (In My Words)

given int array, need to find any value appears more than one,
if at least one occures more than one, return true, else false,
---

## 🔍 Constraints & Observations

- Input size range:0 <= 10^5
- Value range: any
- Order does not matter
- we only care about the dupllicates not the count 

- if all elements are unique, the number of unique elements equals to the lenght of array.

---

## ❌ Brute Force / Naive Approach

**Idea:**  
Compare every elements of arr with every other element.

**Algorithm:**
1. loop through each element.
2. for each element, compare it with all following elements
3. if a match is found, return true

**Complexity:**
- Time Complexity: O(n2)
- Space Complexity: O(1)

**Why this approach is suboptimal:**  
when larger input the nested loops may cause TLE

---

## 💡 Key Insight (Breakthrough)

> if we can track elements we have already seen unsing a hash-based structure, we can detect duplicates 

(Keep this to 1–3 precise sentences.)

---

## ✅ Optimal Approach

### 🔧 Algorithm (Step-by-Step)

1. create an emplty set
2. iterate through the array
3. if current element is already in set, return true
4. otherwise, add the element to set
5. if loop completes return false
---

### 💻 Implementation

#### JavaScript
```js
// Write clean, readable code
// Avoid clever hacks
```

#### c++
```cpp
class Solution {
    bool containsDuplicates(vector<int>& nums) {
        unordered_set<int> s;
        for (int n : nums) {
            if (s.count(n)) return true;
            s.insert(n);
        }
        return false;
    }
}
```