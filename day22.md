# Day22 错题()

### 235

```c++
/*time: O(n) space: O(height) */
class Solution {
public:
    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
        if(!root || root == p | root == q) {
            return root;
        }
        if (root->val > p->val && root->val > q->val) { //left
            auto l = lowestCommonAncestor(root->left, p, q);
            return l;
        }
        else if (root->val < q->val && root->val < p->val){
            auto r = lowestCommonAncestor(root->right, p, q);
            return r;
            
        }
        else {  //right
            return root;
        }
    }
};
```

### 701

```c++
/*time: O(n) space:O(height) */
class Solution {
public:
    TreeNode* insertIntoBST(TreeNode* root, int val) {
        TreeNode* tr = new TreeNode();
        tr -> val = val;
        if (!root) {
            return tr;
        }
        if (root -> val > val) { //left
            root -> left =  insertIntoBST(root -> left, val);
        }
        if (root -> val < val) {
            root -> right =  insertIntoBST(root -> right, val);
        }
        return root;
    }
};
```

### 450

```c++
/*time: O(n) space:O(height) */
class Solution {
public:

    TreeNode* deleteNode(TreeNode* root, int key) {
        if (!root) {
            return nullptr;
        }
        int val = root -> val;
        if (key > val) {
            root -> right = deleteNode(root -> right, key);
        }
        else if (key < val) {
            root -> left = deleteNode(root -> left, key);
        }
        else {
            if (root -> left && root -> right) {
                auto lnode = findleftnode(root -> right);
                lnode -> left = root -> left;
                auto rt = root -> right;
                delete root;
                return rt;
            }
            else if (root -> left) {
                auto rt = root -> left;
                delete root;
                return rt;
            }
            else if (root -> right) {
                auto rt = root -> right;
                delete root;
                return rt;
            }
            else {
                delete root;
                return nullptr;
            }
        }
        return root;
    }

    TreeNode* findleftnode(TreeNode* root) {
        if (root -> left == nullptr) {
            return root;
        }
        return findleftnode(root -> left);
    }
};
```

### 
