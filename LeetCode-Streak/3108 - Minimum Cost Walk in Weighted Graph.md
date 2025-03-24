# Not Completed Yet
# 🔥 LeetCode Problem: Minimum Cost Walk in Weighted Graph

## 🎯 Problem Statement

There is an **undirected weighted graph** with `n` vertices labeled from `0` to `n - 1`.

You are given:
- An integer `n` representing the number of vertices.
- An array `edges`, where `edges[i] = [uᵢ, vᵢ, wᵢ]` indicates an edge between vertices `uᵢ` and `vᵢ` with weight `wᵢ`.
- A 2D array `query`, where `query[i] = [sᵢ, tᵢ]` represents a query to find the **minimum cost walk** from `sᵢ` to `tᵢ`.

A **walk** on a graph is a sequence of vertices and edges. It starts and ends with a vertex, and each edge connects the vertex before it and the vertex after it. A walk can revisit the same edge or vertex multiple times.

The **cost** of a walk starting at node `u` and ending at node `v` is defined as the **bitwise AND** of all the edge weights in the walk:

$$
\text{cost} = w_0 \land w_1 \land w_2 \land \dots \land w_k
$$

where `∧` denotes the bitwise `AND` operator.

Return an array `answer`, where `answer[i]` denotes the **minimum** cost of the walk for `query[i]`. If no such walk exists, return `-1`.

---

## 💡 Example Test Cases

### Example 1:
```plaintext
Input: n = 5, edges = [[0,1,7],[1,3,7],[1,2,1]], query = [[0,3],[3,4]]
Output: [1,-1]
```
**Explanation:** <br />
![Explaination Diagram](../Attached%20Images/3108_Fig_1.jpg)

To achieve the cost of 1 in the first query, we need to move on the following edges: `0->1` (weight 7), `1->2` (weight 1), `2->1` (weight 1), `1->3` (weight 7).
In the second query, there is no walk between nodes 3 and 4, so the answer is -1.
### Example 2:
```plaintext
Input: n = 3, edges = [[0,2,7],[0,1,15],[1,2,6],[1,2,1]], query = [[1,2]]
Output: [0]
```
**Explanation:**
![Explaination Diagram](../Attached%20Images/3108_Fig_2.jpg)
To achieve the cost of 0 in the first query, we need to move on the following edges: `1->2` (weight 1), `2->1` (weight 6), `1->2` (weight 1).

---

## 🔍 Constraints
- `2 <= n <= 10^5`
- `0 <= edges.length <= 10^5`
- `edges[i].length == 3`
- `0 <= uᵢ, vᵢ <= n - 1`
- `uᵢ != vᵢ`
- `0 <= wᵢ <= 10^5`
- `1 <= query.length <= 10^5`
- `query[i].length == 2`
- `0 <= sᵢ, tᵢ <= n - 1`
- `sᵢ != tᵢ`

---

## 💡 Approach 1: Brute Force BFS (Time Complexity: $O(n^3)$)

### 🔧 C++ Solution
```cpp
```

#### Execution link:
```link
https://leetcode.com/problems/minimum-cost-walk-in-weighted-graph/submissions/XXXXX
```

---

## 💡 Approach 2: Optimized BFS with Bitwise Mask Pruning (Time Complexity: $O(n \times m)$)

### 🔧 C++ Solution
```cpp
```

#### Execution link:
```link
https://leetcode.com/problems/minimum-cost-walk-in-weighted-graph/submissions/XXXXX
```

---

## 🔍 Complexity Analysis

| Approach                        | Time Complexity | Space Complexity | Notes                       |
|---------------------------------|-----------------|------------------|----------------------------|
| Brute Force BFS                 | $O(n^3)$        | $O(n^2)$         | Inefficient for large graphs |
| Optimized BFS with Bitwise Mask | $O(n \times m)$ | $O(n + m)$       | Handles large graphs efficiently |

---

## 🎯 Key Takeaways

- **Brute Force BFS:** Tries all paths but slow for large graphs. 🚫  
- **Optimized BFS:** Uses bitwise mask pruning to minimize unnecessary paths. 🚀  
- **Memory Efficient:** Only tracks the best cost per node. 📌  

Write code that not only solves problems but stands the test of time — precision, performance, and clarity matter most. 🎯
