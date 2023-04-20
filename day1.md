# day1 错题(27)

### 704 二分查找

```c++
class Solution {
public:
    int search(vector<int>& nums, int target) {
        int len = nums.size();
        if (len == 0)
            return -1;
        int l = 0;
        int r = len - 1;
        while(l <= r) {
            int mid = (l + r)/2;
            if (nums[mid] == target){
                return mid;
            }
            else if(nums[mid] > target){
                r = mid - 1;
            }
            else {
                l = mid + 1;
            }
        }
        return -1;
    }
};
```

### 27 移除元素

```c++
class Solution {
public:
    int removeElement(vector<int>& nums, int val) {
        int len = nums.size();
        if (len == 0)
            return 0;
        int pr = 0; // 原数组待处理的元素下标
        int pl = 0; // 指向新数组的下一个元素
        while(pr < len){
            if (nums[pr] != val) {
                nums[pl] = nums[pr];
                pr++;
                pl++;
            }
            else {
                pr++;
            }
        }
        return pl;
    }
};
```

### 34

```c++
class Solution {
public:
    vector<int> searchRange(vector<int>& nums, int target) {
        vector<int> ans = {-1,-1};
        ans[0] = find_border(true, nums, target);
        ans[1] = find_border(false, nums, target);
        return ans;
    }

    int find_border(bool LeftOrNot, vector<int>& nums, int target) {
        int ans = -1;
        int l = 0, r = nums.size() - 1, mid = 0;
        while (l <= r) {
            mid = r + ((l - r) / 2);
            if (nums[mid] < target) {
                l = mid + 1;
            }
            else if (nums[mid] > target) {
                r = mid - 1;
            }
            else {
                ans = mid;
                if (LeftOrNot) {
                    r = mid - 1;
                }
                else {
                    l = mid + 1;
                }
            }
        }
        return ans;
    }
};
```

### 35

```c++
class Solution {
public:
    int searchInsert(vector<int>& nums, int target) {
        int len = nums.size();
        int l = 0;
        int r = len - 1;
        int ans = 0, mid;
        while (l <= r) {
            mid = (r + l)/2;
            if (nums[mid] == target)
                return mid;
            else if (nums[mid] < target) {
                l = mid + 1;
            }
            else {
                r = mid - 1;
            }
        }
        return l;
    }
};
```

