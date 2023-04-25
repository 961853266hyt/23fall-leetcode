# Day6 错题()

### 242

```c++
class Solution {
public:
    bool isAnagram(string s, string t) {
        if (s.length() != t.length()) {
            return false;
        }
        sort(s.begin(),s.end());
        sort(t.begin(),t.end());
        return s == t;
    }
};
```

### 349

```c++
class Solution {
public:
    vector<int> intersection(vector<int>& nums1, vector<int>& nums2) {
        vector<int> ans;
        set<int> s;
        for(int a:nums1) {
            s.insert(a);
        }
        for(int a:nums2){
            if(s.count(a)) {
                ans.push_back(a);
                s.erase(a);
            }
        }
        return ans;
    }
};
```

### 202

```c++
class Solution {
public:
    bool isHappy(int n) {
        int slow = cal(n),fast = cal(cal(n));
         do
         {
            if (fast == 1) 
            {
                return true;
            }
            slow = cal(slow);
            fast = cal(cal(fast));
        }while(slow != fast);
        return false;
    }

    int cal(int n) {
        int sum = 0;
        while (n > 0) {
            sum += pow((n % 10),2);
            n /= 10;
        }
        return sum;
    }
};
```

### 1

```c++
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        int len = nums.size();
        map<int,int> mp;
        for(int i = 0; i < len; i++) {
            auto iter = mp.find(target - nums[i]);
            if (iter != mp.end()) {
                return {i,iter -> second};
            }
            mp[nums[i]] = i;
        }
        return {0,0};
    }
};
```



