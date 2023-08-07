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
/*time: O(n) space:O(height) */
class Solution {
public:
    int countNodes(TreeNode* root) {
        if (root == nullptr) {
            return 0;
        }
        return 1 + countNodes(root->left) + countNodes(root->right);
    }
};
```





