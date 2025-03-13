# 🧠 LeetCode Problem: Two Sum

## 📌 Problem Statement

Given an array of integers `nums` and an integer `target`, return **indices** of the two numbers such that they add up to `target`.

You may assume that each input would have **exactly one solution**, and you **may not use the same element twice**.

You can return the answer in **any order**.

### Example 1:

```plaintext
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: nums[0] + nums[1] == 9, so return [0, 1].
```
### Example 2:

```plaintext
Input: nums = [3,2,4], target = 6
Output: [1,2]
```
### Example 3:

```plaintext
Input: nums = [3,3], target = 6
Output: [0,1]
```

---

### Constraints
- `2 <= nums.length <= 104`<br />
- `-109 <= nums[i] <= 109`<br />
- `-109 <= target <= 109`<br />
- `Only one valid answer exists`<br />

Follow-up: Can you come up with an algorithm that is less than O(n2) time complexity?

---

## 💡 Approach 1: Brute Force (Time Complexity: O(n²))

### 🔧 C++ Solution
```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        for(int i=0; i<nums.size(); ++i) {
            for(int j=i+1; j<nums.size(); ++j) {
                if (nums[i] + nums[j] == target) {
                    return {i, j};
                }
            }
        }
        return {};
    }
};
```

### 🔧 Java Solution
```java
import java.util.*;

public class TwoSum {
    public int[] twoSum(int[] nums, int target) {
        for (int i = 0; i < nums.length; i++) {
            for (int j = i + 1; j < nums.length; j++) {
                if (nums[i] + nums[j] == target) {
                    return new int[]{i, j};
                }
            }
        }
        return new int[]{};
    }
}
```

---

## 💡 Approach 2: Hash Map (Time Complexity: O(n))

### 🔧 C++ Solution
```cpp
#include <vector>
#include <unordered_map>
using namespace std;

vector<int> twoSum(vector<int>& nums, int target) {
    unordered_map<int, int> map;
    for (int i = 0; i < nums.size(); i++) {
        int complement = target - nums[i];
        if (map.find(complement) != map.end()) {
            return {map[complement], i};
        }
        map[nums[i]] = i;
    }
    return {};
}
```

### 🔧 Java Solution
```java
import java.util.*;

public class TwoSumHashMap {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            int complement = target - nums[i];
            if (map.containsKey(complement)) {
                return new int[]{map.get(complement), i};
            }
            map.put(nums[i], i);
        }
        return new int[]{};
    }
}
```

---

## 🔍 Complexity Analysis

| Approach      | Time Complexity | Space Complexity |
|---------------|------------------|------------------|
| Brute Force   | O(n²)            | O(1)             |
| Hash Map      | O(n)             | O(n)             |

---

## 🏅 Key Takeaways

- **Brute Force:** Simple but inefficient for large datasets.
- **Hash Map:** Efficient for both time and space, optimal solution.
- **Edge Cases:** Consider duplicates, negative numbers, and minimum array sizes.

Happy problem solving! 🚀

