# Day14 错题()

### 144

```c++
/*time: O(n) space: average O(logn) worst: O(n) */
class Solution {
public:
    vector<int> preorderTraversal(TreeNode* root) {
        stack<TreeNode*> stk;
        if (root == nullptr) {
            return {};
        }
        vector<int> ans;
        stk.push(root);
        while(!stk.empty()) {
            auto node = stk.top();
            stk.pop();
            ans.push_back(node -> val);
            if (node -> right) stk.push(node -> right);
            if (node -> left) stk.push(node -> left);
        }
        return ans;
    }
};
```

### 94

```c++
/*time: O(n) space:O(n) */
class Solution {
public:
    vector<int> inorderTraversal(TreeNode* root) {
        vector <int> a;
        if (root == nullptr) {
            return {};
        }
        vector<int> b;
        if (root -> left) 
            a = inorderTraversal(root -> left);
        a.push_back(root -> val);
        if (root -> right)  
            b = inorderTraversal(root -> right);
        a.insert(a.end(),b.begin(),b.end());
        return a;
    }
};
```

### 145

```c++
/*time: O(n) space:O(n) */
class Solution {
public:
    vector<int> postorderTraversal(TreeNode* root) {
        vector<int> ans;
        Traver(ans,root);
        return ans;
    }

    void Traver(vector<int> & ans, TreeNode* root) 
    {
        if(!root) return;
        if (root ->left) Traver(ans, root -> left);
        if (root ->right) Traver(ans, root -> right);
        ans.push_back(root->val);
        return;
    }
};
```





