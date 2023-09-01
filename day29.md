# Day29 错题()

### 491

```c++
/*time: O(n) space: O(height) */
class Solution {
public:
    vector<vector<int>> ans;
    vector<int> nums;
    vector<vector<int>> findSubsequences(vector<int>& nums) {
        this -> nums = nums;
        vector<int> path;
        dfs(path, 0);
        return ans;
    }

    void dfs(vector<int> path, int start) {
        int len = path.size();
        if (len >= 2) {
            ans.push_back(path);
        }
        unordered_map<int, bool> used;
        for(int i = start; i < nums.size(); i++) {
            if(used[nums[i]]) {
                continue;
            }
            if (len == 0 || nums[i] >= path[len - 1]) {
                used[nums[i]] = true;
                path.push_back(nums[i]);
                dfs(path, i + 1);
                path.pop_back();
            }
        }
    }
}; 
```

### 46

```c++
/*time: O(n) space: O(height) */
class Solution {
public:
    vector<vector<int>> ans;
    vector<vector<int>> permute(vector<int>& nums) {
        vector<int> path;
        unordered_map<int, bool> used;
        dfs(path, nums, used);
        return ans;
    }

    void dfs(vector<int> path, vector<int>& nums, unordered_map<int, bool> used) {
        if (path.size() == nums.size()) {
            ans.push_back(path);
            return;
        }
        for(int i = 0; i < nums.size();i++) {
            if(!used[i]) {
                used[i] = true;
                path.push_back(nums[i]);
                dfs(path, nums,used);
                path.pop_back();
                used[i] = false;
            }
        }
    }
};
```

