# 🧠 LeetCode Problem: Count the Number of Complete Components

## 📌 Problem Statement

You are given an integer `n`. There is an undirected graph with `n` vertices, numbered from `0` to `n - 1`. You are given a 2D integer array `edges` where `edges[i] = [aᵢ, bᵢ]` denotes that there exists an undirected edge connecting vertices `aᵢ` and `bᵢ`.

Return the number of **complete connected components** of the graph.

A **connected component** is a subgraph of a graph in which there exists a path between any two vertices, and no vertex of the subgraph shares an edge with a vertex outside of the subgraph.

A **connected component** is said to be **complete** if there exists an edge between every pair of its vertices.

### Example 1:
![Example Diagram](../Attached&20Images/2685_Fig_1.jpg)
```plaintext
Input: n = 6, edges = [[0,1],[0,2],[1,2],[3,4]]
Output: 3
Explanation: From the picture above, one can see that all of the components of this graph are complete.
```

### Example 2:

![Example Diagram](../Attached&20Images/2685_Fig_2.jpg)
![Explaination Diagram](../Attached%20Images/2685_Fig_1.jpg)
```plaintext
Input: n = 6, edges = [[0,1],[0,2],[1,2],[3,4],[3,5]]
Output: 1
Explanation: The component containing vertices 0, 1, and 2 is complete since there is an edge between every pair of two vertices. On the other hand, the component containing vertices 3, 4, and 5 is not complete since there is no edge between vertices 4 and 5. Thus, the number of complete components in this graph is 1.
```

### Constraints:
- `1 <= n <= 50`
- `0 <= edges.length <= n * (n - 1) / 2`
- `edges[i].length == 2`
- `0 <= aᵢ, bᵢ <= n - 1`
- `aᵢ != bᵢ`
- There are no repeated edges.

---

## 💡 Approach 1: Brute Force (DFS + Checking Edges) (Time Complexity: `O(n^3)`, Space Complexity: `O(n^2)`)  

### 🔧 C++ Solution
```cpp
class Solution {
public:
    int countCompleteComponents(int n, vector<vector<int>>& edges) {
        vector<vector<int>> adj(n);
        for(auto& edge : edges) {
            adj[edge[0]].push_back(edge[1]);
            adj[edge[1]].push_back(edge[0]);
        }
        
        vector<bool> visited(n, false);
        int count = 0;
        
        function<bool(int, unordered_set<int>&)> dfs = [&](int node, unordered_set<int>& nodes) {
            visited[node] = true;
            nodes.insert(node);
            bool complete = true;
            for(int neighbor : adj[node]) {
                if(!visited[neighbor]) {
                    complete &= dfs(neighbor, nodes);
                }
            }
            return complete;
        };
        
        for(int i = 0; i < n; i++) {
            if(!visited[i]) {
                unordered_set<int> nodes;
                if(dfs(i, nodes)) {
                    bool isComplete = true;
                    for(int node : nodes) {
                        if(adj[node].size() != nodes.size() - 1) {
                            isComplete = false;
                            break;
                        }
                    }
                    if(isComplete) count++;
                }
            }
        }
        return count;
    }
};
```

### Execution of above code:
```link
  https://leetcode.com/problems/count-the-number-of-complete-components/submissions/1589798925/?envType=problem-list-v2&envId=2uzxgkqe
```

### 🔧 Java Solution
```java
class Solution {
    public int countCompleteComponents(int n, int[][] edges) {
        List<Integer>[] adj = new ArrayList[n];
        for(int i = 0; i < n; i++) adj[i] = new ArrayList<>();
        
        for(int[] edge : edges) {
            adj[edge[0]].add(edge[1]);
            adj[edge[1]].add(edge[0]);
        }
        
        boolean[] visited = new boolean[n];
        int count = 0;
        
        for(int i = 0; i < n; i++) {
            if(!visited[i]) {
                Set<Integer> nodes = new HashSet<>();
                if(dfs(i, adj, visited, nodes)) {
                    boolean isComplete = true;
                    for(int node : nodes) {
                        if(adj[node].size() != nodes.size() - 1) {
                            isComplete = false;
                            break;
                        }
                    }
                    if(isComplete) count++;
                }
            }
        }
        return count;
    }
    
    private boolean dfs(int node, List<Integer>[] adj, boolean[] visited, Set<Integer> nodes) {
        visited[node] = true;
        nodes.add(node);
        boolean complete = true;
        for(int neighbor : adj[node]) {
            if(!visited[neighbor]) {
                complete &= dfs(neighbor, adj, visited, nodes);
            }
        }
        return complete;
    }
}
```

### Execution of above code:
```link
  https://leetcode.com/problems/count-the-number-of-complete-components/submissions/1589800658/?envType=problem-list-v2&envId=2uzxgkqe
```

---

## 💡 Approach 2: Union-Find (Optimized) (Time Complexity: `O(n^2)`, Space Complexity: `O(n)`)  

- Uses Union-Find to efficiently group connected components.
- Then, checks if each group forms a complete component.
- **Key Insight:** A component with `k` nodes should have exactly `k*(k-1)/2` edges.

### 🔧 C++ Solution (Union-Find)
```cpp
class Solution {
public:
    int countCompleteComponents(int n, vector<vector<int>>& edges) {
        vector<int> parent(n), size(n, 1), edgeCount(n, 0);
        iota(parent.begin(), parent.end(), 0);

        function<int(int)> find = [&](int x) {
            return parent[x] == x ? x : parent[x] = find(parent[x]);
        };

        for(auto& e : edges) {
            int u = find(e[0]), v = find(e[1]);
            if(u != v) {
                parent[v] = u;
                size[u] += size[v];
                edgeCount[u] += edgeCount[v];
            }
            edgeCount[u]++;
        }

        int count = 0;
        for(int i = 0; i < n; i++) {
            if(parent[i] == i && size[i] * (size[i] - 1) / 2 == edgeCount[i]) 
                count++;
        }
        return count;
    }
};
```

### Execution of above code:
```link
  https://leetcode.com/problems/count-the-number-of-complete-components/submissions/1589801590/?envType=problem-list-v2&envId=2uzxgkqe
```

### 🔧 Java Solution
```java
import java.util.*;

class Solution {
    public int countCompleteComponents(int n, int[][] edges) {
        int[] parent = new int[n];
        int[] size = new int[n];
        int[] edgeCount = new int[n];
        
        for(int i = 0; i < n; i++) {
            parent[i] = i;
            size[i] = 1;
        }
        
        for(int[] edge : edges) {
            int u = find(edge[0], parent);
            int v = find(edge[1], parent);
            if(u != v) {
                parent[v] = u;
                size[u] += size[v];
                edgeCount[u] += edgeCount[v];
            }
            edgeCount[u]++;
        }

        int count = 0;
        for(int i = 0; i < n; i++) {
            if(parent[i] == i && size[i] * (size[i] - 1) / 2 == edgeCount[i]) {
                count++;
            }
        }
        return count;
    }

    private int find(int x, int[] parent) {
        if(parent[x] != x) {
            parent[x] = find(parent[x], parent);
        }
        return parent[x];
    }
}
```

### Execution of above code:
```link
  https://leetcode.com/problems/count-the-number-of-complete-components/submissions/1589802350/?envType=problem-list-v2&envId=2uzxgkqe
```
---

## 🔍 Complexity Analysis

| Approach      | Time Complexity | Space Complexity |
|--------------|----------------|-----------------|
| Brute Force  | `O(n^3)`       | `O(n^2)`       |
| Union-Find   | `O(n^2)`       | `O(n)`         |

---

## 🏅 Key Takeaways  
- **Brute Force:** Uses DFS to find components and check completeness.
- **Union-Find:** Efficiently groups and validates complete components.
- **Optimized Approach:** Reduces time complexity significantly using mathematical properties of complete graphs.
Write code that not only solves problems but stands the test of time — precision, performance, and clarity matter most. 🎯
