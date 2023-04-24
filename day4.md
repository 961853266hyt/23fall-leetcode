# Day4 错题()

### 24

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
    ListNode* swapPairs(ListNode* head) {
        if (head == nullptr || head -> next == nullptr) {
            return head;
        }
        ListNode* next = head -> next;
        ListNode* tmp = next -> next;
        next -> next = head;
        head -> next = swapPairs(tmp);
        return next; 
    }
};
```

### 19

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
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        ListNode* dummy = new ListNode(0, head);
        ListNode* slow = dummy;
        ListNode* fast = dummy;
        while(n--!=0) {
            fast = fast -> next;
        }
        while(fast -> next != nullptr) {
            fast = fast -> next;
            slow = slow -> next;
        }
        slow -> next = slow -> next -> next;
        return dummy -> next;
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
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
        set<ListNode*> s;
        if (headA == nullptr || headB == nullptr) {
            return nullptr;
        }
        while(headA != nullptr) {
            s.insert(headA);
            headA = headA -> next;
        }
        while(headB != nullptr) {
            if (s.count(headB)) {
                return headB;
            }
            headB = headB -> next;
        }
        return nullptr;
    }
};
```

### 142

```c++
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode *detectCycle(ListNode *head) {
        ListNode* slow = head;
        ListNode* fast = head;
        bool flag = false;
        while(fast!= nullptr && fast -> next != nullptr) {
            slow = slow -> next;
            fast = fast -> next -> next;
            if (fast == slow) {
                flag = true;
                break;
            } 
        }
        if (!flag) {
            return nullptr;
        }
        fast = head;
        while(fast!=slow) {
            fast = fast -> next;
            slow = slow -> next;
        }
        return fast;
    }
};
```



