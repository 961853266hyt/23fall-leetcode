# Day20 错题()

### 654

```c++
/*time: O(n) space: O(height) */
class Solution {
public:
    vector<int> nums;
    TreeNode* constructMaximumBinaryTree(vector<int>& nums) {
        this -> nums = nums;
        return help(0, nums.size());
    }

    TreeNode* help(int i, int j) { // [i,j)
        if (j <= i) {
            return nullptr;
        }
        TreeNode* root = new TreeNode();
        int m_index = i;
        int max_val = nums[i];
        for(int k = i ; k < j;k++) {
            if (max_val < nums[k]) {
                m_index = k;
                max_val = nums[k];
            }
        }
        root -> val = max_val;
        root -> left = help(i, m_index);
        root -> right = help(m_index+1, j);
        return root;
    }
};
```

### 617

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

### 700

```c++
/*time: O(n) space:O(height) */
class Solution {
public:
    TreeNode* searchBST(TreeNode* root, int val) {
        if (root -> val == val) {
            return root;
        }
        if (root -> val < val) {
            if (root -> right == nullptr) 
                return nullptr;
            return searchBST(root -> right, val);
        }
        if (root -> val > val) {
            if (root -> left == nullptr) 
                return nullptr;
            return searchBST(root -> left, val);
        }
        return nullptr;
    }
};
```

### 98

```c++
/*time: O(n) space:O(height) */
class Solution {
public:
    long long max_val = LONG_MIN;
    bool isValidBST(TreeNode* root) {
        if (!root)
            return true; 
        bool left_ans = isValidBST(root -> left);
        if (root -> val > max_val) {
            max_val = root -> val;
        }
        else {
            return false;
        }
        bool right_ans = isValidBST(root -> right);
        return left_ans && right_ans;
    } 
};
```

