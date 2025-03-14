# 🧠 LeetCode Problem: Maximum Candies Allocated to K Children

## 📌 Problem Statement

You are given a **0-indexed** integer array `candies`. Each element in the array denotes a pile of candies of size `candies[i]`. You can divide each pile into any number of **sub piles**, but you **cannot** merge two piles together.

You are also given an integer `k`. You should allocate piles of candies to `k` children such that each child gets the **same** number of candies. Each child can be allocated candies from **only one** pile of candies and some piles of candies may go unused.

Return the **maximum number of candies** each child can get.

### Example 1:

```plaintext
Input: candies = [5,8,6], k = 3
Output: 5
Explanation: We can divide candies[1] into 2 piles of size 5 and 3, and candies[2] into 2 piles of size 5 and 1. We now have five piles of candies of sizes 5, 5, 3, 5, and 1. We can allocate the 3 piles of size 5 to 3 children. It can be proven that each child cannot receive more than 5 candies.
```

### Example 2:

```plaintext
Input: candies = [2,5], k = 11
Output: 0
Explanation: There are 11 children but only 7 candies in total, so it is impossible to ensure each child receives at least one candy. Thus, each child gets no candy and the answer is 0.
```

### Constraints:

- `1 <= candies.length <= 105`
- `1 <= candies[i] <= 107`
- `1 <= k <= 1012`

---

## 💡 Approach: Binary Search (Time Complexity: O(n log(sum(candies)/k)))

### 🔧 C++ Solution
```cpp
class Solution {
    public:
    int maximumCandies(vector<int>& candies, long long k) {
        // Calculating the total number of candies available
        // Using a long long to avoid overflow with large values
        long long sum = 0;
        for(int candy : candies) {
            sum += candy;
        }
        
        // Edge Case 1: If total candies are less than k,
        // It is impossible to give each child at least one candy
        if(sum < k) return 0;
        
        // Edge Case 2: If there's only one pile, return the integer division of that pile by k
        if(candies.size() == 1) return candies[0] / k;
        
        // Defining the search boundaries for binary search.
        // l: Minimum candies per child (at least 1)
        // r: Maximum candies per child, which is sum/k (if candies were evenly distributed).
        int l = 1;
        int r = sum / k;
        
        // Performing binary search to find the maximum feasible number of candies per child
        // Using the condition 'l < r' with a mid-point calculation of (l + r + 1) / 2
        while(l < r) {
            // Calculating the middle point
            int m = (l + r + 1) / 2;
            
            // Checking if it is possible to distribute m candies per child to at least k children
            // This function calculates how many children can be served with m candies each
            if(numChildren(candies, m) >= k)
                l = m; // If possible, try to see if we can give more candies (search right half)
            else
                r = m - 1; // Otherwise, search the left half (reduce the number)
        }
        
        // When the loop ends, l is the maximum valid number of candies per child.
        return l;
    }
    
private:
    /**
     * Helper function that calculates how many children can receive m candies each
     * It does this by summing up the number of full m-candy distributions from each pile
     *
     * @param candies: vector of candy counts for each pile
     * @param m: number of candies to give to each child
     * @return The total number of children that can be served
     */
    long long numChildren(const vector<int>& candies, int m) {
        long long count = 0;
        for(int candy : candies) {
            count += candy / m; // Integer division counts full groups of m candies that can be formed
        }
        return count;
    }
};
```

#### Execution of above code:
```link
    https://leetcode.com/problems/maximum-candies-allocated-to-k-children/?envType=daily-question&envId=2025-03-14
```

### 🔧 Java Solution
```java
class Solution {
    public int maximumCandies(int[] candies, long k) {
        // Calculate the total number of candies available
        long sum = Arrays.stream(candies).asLongStream().sum();

        // Edge Case - If total candies are less than k, distribution is impossible
        if(sum < k) return 0;  

        // Edge Case - If only one pile exists, return its division by k
        if(candies.length == 1) return (int) (candies[0] / k);  

        // Define binary search boundaries
        int l = 1; // Minimum possible candies per child (at least 1)
        int r = (int) (sum / k); // Maximum possible candies per child

        // Perform binary search to find the maximum possible candies per child
        while(l < r) {  // Standard Binary Search condition (stops when l == r)
            int m = (l + r + 1) / 2; // Compute middle value, avoids overflow

            // Check if `m` candies per child is feasible
            if(numChildren(candies, m) >= k)
                l = m;  // If possible, try a larger value of m
            else
                r = m - 1;  // If not possible, reduce the search space
        }

        // Return the maximum valid number of candies per child
        return l; // Since loop exits when l == r, return l directly
    }

    /**
     * Helper function to calculate how many children can receive `m` candies each.
     * It divides each pile of candies by `m` and sums up the number of children served.
     */
    private long numChildren(int[] candies, int m) {
        long count = 0; // Stores number of children that can be served
        for(int c : candies)
            count += c / m; // Count how many full groups of `m` can be made
        return count;
    }
}
```

#### Execution of above code:
```link
    https://leetcode.com/problems/maximum-candies-allocated-to-k-children/submissions/1573159660/?envType=daily-question&envId=2025-03-14
```

---


## 🔍 Complexity Analysis

| Approach      | Time Complexity          | Space Complexity |
|---------------|--------------------------|------------------|
| Binary Search | O(n log(sum(candies)/k)) | O(1)             |

---

## 🏅 Key Takeaways  

- **Optimized Using Binary Search:** The solution efficiently finds the maximum candies per child using **binary search on the answer**.  
- **Time Complexity:** **O(N log(sum(candies) / k))**, where `N` is the number of candy piles.  
- **Space Complexity:** **O(1)** since no extra space is used apart from variables.  
- **Avoids Integer Overflow:** Uses **`m = (l + r + 1) / 2`** to prevent overflow when calculating the middle value.  
- **Iterative & Efficient:** Uses a **while loop** for binary search and a simple loop for division, avoiding unnecessary stream operations.  
- **Handles Edge Cases:** Covers cases where `sum < k`, a single pile of candies, and very large `k` values.  
- **Improved Readability:** Uses a helper function `numChildren()` to keep the main logic clean and modular.

Write code that not only solves problems but stands the test of time — precision, performance, and clarity matter most. 🎯


