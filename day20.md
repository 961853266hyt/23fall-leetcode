# Day20 错题(236 501)

### 530

```c++
/*time: O(n) space: O(height) */
class Solution {
public:
    int min_diff = INT_MAX;
    int pre_val = -1;
    int getMinimumDifference(TreeNode* root) {
        help(root);
        return min_diff;
    }

    void help(TreeNode* root) {
         if (!root) {
            return;
        }
        int val = root -> val;
        cout<<val<<endl;
        help(root -> left);
        if (pre_val == -1) 
        {
            pre_val = val;
        } 
        else 
        {
        min_diff = min(abs(pre_val - val), min_diff);
        }
        pre_val = val;
        help(root -> right); 
    }
};
```

### 501

```c++
/*time: O(n) space:O(height) */
class Solution {
public:
    TreeNode* mergeTrees(TreeNode* root1, TreeNode* root2) {
        TreeNode* root = new TreeNode();
        if (root1 && root2 ) {
            root -> val = root1 -> val + root2 -> val;
            root -> left = mergeTrees(root1 -> left, root2 -> left);
            root -> right = mergeTrees(root1 -> right, root2 -> right);
        }
        else if (root1) {
            root -> val = root1 -> val;
            root -> left = root1 -> left;
            root -> right = root1 -> right;
        }
        else if (root2) {
            root -> val = root2 -> val;
            root -> left = root2 -> left;
            root -> right = root2 -> right;
        }
        else {
            return nullptr;
        }
        return root;
    }
};
```

### 236

```c++
/*time: O(n) space:O(n) */
class Solution {
public:
    // 如果 ppp 和 qqq 都存在，则返回它们的公共祖先；
    // 如果只存在一个，则返回存在的一个；
    // 如果 ppp 和 qqq 都不存在，则返回 NULL
    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
        if (root == nullptr | root == p || root == q){
            return root;
        }
        auto left = lowestCommonAncestor(root -> left, p , q);
        auto right = lowestCommonAncestor(root -> right, p , q);
        if (left && right) {
            return root;
        }
        if (left) {
            return left;
        }
        return right;
    }
};
```

