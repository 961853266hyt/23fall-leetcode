# Day18 错题(513，106)

### 513

```c++
/*time: O(n) space: O(height) */
class Solution {
public:
    int mdepth = -1;
    int val = 0;
    void traverse(TreeNode* root, int depth){
        if (root -> left == nullptr && root -> right == nullptr) { //leaf
            if (depth > mdepth) {
                mdepth = depth;
                val = root -> val;
            }
            return;
        }
        if (root -> left) {
            traverse(root -> left, ++depth);
            depth--;
        }
        if (root -> right) {
            traverse(root -> right, ++depth);
            depth--;
        }
        return;
    }

    int findBottomLeftValue(TreeNode* root) {
        traverse(root,0);
        return val;
    }
};
```

### 112

```c++
/*time: O(n) space:O(height) */
class Solution {
public:
    bool ans = false;
    bool hasPathSum(TreeNode* root, int targetSum) {
        dfs(root, 0, targetSum);
        return ans;
    }

    void dfs(TreeNode* root, int sum, int targetSum) {
        if (!root) {
            return;
        }
        sum += root -> val;
        if (root -> left == nullptr && root -> right == nullptr){
            if (targetSum == sum) {
                ans = true;
                return;
            }
        }
        dfs(root -> left, sum, targetSum);
        dfs(root -> right, sum, targetSum);
    }
};
```

### 113

```c++
/*time: O(n) space:O(height) */
class Solution {
public:
    vector<vector<int>> ans;
    int ts;
    vector<vector<int>> pathSum(TreeNode* root, int targetSum) {
        if (root == nullptr) {
            return ans;
        }
        vector<int> path;
        ts = targetSum;
        dfs(root, 0, path);
        return ans;
    }
    void dfs(TreeNode* root, int sum, vector<int> path) {
        path.push_back(root -> val);
        if (root -> left == nullptr && root -> right == nullptr) {
            if ((sum + root -> val) == ts) {
                ans.push_back(path);
                return;
            }
        }
        if (root -> left) {
            dfs(root -> left, sum + root -> val, path);
        }
        if (root -> right) {
            dfs(root -> right, sum + root -> val, path);
        }
    }
};
```

### 106

```c++
/*time: O(n) space:O(height) */
class Solution {
public:
    vector<int> in;
    vector<int> post;
    TreeNode* buildTree(vector<int>& inorder, vector<int>& postorder) {
        int size = inorder.size();
        TreeNode* root = new TreeNode();
        if (size == 1) {
            root -> val = inorder[0];
            return root;
        }
        in = inorder;
        post = postorder;
        construct(root, 0, size-1, 0, size - 1);
        return root;
    }

    void construct(TreeNode* root, int l_in, int r_in, int l_post, int r_post) {
        if (root == nullptr) {
            return;
        }
        TreeNode* ltree = new TreeNode();
        TreeNode* rtree = new TreeNode();
        int rootval = post[r_post];
        root -> val = rootval;
        cout<<rootval<<endl;
        int index = 0;
        for(int i = l_in; i <= r_in; i++) {
            if (in[i] == rootval) {
                index = i;
                break;
            }
        }
        int lsize = index - l_in;
        int rsize = r_in - index;
        if (rsize == 0) { 
            rtree = nullptr;
        }
        if (lsize == 0) { 
            ltree = nullptr;
        }
        
        root -> left = ltree; 
        construct(ltree, l_in, index - 1,l_post, l_post + lsize - 1);
        root -> right = rtree; 
        construct(rtree, index + 1, r_in, l_post + lsize, r_post - 1);
        return;
    }
};
```

### 105

### 

```c++
/*time: O(n) space:O(height) */
class Solution {
public:
    vector<int> in;
    vector<int> pre;
    TreeNode* buildTree(vector<int>& preorder, vector<int>& inorder) {
        int size = inorder.size();
        TreeNode* root = new TreeNode();
        if (size == 1) {
            root -> val = inorder[0];
            return root;
        }
        in = inorder;
        pre = preorder;
        construct(root, 0, size-1, 0, size - 1);
        return root;
    }
    void construct(TreeNode* root, int l_in, int r_in, int l_pre, int r_pre) {
        if (root == nullptr) {
            return;
        }
        TreeNode* ltree = new TreeNode();
        TreeNode* rtree = new TreeNode();
        int rootval = pre[l_pre];
        root -> val = rootval;
        int index = 0;
        for(int i = l_in; i <= r_in; i++) {
            if (in[i] == rootval) {
                index = i;
                break;
            }
        }
        int lsize = index - l_in;
        int rsize = r_in - index;
        if (rsize == 0) { 
            rtree = nullptr;
        }
        if (lsize == 0) { 
            ltree = nullptr;
        }
        
        root -> left = ltree; 
        construct(ltree, l_in, index - 1,l_pre + 1, l_pre + lsize);
        root -> right = rtree; 
        construct(rtree, index + 1, r_in, l_pre + lsize + 1, r_pre);
        return;
    }
};
```





