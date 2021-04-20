# 94. 二叉树的中序遍历
## 1. 递归
```cpp
class Solution {
    vector<int> ret;
    void inorder(TreeNode* root) {
        if (root) {
            inorder(root->left);
            ret.emplace_back(root->val);
            inorder(root->right);
        }
    }
public:
    vector<int> inorderTraversal(TreeNode* root) {
        inorder(root);
        return ret;
    }
};
```

## 2. 迭代
```cpp
class Solution {
public:
    vector<int> inorderTraversal(TreeNode* root) {
        vector<int> ret;
        if(!root) {
            return ret;
        }
        stack<TreeNode*> s;
        TreeNode* p = root;
        while (p || !s.empty()) {
            if (p) {
                s.push(p);
                p = p->left;
            } else {
                TreeNode* tmp = s.top();
                s.pop();
                ret.emplace_back(tmp->val);
                p = tmp->right;
            }
        }

        return ret;
    }
};
```