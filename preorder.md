# 144. 二叉树的前序遍历
## 1. 递归
```cpp
class Solution {
    vector<int> ret;
    void preorder(TreeNode* root) {
        if (root) {
            ret.emplace_back(root->val);
            preorder(root->left);
            preorder(root->right);
        }
    }
public:
    vector<int> preorderTraversal(TreeNode* root) {
        preorder(root);
        return ret;
    }
};
```

## 2. 迭代
```cpp
class Solution {
public:
    vector<int> preorderTraversal(TreeNode* root) {
        stack<TreeNode*> s;
        vector<int> ret;
        if (!root) {
            return ret;
        }
        //s.push(root);
        TreeNode* p = root;
        while (p || !s.empty()) {
            if (p) {
                ret.emplace_back(p->val);
                s.push(p);
                p = p->left;
            } else {
                if (!s.empty()) {
                    p = s.top()->right;
                    s.pop();
                } else {
                    p = NULL;
                }
            }
        }

        return ret;
    }
};
```

或者

```cpp
class Solution {
public:
    vector<int> preorderTraversal(TreeNode* root) {
        vector<int> ans;
        stack<TreeNode*> s;
        s.push(root);
        while(!s.empty()){
            TreeNode* r = s.top();
            s.pop();
            if(!r) continue;
            ans.push_back(r->val);
            s.push(r->right);
            s.push(r->left);
        }
        return ans;
    }
};
```