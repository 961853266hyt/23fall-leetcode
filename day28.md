# Day28 错题(93, 78)

### 93

```c++
/*time: O(n) space: O(height) */
class Solution {
public:
    vector<string> ans;
    string ss;
    int count = 0;
    vector<string> restoreIpAddresses(string s) {
        if (s.size() < 4||s.size() > 12) {
            return ans;
        }
        ss = s;
        dfs("",0);
        return ans;
    }

    void dfs(string ip, int start) {
        if (start == ss.size() && count == 4) {
            ans.push_back(ip.substr(0, ip.size() - 1)); //remove last dot
            return;
        }
        for (int i = start; i <= start + 2 && i <= ss.size() - 1; i++){
            string num = ss.substr(start, i - start + 1);
            if (judge(num)) {
                string temp = ip;
                ip += (num + ".");
                count++;
                dfs(ip, i + 1);
                count--;
                ip = temp;
            }  
        }
    }

    bool judge(string s) {
        int l = s.size();
        if (l == 1 || l == 2 && s[0] != '0' || l == 3 && stoi(s) <= 255 && s[0] != '0') {
            return true;
        }
        return false;
    }
};
```

### 78

```c++
/*time: O(n) space: O(height) */
class Solution {
public:
    vector<vector<int>> ans;
    vector<int> nums;
    vector<vector<int>> subsets(vector<int>& nums) {
        this -> nums = nums;
        vector<int> a;
        dfs(a,0);
        return ans;
    }

    void dfs(vector<int> subset, int start) {
        ans.push_back(subset);
        if (start == nums.size()) {
            return;
        }
        for(int i = start; i < nums.size();i++) {
            subset.push_back(nums[i]);
            dfs(subset, i + 1);
            subset.pop_back();
        }
    }
};
```

### 90

```c++
/*time: O(n) space: O(height) */
class Solution {
public:
    vector<vector<int>> ans;
    vector<int> nums;
    vector<vector<int>> subsetsWithDup(vector<int>& nums) {
        vector<int> subset;
        sort(nums.begin(), nums.end());
        this -> nums = nums;
        dfs(subset, 0);
        return ans;
    }

    void dfs(vector<int> subset, int start){
         ans.push_back(subset);
        if (start == nums.size()){
            return;
        }
        unordered_map<int,bool> used;
        for(int i = start; i < nums.size(); i++) {
            if (!used[nums[i]]) {
                used[nums[i]] = true;
                subset.push_back(nums[i]);
                dfs(subset, i + 1);
                subset.pop_back();
            }
        }
    }
};
```

