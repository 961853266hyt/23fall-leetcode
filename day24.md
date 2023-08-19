# Day24 错题()

### 77

```c++
/*time: O(n) space: O(height) */
class Solution {
public:
    vector<vector<int>> ans;
    int k,n;
    vector<vector<int>> combine(int n, int k) {
        this-> k = k;
        this -> n = n;
        vector<int> path;
        backtrace(path,0, 1);
        return ans;
    }

    void backtrace(vector<int> path, int depth, int start) {
        if (depth == k) {
            ans.push_back(path);
            return;
        }
        if (path.size() + n - start + 1 < k){
            return;
        }
        for(int i = start; i <= n; i++) {
            path.push_back(i);
            backtrace(path, depth + 1, i + 1);
            path.pop_back();
        }
    }
};
```

