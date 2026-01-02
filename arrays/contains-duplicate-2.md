# 📌 Problem Overview

**Problem Name:**  Contains Duplicate 2
**LeetCode #:**  219
**Difficulty:** Easy 
**Category:** Array  
**Core Pattern:** Hashing(map)

---

## 🧠 Problem Restatement (In My Words)

given int array and int k, if two value arr[i] and arr[j] at diff index are same and 
abs(i - j) <= k; (means the difference of position should not be greater than k) return true.
else return false.
---

## 🔍 Constraints & Observations

- Input size range:0 <= 10^5
- Value range: any
- Order does not matter
- we care about duplicate value not count 

- if all elements are unique, the value of k must be 0,
- 
---

## ❌ Brute Force / Naive Approach

**Idea:**  
we can make nested loops and check with condition, if satisfy than return true else false.

**Algorithm:**
1. outer loop i, inner loop j > i.
2. check for arr[i] === arr[j] and abs(i - j ) <= k
3. if a match is found, return true else false

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

1. create an emplty map
2. iterate through the array
3. if current element is already in map and satisfy condition, return true
4. otherwise, add the element to map
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

//brute force:

class Solution {
public:
    bool containsNearbyDuplicate(vector<int>& nums, int k) {
        int n = nums.size();
        for (int i = 0; i < n; i++) {
            for (int j = i + 1; j < n; j++) {
                if (nums[i] == nums[j] && abs(i - j) <= k) {
                    return true;
                }
            }
        }
        return false;
    }
};

// optimized solution 
class Solution {
public:
    bool containsNearbyDuplicate(vector<int>& nums, int k) {
        unordered_map<int,int> m;
            for(int i = 0; i < nums.size(); i++) {
                if (m.count(nums[i]) && abs(i - m[nums[i]]) <= k) {
                    return true;
                }
                m[nums[i]] = i;
            }
        return false;
    }
};
```