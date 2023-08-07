# Day16 错题()

### 104

```c++
/*time: O(n) space: O(height) */
class Solution {
public:
    int maxDepth(TreeNode* root) {
        if (root == nullptr) {
            return 0;
        }
        return max(maxDepth(root -> left), maxDepth(root -> right)) + 1; 
    }
};
```

### 559

```c++
/*time: O(n) space:O(height) */
class Solution {
public:
    int maxDepth(Node* root) {
        if (root == nullptr) {
            return 0;
        }
        int maxd = 0;
        for(auto child:root->children) {
            int temp = maxDepth(child);
            if (temp > maxd) maxd = temp;
        }
        return maxd + 1;
    }
};
```

### 111

```c++
/*time: O(n) space:O(height) */
class Solution {
public:
    int minDepth(TreeNode* root) {
        if(root == nullptr) {
            return 0;
        }
        if (root -> left == nullptr) return 1 + minDepth(root->right);
        if (root -> right == nullptr) return 1 + minDepth(root->left);
        return min(minDepth(root -> left), minDepth(root->right)) + 1;
    }
};
```

### 222

```c++
/*time: O(logn * logn) space:O(1) */
class Solution {
public:
    // count depth
    int countLevels(TreeNode* root) {
        int levels = 0;
        while (root) {
            root = root->left; 
            levels += 1;
        }
        return levels;
    }
    int countNodes(TreeNode* root){
        if(root == nullptr) return 0;
        int left_levels = countLevels(root->left);
        int right_levels = countLevels(root->right);
        if(left_levels == right_levels){ // 左子树是满二叉树的情况
            return countNodes(root->right) + (1<<left_levels);
        }else{
            return countNodes(root->left) + (1<<right_levels);
        }
    }
};

```





