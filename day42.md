# Day42 错题(416)

### 416

```c++
/*time: O(V*n) space: O(V) */
class Solution {
public:
    bool canPartition(vector<int>& nums) {
        int n = nums.size();
        int sum = 0;
        for (int a:nums) {
            sum += a;
        }
        int V = sum/2;
        if (sum % 2 != 0) {
            return false;
        }
        vector<int> dp(V + 1, 0);
        for (int i = 0; i <= n - 1; i++) {
            for (int j = V; j >= nums[i]; j--) {
                dp[j] = max(dp[j], dp[j - nums[i]] + nums[i]);
            }
        }
        if (dp[V] == V) {
            return true;
        }
        return false;
    }
};
```

