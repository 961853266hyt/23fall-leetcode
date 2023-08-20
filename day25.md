# Day25 错题()

### 17

```c++
/*time: O(n) space: O(height) */
class Solution {
public:
    vector<string> mp;
    int len;
    vector<string> ans;
    vector<string> letterCombinations(string digits) {
        if (digits == "") {
            return ans;
        }
        len = digits.size();
        mp = {"abc","def","ghi","jkl","mno","pqrs","tuv","wxyz"};
        dfs("", 0, digits);
        return ans;

    }

    void dfs(string path, int start, string digits) {
        if (path.size() == len) {
            ans.push_back(path);
            return;
        }

        for(int i = start; i < len; i++) {
            for (char c: mp[digits[i] - '2']) {
                path.push_back(c);
                dfs(path, i + 1, digits);
                path.pop_back();
            }
        }
    }
};
```

### 216

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

