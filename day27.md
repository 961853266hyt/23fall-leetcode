# Day27 错题(40)

### 39

```c++
/*time: O(n) space: O(height) */
class Solution {
public:
    vector<vector<int>> ans;
    vector<int> candidates;
    int target;
    vector<vector<int>> combinationSum(vector<int>& candidates, int target) {
        vector<int> path;
        this -> candidates = candidates;
        this -> target = target;
        dfs(path, 0, 0);
        return ans;
    }

    void dfs(vector<int> path, int sum, int start) {
        if (sum == target) {
            ans.push_back(path);
            return;
        }
        if (sum > target) 
            return;
        for (int i = start; i < candidates.size(); i++) {
            path.push_back(candidates[i]);
            dfs(path, sum + candidates[i], i);
            path.pop_back();
        }
    }
};
```

### 40

```c++
/*time: O(n) space: O(height) */
class Solution {
public:
    vector<vector<int>> ans;
    int k,n;
    vector<vector<int>> combinationSum3(int k, int n) {
        vector<int> path;
        this -> k = k;
        this -> n = n;
        backtrace(path, 0, 1, 0);
        return ans;
    }

    void backtrace(vector<int> path, int depth, int start, int sum) {
        if (depth == k && sum == n) {
            ans.push_back(path);
            return;
        }
        for(int i = start; i <= 9; i++) {
            if (sum + i > n) {
                return;
            }
            path.push_back(i);
            backtrace(path, depth + 1, i + 1, sum + i);
            path.pop_back();
        }

    }
};
```

### 131

```c++
/*time: O(n) space: O(height) */
class Solution {
public:
    vector<vector<int>> ans;
    int k,n;
    vector<vector<int>> combinationSum3(int k, int n) {
        vector<int> path;
        this -> k = k;
        this -> n = n;
        backtrace(path, 0, 1, 0);
        return ans;
    }

    void backtrace(vector<int> path, int depth, int start, int sum) {
        if (depth == k && sum == n) {
            ans.push_back(path);
            return;
        }
        for(int i = start; i <= 9; i++) {
            if (sum + i > n) {
                return;
            }
            path.push_back(i);
            backtrace(path, depth + 1, i + 1, sum + i);
            path.pop_back();
        }

    }
};
```

