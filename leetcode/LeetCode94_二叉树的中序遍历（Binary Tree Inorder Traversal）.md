---
LeetCode94:二叉树的中序遍历(Binary Tree Inorder Traversal)
---



#### 英文题目：


Given a binary tree, return the inorder traversal of its nodes' values.

**Example:**

```
Input: [1,null,2,3]
    1
    \
        2
    /
    3

Output: [1,3,2]
```

Follow up: Recursive solution is trivial, could you do it iteratively?


#### 中文题目：


给定一个二叉树，返回它的中序 遍历。

**示例:**

```
输入: [1,null,2,3]
    1
    \
        2
    /
    3

输出: [1,3,2]
```

进阶: 递归算法很简单，你可以通过迭代算法完成吗？



#### 解答：

##### C++

```
/**
    * Definition for a binary tree node.
    * struct TreeNode {
    *     int val;
    *     TreeNode *left;
    *     TreeNode *right;
    *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
    * };
    */
class Solution {
public:
    vector<int> inorderTraversal(TreeNode* root) {
        vector<int> res;
        stack<TreeNode*> stk;
        
        auto p=root;
        while (p || stk.size())
        {
            while (p)
            {
                stk.push(p);
                p = p->left;
            }
            p = stk.top();
            stk.pop();
            res.push_back(p->val);
            p=p->right;
        }
        return res;
    }
};
```
