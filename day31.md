# Day31 错题(376, 53)

### 455

```c++
/*time: O(n) space: O(height) */
class Solution {
public:
    int findContentChildren(vector<int>& g, vector<int>& s) {
        if(s.size() == 0) {
            return 0;
        }
        int ans = 0;
        int i = 0;
        int j = 0;
        sort(g.begin(), g.end(), greater<int>());
        sort(s.begin(), s.end(), greater<int>());
        while(i < g.size() && j < s.size()) {
            if(s[j] >= g[i]) {
                ans++;
                j++;
                i++;
            }
            else {
                i++;
            }
        }
        return ans;
    }
};
```

### 376

```c++
/*time: O(n) space: O(height) */
class Solution {
public:
    int wiggleMaxLength(vector<int>& nums) {
        int res = 0;
        int reverse = 0; 
        for(int i = 1; i < nums.size(); i++){
            if(nums[i-1]<nums[i] && reverse != 1){
                res++;
                reverse = 1; // up
            }
            else if(nums[i-1]>nums[i] && reverse != 2){
                res++;
                reverse = 2; // down
            } 
        }
        return res + 1; 
    }
};
```

### 53

```c++
/*time: O(n) space: O(1) */
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int maxsum = INT_MIN;
        int cursum = 0;
        for(int i = 0; i < nums.size(); i++) {
            cursum += nums[i];
            if (cursum > maxsum) {
                maxsum = cursum;
            }
            if (cursum < 0) {
                cursum = 0;
            }
        }
        return maxsum;
    }
};
```

