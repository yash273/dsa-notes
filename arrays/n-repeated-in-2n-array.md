# 📌 Problem Overview

**Problem Name:**  N-Repeated Element in Size 2N Array
**LeetCode #:**  961
**Difficulty:** Easy 
**Category:** Array.  
**Core Pattern:**  Hashing, Pattern Based

---

## 🧠 Problem Restatement (In My Words)

given array, need to find which element repeats n times
where n = arr.length/2;
arr has n + 1 unique ele

---

## 🔍 Constraints & Observations

- Input size range: 2 <= n <= 5000

---

## ❌ Brute Force / Naive Approach

**Idea:**  
add each ele to set and check if it is repeating , if yes then return ele

**Algorithm:**
1. initialize set,
2. loop through the arr
3. check arr[i] exists in set or not
4. if yes then return arr[i] else add arr[i] to set

**Complexity:**
- Time Complexity: O(1)
- Space Complexity: O(n)

**Why this approach is suboptimal:**  
its taking extra space due to in worst case senario one has to store n + 1 elements

---

## 💡 Key Insight (Breakthrough)

> there are 2n positions, in which one element repeats n times,
> so we can say that elements cannot stay saparated for so long,
> can say that repeated element must appear at most 2 indices apart somewhare in arr

---

## ✅ Optimal Approach

### 🔧 Algorithm (Step-by-Step)

1. loop through the arr
2. compare arr[i] == arr[i + 1] || arr[i] == arr[i + 2]
3. if conditions met then return element

---

### 💻 Implementation

#### JavaScript
```js
// Write clean, readable code
// Avoid clever hacks
```

#### c++
```cpp
// less optimal

class Solution {
public:
    int repeatedNTimes(vector<int>& nums) {
        unordered_set<int> s;
        for (int n : nums) {
            if (s.count(n))
                return n;
            s.insert(n);
        }
        return -1;
    }
};

//optimal

class Solution {
public:
    int repeatedNTimes(vector<int>& nums) {
        for(int i = 0; i < nums.size() - 2; i++){
            if(nums[i] == nums[i + 1] || nums[i] == nums[i + 2]){
                return nums[i];
            }
        }
        return nums.back();
    }
};
```