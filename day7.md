# Day6 错题(15)

### 454

```c++
/*time: O(n^2) space:O(n^2) */
class Solution {
public:
    int fourSumCount(vector<int>& nums1, vector<int>& nums2, vector<int>& nums3, vector<int>& nums4) {
        int sum = 0;
        int n = nums1.size();
        if (n == 1) {
            return (nums1[0] + nums2[0] + nums3[0] + nums4[0] == 0)?1:0;
        }
        map<int,int> mp;
        for(int i = 0; i < n; i++) {
            for (int j = 0; j < n;j++) {
                int s = nums1[i] + nums2[j];
                auto iter = mp.find(s);
                if (iter != mp.end()) {
                    mp[s] ++;
                }
                else {
                    mp[s] = 1;
                }
            }
        }

        for(int i = 0; i < n; i++) {
            for (int j = 0; j < n;j++) {
                int s = nums3[i] + nums4[j];
                auto iter = mp.find(-s);
                if (iter != mp.end()) {
                    sum += mp[-s];          
                }
                else {
                    continue;
                }
            }
        }
        return sum;
    }
};
```

### 383

```c++
/*time: O(n + m) space:O(1) */
class Solution {
public:
    bool canConstruct(string ransomNote, string magazine) {
        if (ransomNote.size() > magazine.size()) {
            return false;
        }
        vector<int> s(26,0);
        for(char c:magazine) {
            s[c - 'a']++ ;
        }
        for(char c:ransomNote) {
            if (--s[c - 'a'] < 0) {
                return false;
            }
        }
        return true;
    }
};
```

### 15

```c++
/*time: O(n^2) space:O(logn) */
class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& nums) {
        vector<vector<int>> ans;
        sort(nums.begin(),nums.end());
        int prev = nums[0] - 1;
        int len = nums.size();
        for(int i = 0; i < len - 2; i++){
            if (nums[i] == prev) {
                continue;
            }
            int j = i + 1, k = len - 1;
            while(j < k) {
                int sum = nums[i] + nums[j] + nums[k];
                if (sum > 0) {
                    k--;
                }
                else if (sum < 0) {
                    j++;            
                }
                else {
                    ans.push_back({nums[i],nums[j],nums[k]});
                    while(k > j && nums[j] == nums[j + 1]){
                        j++;
                    } 
                    j++;
                    while(k > j && nums[k] == nums[ k - 1]){
                        k--;
                    } 
                    k--;
                }
            }
            prev = nums[i];
        }
        return ans;
    }
};
```

### 18

```c++
/*time: O(n^3) space:O(logn) */
class Solution {
public:
    vector<vector<int>> fourSum(vector<int>& nums, int target) {
        sort(nums.begin(), nums.end());
        int len = nums.size();
        if (len < 4) {
            return {};
        }
        vector<vector<int>> ans;
        int prev = nums[0] - 1;
        for(int i = 0; i < len - 3; i++) {
            if (nums[i] == prev) {
                continue;
            }
            int prev2 = nums[i + 1] - 1;
            for (int j = i + 1; j < len - 2;j++) {
                if (nums[j] == prev2) {
                    continue;
                }
                int c = j + 1,d = len - 1;
                while(c < d){
                    int64_t sum = nums[c] + nums[d];
                    if (sum == target - (int64_t)(nums[i] + nums[j])) {
                        ans.push_back({nums[i],nums[j],nums[c],nums[d]});
                        c++;
                        while(c < d && nums[c] == nums[c - 1]){
                            c++;
                        }
                        d--;
                        while(c < d && nums[d] == nums[d + 1]){
                            d--;
                        }
                    }
                    else if (sum < target - (int64_t)(nums[i] + nums[j])) {
                        c++;
                    }
                    else if (sum > target - (int64_t)(nums[i] + nums[j])) {
                        d--;
                    }
                }
                prev2 = nums[j]; 
            }
            prev = nums[i];
        }
        return ans;
    }
};
```



