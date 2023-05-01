# Day13 错题(347, 239)

### 239

```c++
/*time: O(n) space:O(k) */
class Solution {
public:
    vector<int> maxSlidingWindow(vector<int>& nums, int k) {
        int len = nums.size();
        vector<int> ans;
        deque<int> dq;  // store index
        for(int i = 0; i < k; i++) {
            while(!dq.empty() && nums[i] >= nums[dq.back()]) {
                dq.pop_back();
            }
            dq.push_back(i);
        }
        ans.push_back(nums[dq.front()]);
        for(int i = 1;i < len - k + 1; i++) {
            int new_index = i + k - 1;
            if(!dq.empty() && dq.front() < i) {
                dq.pop_front();
            }
            while(!dq.empty() && nums[new_index] >= nums[dq.back()]) {
                dq.pop_back();
            }
            dq.push_back(new_index);
            ans.push_back(nums[dq.front()]);
        }
        return ans;
    }
};
```

### 347

```c++
/*time: O(nlogk) space:O(N) */
class Solution {
public:
    struct cmp {
        bool operator() (pair<int, int>& a, pair<int, int>& b) {
            return a.second > b.second;
        }
    };

    vector<int> topKFrequent(vector<int>& nums, int k) {
        priority_queue<pair<int, int>, vector<pair<int, int>>, cmp> pq;
        unordered_map<int,int> mp;
        for(int n:nums) 
        {
            mp[n]++; 
        }
        vector<int> ans;
        for(auto a:mp) {
            pq.push(a);
            if (pq.size() > k) {
                pq.pop();
            }
        }
        while(!pq.empty()) {
            ans.push_back(pq.top().first);
            pq.pop();
        }
        return ans;
    }
};
```



Deque:  3 2 1

Ans: 3 3

