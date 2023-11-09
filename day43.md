# Day43 错题(1049, 494)

### 1049

```c++
/*time: O(V*n) space: O(V) */
class Solution {
public:
    int lastStoneWeightII(vector<int>& stones) {
        int sum = 0;
        for (int a:stones) {
            sum += a;
        }
        int V = sum/2;
        int n = stones.size();
        vector<int> dp(V + 1, 0);
        for (int i = 0; i < n; i++) {
            for (int j = V; j >= stones[i]; j--) {
                dp[j] = max(dp[j], dp[j - stones[i]] + stones[i]);
            }
        }
        return sum - 2 * dp[V];
    }
};
```

### 494

```c++
/*time: O(V*n) space: O(V) */
class Solution {
public:
    int findTargetSumWays(vector<int>& nums, int target) {
        int n = nums.size();
        int s = 0;
        for (int i = 0; i < n; i++) {
            s += nums[i];
        }
        int pos = (s + target)/2;
        int neg = (s - target)/2;
        if (target > s || pos < 0) return 0;
        if ((s + target) % 2 != 0) return 0;
        vector<int> dp(pos + 1, 0);
        dp[0] = 1;
        for (int i = 0; i < n; i++) {
            for (int j = pos; j >= nums[i]; j--) {
                dp[j] += dp[j - nums[i]];
            }
        }
        return dp[pos];
    }
};
```

### 474

```c++
/*time: O(V*n) space: O(V) */
class Solution {s
public:
    int lastStoneWeightII(vector<int>& stones) {
        int sum = 0;
        for (int a:stones) {
            sum += a;
        }
        int V = sum/2;
        int n = stones.size();
        vector<int> dp(V + 1, 0);
        for (int i = 0; i < n; i++) {
            for (int j = V; j >= stones[i]; j--) {
                dp[j] = max(dp[j], dp[j - stones[i]] + stones[i]);
            }
        }
        return sum - 2 * dp[V];
    }
};
```

