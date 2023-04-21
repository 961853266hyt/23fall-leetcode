# Day4 错题()

### 24

```c++
class Solution {
public:
    ListNode* removeElements(ListNode* head, int val) {
        if (head == nullptr) {
            return head;
        }
        if (head -> val != val) {
            head -> next = removeElements(head -> next, val);
        }
        else {
            return removeElements(head -> next, val);
        }
        return head;
    }
};
```

### 19

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

### 02.07

```c++
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* reverseList(ListNode* head) {
        if (head == nullptr || head -> next == nullptr) {
            return head;
        }
        ListNode* a = reverseList(head -> next);
        head -> next -> next = head;
        head -> next = nullptr;
        return a;
    }
};
```

### 142

```c++

```



