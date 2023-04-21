# Day2 错题()

### 704 二分查找

```c++
class Solution {
public:
    vector<int> sortedSquares(vector<int>& nums) {
        int len = nums.size();
        vector<int> ans(len, 0);
        int l = 0,r = len -1,i = r;
        while(l <= r) {
            int a = nums[l] * nums[l];
            int b = nums[r] * nums[r];
            if ( a > b) {
                ans[i--] = a; 
                l++;
                
            }
            else {
                ans[i--] = b;
                r--;
            }
        }

        return ans;
    }
};
```

### 27 移除元素

```c++
class Solution {
public:
    int minSubArrayLen(int target, vector<int>& nums) {
        int ans = INT_MAX;
        int len = nums.size();
        if (len == 1) {
            return nums[0] >= target?1:0;
        }
        int l = 0, r = 0,win_sum = nums[0]; // [l,r]
        while(r <= len - 1) {
            while (l <= r && win_sum >= target) {
                ans = min(ans,r - l + 1);
                win_sum -= nums[l++];
            }
            while (win_sum < target) {                  // 比target小 则r右移
                if (++r > len - 1)
                    break;
                win_sum += nums[r];
            }
        }
        return ans == INT_MAX?0:ans;
    }
};
```

### 34

```c++
class Solution {
public:
    vector<vector<int>> generateMatrix(int n) {
        vector<vector<int>> ans(n,vector<int> (n,0));
        int lu,lp,ru,rp;
        draw(0,n,ans,1,n * n);
        if (n % 2 == 1) {
            ans[n/2][n/2] = n * n;
        }
        return ans;
    }

    void draw(int x,int n, vector<vector<int>> & ans,int cnt,int target) {
        vector<int> a = {x, x, x + n - 1, x + n - 1};
        vector<int> b = {x, x + n - 1, x + n - 1, x};
        for(int i = 0;i < 4;i++){
            if (i == 0) {
                for(int j = 0; j <= n - 2;j++) {
                    ans[a[i]][b[i] + j] = cnt++;
                }
            }
            if (i == 1) {
                for(int j = 0; j <= n - 2;j++) {
                    ans[a[i] + j][b[i]] = cnt++;
                }
            }
            if (i == 2) {
                for(int j = 0; j <= n - 2;j++) {
                    ans[a[i]][b[i] - j] = cnt++;
                }
            }
            if (i == 3) {
                for(int j = 0; j <= n - 2;j++) {
                    ans[a[i] - j][b[i]] = cnt++;
                }
            }
        }
        if (cnt >= target - 1) {
            return;
        } 
        draw(x + 1, n - 2,ans,cnt,target);
        return;
    }
};
```

### 

