# Day33 错题(134，135)

### 1005

```c++
/*time: O(nlogn) space: O(n) */
class Solution {
public:
    int largestSumAfterKNegations(vector<int>& nums, int k) {
        int ans = 0;
        priority_queue<int, vector<int>, greater<int>> pq;
        for(int n:nums) {
            pq.push(n);
        }
        if (pq.top() > 0) {
            if (k % 2 == 1) {
                int tp = pq.top();
                pq.pop();
                pq.push(-tp);
            }
        }
        else {
            while(k--) {
            int tp = pq.top();
            pq.pop();
            pq.push(-tp);
            }
        }  
        while(!pq.empty()) {
            ans += pq.top();
            pq.pop();
        }
        return ans;
    }
};
```

### 134

```c++
/*time: O(n) space: O(1) */
class Solution {
public:
    int canCompleteCircuit(vector<int>& gas, vector<int>& cost) {
        int n = gas.size();
        vector<int> aux;
        int sum = 0;
        for(int i = 0; i < n; i++) {
            aux.push_back(gas[i] - cost[i]);
            sum += (gas[i] - cost[i]);
        }
        if (sum < 0) {
            return -1;
        }
        int i = 0;
        while(i < n) {
            if (aux[i] < 0){
                i++;
                continue;
            }
            int cnt = 0;
            int gas = 0;
            int start = i;
            while(cnt <= n && gas >= 0) {
                gas += aux[i];
                cnt++;
                i = (i + 1) % n;
            }
            if (cnt == (n + 1)) {
                return start;
            }
        }
        return -1;
    }
};
```

### 135

```c++
/*time: O(n) space: O(n) */
class Solution {
public:
    int candy(vector<int>& ratings) {
        int n = ratings.size();
        vector<int> candy(n,1);
        for(int i = 0; i < n - 1; i++) {
            if(ratings[i + 1] > ratings[i] && candy[i + 1] <= candy[i]) {
                candy[i + 1] = candy[i] + 1;
            }
        }
        for(int i = n - 1; i > 0; i--) {
            if(ratings[i - 1] > ratings[i] && candy[i - 1] <= candy[i]) {
                candy[i - 1] = candy[i] + 1;
            }
        }
        int ans = 0;
        for(int c:candy) {
            ans += c;
        }
        return ans;
    }
};
```

