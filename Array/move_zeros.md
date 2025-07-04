# 📄 Move Zeroes — LeetCode Problem

---

## ✨ Problem Statement

**LeetCode Problem: Move Zeroes**

> Given an integer array `nums`, move all `0`'s to the end of it while maintaining the relative order of the non-zero elements.
>
> Note: You must do this in-place without making a copy of the array.

---

## ✅ Example

### Example 1

```
Input: nums = [0,1,0,3,12]
Output: [1,3,12,0,0]
```

### Example 2

```
Input: nums = [0]
Output: [0]
```

---

## 💡 Constraints

* `1 <= nums.length <= 10^4`
* `-2^31 <= nums[i] <= 2^31 - 1`

---

## 💬 Follow-up

Can you minimize the total number of operations done?

---

## 🗂️ Related Topics

* Array
* Two Pointers

---

## ⚡ Approach Explanation

### 🧠 Intuition

The main idea is to move all non-zero elements to the front of the array, keeping their relative order, and then fill the remaining positions with zeros.

---

### ❗ Important Points

* We are **not allowed to use extra copies of the array** (need to do it in-place).
* However, this solution uses an auxiliary array to clarify logic (before moving to a fully in-place optimization).

---

## 💻 Your Solution (with Extra Array)

```cpp
#include <bits/stdc++.h>
using namespace std;
class Solution {
 public:
  void moveZeroes(vector<int>& nums) {
    int increment = 0;
    vector<int> tempNums(nums.size());
    for (int i = 0; i < nums.size(); i++) {
      if (nums[i] != 0) {
        tempNums[increment] = nums[i];
        increment++;
      }
    }
    while (increment < tempNums.size()) {
      tempNums[increment] = 0;
      increment++;
    }
    for (int i = 0; i < tempNums.size(); i++) {
      nums[i] = tempNums[i];
      cout << nums[i] << " ";
    }
  }
};
```

---

## 📝 Explanation of Your Solution

### Step 1️⃣ — Create a Temporary Array

You initialize a temporary array `tempNums` of the same size as `nums`. This helps to separately build the non-zero sequence first.

---

### Step 2️⃣ — Copy Non-Zero Elements

You iterate over the original `nums` array, and whenever you find a non-zero element, you put it into `tempNums` at the current `increment` index.

```cpp
if (nums[i] != 0) {
  tempNums[increment] = nums[i];
  increment++;
}
```

---

### Step 3️⃣ — Fill Remaining with Zeros

After adding all non-zero elements, the remaining slots in `tempNums` are filled with zeros.

```cpp
while (increment < tempNums.size()) {
  tempNums[increment] = 0;
  increment++;
}
```

---

### Step 4️⃣ — Copy Back to Original Array

Finally, you overwrite the original `nums` array with `tempNums` contents.

```cpp
for (int i = 0; i < tempNums.size(); i++) {
  nums[i] = tempNums[i];
  cout << nums[i] << " ";
}
```

---

## ⚠️ Limitations

Although this approach is correct and easy to understand, it **does not strictly follow the in-place constraint** since it uses an extra temporary array.

---

## 🚀 Optimization Idea (In-Place)

If we want to strictly follow the problem requirement of no extra array, we can use the **Two Pointers technique** to shift non-zero elements forward directly in `nums` without using extra space.

---

## ✅ Summary

* The problem focuses on moving all zeros to the end of the array while preserving the order of non-zero elements.
* Your current approach clarifies the logic step by step using an extra array (easier to understand).
* For production or optimal solution, a pure in-place two-pointer approach is recommended to meet constraints.

---

## 💬 Topics Covered

* **Array**
* **Two Pointers**

---

## ⭐ Final Thoughts

Your current solution is a great first step to understand the algorithm and flow. Once comfortable, you can try improving it using purely in-place logic to further reduce space complexity.

---

### 🎉 Happy Coding!
