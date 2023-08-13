# Day17 错题()

### 104

```c++
/*time: O(n) space: O(height) */
class Solution {
public:
    bool isBalanced(TreeNode* root) {
        if (root == nullptr) {
            return true;
        }
        if (abs(geth(root -> left) - geth(root -> right)) <= 1) {
            return isBalanced(root -> left) && isBalanced(root -> right);
        }
        return false;
    }

    int geth(TreeNode* root) {
        if(root == nullptr) {
            return 0;
        }
        return max(geth(root -> left), geth(root -> right)) + 1;
    }
};
```

### 257

```c++
/*time: O(n) space:O(height) */
class Solution {
public:
    vector<string> binaryTreePaths(TreeNode* root) {
        vector<string> ans;
        string path = to_string(root->val);
        if (root->left == nullptr && root -> right == nullptr) {
            ans.push_back(path);
            return ans;
        }
        dfs(root->left, ans, path);
        dfs(root->right, ans, path);
        return ans;
    }

    void dfs(TreeNode* rt, vector<string>& ans, string path) {
        if (rt == nullptr){
            return;
        }
        path += ("->"+to_string(rt->val));
        if (rt->left == nullptr && rt->right == nullptr) {
            ans.push_back(path);
            return;
        }
        if (rt->left != nullptr) {
            dfs(rt->left, ans, path);
        }
        if (rt->right != nullptr) {
            dfs(rt->right, ans, path);
        }
        return;
    }
};
```

### 404

```c++
/*time: O(n) space:O(height) */
class Solution {
public:
    int sum = 0;
    int sumOfLeftLeaves(TreeNode* root) {
        if (root == nullptr) {
            return 0;
        }
        if (root -> left != nullptr && root -> left -> left == nullptr && root -> left -> right == nullptr) {
            sum += root ->left-> val;
        }
        if (root -> left != nullptr) {
            sumOfLeftLeaves(root -> left);
        }
        sumOfLeftLeaves(root -> right);
        return sum;
    }
};
```

### 

