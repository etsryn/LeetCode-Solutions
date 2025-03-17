# 🧠 LeetCode Problem: Remove Element

## 📌 Problem Statement

Given an integer array `nums` and an integer `val`, remove all occurrences of `val` in `nums` <a href="https://en.wikipedia.org/wiki/In-place_algorithm">**in-place**</a>. The order of the elements may be changed. Then return the number of elements in `nums` which are **not equal** to `val`.

Consider the number of elements in `nums` which are not equal to `val` be `k`, to get accepted, you need to do the following things:

- Change the array `nums` such that the first `k` elements of `nums` contain the elements which are not equal to `val`. The remaining elements of `nums` are not important as well as the size of `nums`.
- Return `k`.

### Custom Judge:

The judge will test your solution with the following code:

> int[] nums = [...]; // Input array
> int val = ...; // Value to remove
> int[] expectedNums = [...]; // The expected answer with correct length.
>                             // It is sorted with no values equaling val.
> 
> int k = removeElement(nums, val); // Calls your implementation
> 
> assert k == expectedNums.length;
> sort(nums, 0, k); // Sort the first k elements of nums
> for (int i = 0; i < actualLength; i++) {
>     assert nums[i] == expectedNums[i];
> }
If all assertions pass, then your solution will be **accepted**.

### Example 1:

```plaintext
  Input: nums = [3,2,2,3], val = 3
  Output: 2, nums = [2,2,_,_]
  Explanation: Your function should return k = 2, with the first two elements of nums being 2.
  It does not matter what you leave beyond the returned k (hence they are underscores).
```

### Example 2:
```plaintext
  Input: nums = [0,1,2,2,3,0,4,2], val = 2
  Output: 5, nums = [0,1,4,0,3,_,_,_]
  Explanation: Your function should return k = 5, with the first five elements of nums containing 0, 0, 1, 3, and 4.
  Note that the five elements can be returned in any order.
  It does not matter what you leave beyond the returned k (hence they are underscores).
```

### Constraints:

- `0 <= nums.length <= 100`
- `0 <= nums[i] <= 50`
- `0 <= val <= 100`

## 💡 Approach 1: Brute Force (Naive) (Time Complexity: `O(n²)`)

### 🔧 C++ Solution

```cpp
class Solution {
public:
    int removeElement(vector<int>& nums, int val) {
        int k=0;
        for(int i=0; i<nums.size(); i++) {
            if(nums[i]!=val) {
                nums[k++] = nums[i];
            }
        }
        return k;
    }
};
```

#### Execution of above code:
```link
    https://leetcode.com/problems/remove-element/submissions/1575310045/
```

### 🔧 Java Solution

```java
class Solution {
    public int removeElement(int[] nums, int val) {
        int k=0;
        for(int i=0; i<nums.length; i++) {
            if(nums[i]!=val) {
                nums[k++] = nums[i];
            }
        }
        return k;
    }
}
```

#### Execution of above code:
```link
    https://leetcode.com/problems/remove-element/submissions/1575311968/
```

---

## 💡 Approach 2: Two Pointers (Efficient In-Place) (Time Complexity: `O(n)`)

- **Idea:** Use two pointers — one for iterating and one for writing only valid elements.

### 🔧 C++ Solution

```cpp
class Solution {
public:
    int removeElement(vector<int>& nums, int val) {
        int i = 0;
        for(int j=0; j<nums.size(); j++) {
            if(nums[j]!=val) {
                nums[i++] = nums[j];
            }
        }
        return i;
    }
};
```

#### Execution of above code:
```link
    https://leetcode.com/problems/remove-element/submissions/1575320604/
```

### 🔧 Java Solution

```java
class Solution {
    public int removeElement(int[] nums, int val) {
        int i = 0;
        for(int j=0; j<nums.length; j++) {
            if(nums[j]!=val) {
                nums[i++] = nums[j];
            }
        }
        return i;
    }
}
```

#### Execution of above code:
```link
    https://leetcode.com/problems/remove-element/submissions/1575321499/
```

---

## 💡 Approach 3: Swap to End (Fewer Writes) (Time Complexity: `O(n)`)

### 🔧 C++ Solution

```cpp
class Solution {
public:
    int removeElement(vector<int>& nums, int val) {
        int n = nums.size();
        int i = 0;
        while(i<n) {
            if(nums[i]==val) {
                nums[i] = nums[--n];
            } else {
                i++;
            }
        }
        return n;
    }
};
```

#### Execution of above code:
```link
    https://leetcode.com/problems/remove-element/submissions/1575316310/
```

### 🔧 Java Solution

```java
class Solution {
    public int removeElement(int[] nums, int val) {
        int n = nums.length;
        int i = 0;
        while(i<n) {
            if(nums[i]==val) {
                nums[i] = nums[--n];
            } else {
                i++;
            }
        }
        return n;
    }
}
```

#### Execution of above code:
```link
    https://leetcode.com/problems/remove-element/submissions/1575317408/
```

---

## 🔍 Comprehensive Complexity Analysis

| Approach         | Time Complexity | Space Complexity | Notes                                |
| ---------------- | --------------- | ---------------- | ------------------------------------ |
| Brute Force      | $O(n^2)$        | $O(1)$           | Shifts elements repeatedly           |
| Two Pointers     | $O(n)$          | $O(1)$           | Stable, maintains order              |
| Swap to End      | $O(n)$          | $O(1)$           | Unstable, faster for fewer writes    |

---

## 🏅 Key Takeaways

- **Brute Force:** Basic approach but inefficient for large inputs.
- **Two Pointers:** Best balance of performance and readability.
- **Swap to End:** Optimal when order doesn’t matter.
- **Edge Cases:** Handles arrays with all matching or no matching elements seamlessly.

Write code that not only solves problems but stands the test of time — precision, performance, and clarity matter most. 🎯
