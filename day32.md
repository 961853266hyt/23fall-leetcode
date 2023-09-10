# Day32 错题(122)

### 122

```c++
/*time: O(n) space: O(1) */
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        if (prices.size() == 1) {
            return 0;
        }
        vector<int> aux;
        for(int i = 0; i < prices.size() - 1; i++) {
            aux.push_back(prices[i + 1] - prices[i]);
        }
        int count = 0;
        for(int i = 0; i < aux.size(); i++) {
            count += aux[i] > 0 ? aux[i] : 0;
            
        }
        return count;
    }
};
```

### 55

```c++
/*time: O(n) space: O(1) */
class Solution {
public:
    bool canJump(vector<int>& nums) { 
        int Cover = 0;
        int a = nums.size() - 1;
        if(nums.size() == 1) return true;
        for(int i = 0; i <= Cover; i++) {
            Cover = max(nums[i] + i, Cover);
            if (Cover >= nums.size() - 1) return true;
        }
        return false;
    }
};
```

### 45

```c++
/*time: O(n) space: O(1) */
class Solution {
public:
    int jump(vector<int>& nums) {
        int ans = 0;
        int start = 0;
        int end = 1;
        while(end < nums.size()) {
            int maxPos = 0;
            for(int i = start; i < end; i++) {
                maxPos = max(maxPos, i + nums[i]);
            }
            start = end;
            end = maxPos + 1;
            ans++;
        }
        return ans;
    }
};
```

