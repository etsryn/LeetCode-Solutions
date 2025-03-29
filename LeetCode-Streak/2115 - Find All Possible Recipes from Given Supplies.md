# 🧠 LeetCode Problem: Find All Possible Recipes from Given Supplies

## 📌 Problem Statement

You have information about `n` different recipes. You are given a string array `recipes` and a 2D string array `ingredients`. The `i-th` recipe has the name `recipes[i]`, and you can create it if you have all the needed ingredients from `ingredients[i]`. A recipe can also be an ingredient for other recipes, i.e., `ingredients[i]` may contain a string that is in `recipes`.

You are also given a string array `supplies` containing all the ingredients that you initially have, and you have an infinite supply of all of them.

Return a list of all the recipes that you can create. You may return the answer in **any order**.

Note that two recipes may contain each other in their ingredients.

### Example 1:

```plaintext
Input: recipes = ["bread"], ingredients = [["yeast","flour"]], supplies = ["yeast","flour","corn"]
Output: ["bread"]
```

### Example 2:

```plaintext
Input: recipes = ["bread","sandwich"], ingredients = [["yeast","flour"],["bread","meat"]], supplies = ["yeast","flour","meat"]
Output: ["bread","sandwich"]
```

### Example 3:

```plaintext
Input: recipes = ["bread","sandwich","burger"], ingredients = [["yeast","flour"],["bread","meat"],["sandwich","meat","bread"]], supplies = ["yeast","flour","meat"]
Output: ["bread","sandwich","burger"]
```

### Constraints
- `n == recipes.length == ingredients.length`  
- `1 <= n <= 100`  
- `1 <= ingredients[i].length, supplies.length <= 100`  
- `1 <= recipes[i].length, ingredients[i][j].length, supplies[k].length <= 10`  
- `recipes[i], ingredients[i][j], and supplies[k]` consist only of lowercase English letters.  
- All the values of `recipes` and `supplies` combined are **unique**.  
- Each `ingredients[i]` does not contain any duplicate values.  

---

## 💡 Approach 1: Brute Force (Time Complexity: `O(n^2 * m)`, where `m` is the average ingredient list size)

### 🔧 C++ Solution
```cpp
class Solution {
public:
    vector<string> findAllRecipes(vector<string>& recipes, vector<vector<string>>& ingredients, vector<string>& supplies) {
        unordered_set<string> available(supplies.begin(), supplies.end());
        vector<string> result;
        bool progress = true;
        
        while(progress) {
            progress = false;
            for(int i = 0; i < recipes.size(); ++i) {
                if(available.count(recipes[i])) continue;
                bool canMake = true;
                for(string& ing : ingredients[i]) {
                    if(!available.count(ing)) {
                        canMake = false;
                        break;
                    }
                }
                if(canMake) {
                    available.insert(recipes[i]);
                    result.push_back(recipes[i]);
                    progress = true;
                }
            }
        }
        return result;
    }
};
```

### Execution of above code:
```link
  https://leetcode.com/problems/find-all-possible-recipes-from-given-supplies/submissions/1589781565/?envType=problem-list-v2&envId=2uzxgkqe
```

### 🔧 Java Solution
```java
import java.util.*;

class Solution {
    public List<String> findAllRecipes(String[] recipes, List<List<String>> ingredients, String[] supplies) {
        Set<String> available = new HashSet<>(Arrays.asList(supplies));
        List<String> result = new ArrayList<>();
        boolean progress = true;

        while(progress) {
            progress = false;
            for(int i = 0; i < recipes.length; i++) {
                if(available.contains(recipes[i])) continue;
                boolean canMake = true;
                for(String ing : ingredients.get(i)) {
                    if (!available.contains(ing)) {
                        canMake = false;
                        break;
                    }
                }
                if(canMake) {
                    available.add(recipes[i]);
                    result.add(recipes[i]);
                    progress = true;
                }
            }
        }
        return result;
    }
}
```

### Execution of above code:
```link
  https://leetcode.com/problems/find-all-possible-recipes-from-given-supplies/submissions/1589783127/?envType=problem-list-v2&envId=2uzxgkqe
```

---

## 💡 Approach 2: Topological Sorting (Time Complexity: `O(n * m)`, Space Complexity: `O(n + m)`)

### 🔧 C++ Solution
```cpp
class Solution {
public:
    vector<string> findAllRecipes(vector<string>& recipes, vector<vector<string>>& ingredients, vector<string>& supplies) {
        unordered_map<string, int> indegree;
        unordered_map<string, vector<string>> graph;
        unordered_set<string> available(supplies.begin(), supplies.end());
        queue<string> q;
        vector<string> result;
        
        for(int i = 0; i < recipes.size(); i++) {
            indegree[recipes[i]] = ingredients[i].size();
            for(string& ing : ingredients[i]) {
                graph[ing].push_back(recipes[i]);
            }
        }
        
        for(string& sup : supplies) q.push(sup);
        
        while(!q.empty()) {
            string cur = q.front(); q.pop();
            for(string& next : graph[cur]) {
                if(--indegree[next] == 0) {
                    q.push(next);
                    result.push_back(next);
                }
            }
        }
        return result;
    }
};
```

### Execution of above code:
```link
  https://leetcode.com/problems/find-all-possible-recipes-from-given-supplies/submissions/1589783999/?envType=problem-list-v2&envId=2uzxgkqe
```

### 🔧 Java Solution
```java
class Solution {
    public List<String> findAllRecipes(String[] recipes, List<List<String>> ingredients, String[] supplies) {
        Map<String, Integer> indegree = new HashMap<>();
        Map<String, List<String>> graph = new HashMap<>();
        Set<String> available = new HashSet<>(Arrays.asList(supplies));
        Queue<String> q = new LinkedList<>();
        List<String> result = new ArrayList<>();

        for(int i = 0; i < recipes.length; i++) {
            indegree.put(recipes[i], ingredients.get(i).size());
            for(String ing : ingredients.get(i)) {
                graph.computeIfAbsent(ing, k -> new ArrayList<>()).add(recipes[i]);
            }
        }
        
        q.addAll(available);
        while(!q.isEmpty()) {
            String cur = q.poll();
            for(String next : graph.getOrDefault(cur, new ArrayList<>())) {
                if(indegree.merge(next, -1, Integer::sum) == 0) {
                    q.offer(next);
                    result.add(next);
                }
            }
        }
        return result;
    }
}
```

### Execution of above code:
```link
  https://leetcode.com/problems/find-all-possible-recipes-from-given-supplies/submissions/1589784778/?envType=problem-list-v2&envId=2uzxgkqe
```

---

## 📊 Complexity Analysis

| Approach | Time Complexity | Space Complexity |
|----------|----------------|------------------|
| Brute Force | `O(n^2 * m)` | `O(n + m)` |
| Topological Sorting | `O(n * m)` | `O(n + m)` |

---

## 🏅 Key Takeaways
- **Brute Force:** Inefficient for large cases.
- **Topological Sorting:** Efficient `O(n*m)` complexity using dependency tracking.
- **Real-World Use:** Helps in recipe planning, dependency resolution, and scheduling.

Write code that not only solves problems but stands the test of time — precision, performance, and clarity matter most. 🎯
