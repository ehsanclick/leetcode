## Binary Tree Inorder Traversal

[Description](https://leetcode.com/problems/binary-tree-inorder-traversal/description/)

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
**Follow up:** Recursive solution is trivial, could you do it iteratively?

[Iterative Solution]()
If a node has left node, put the node to the most right position of left sub tree:

```c++
class Solution {
public:
    vector<int> inorderTraversal(TreeNode* root) {
        vector<int> res;
        while (root){
            if (root->left == NULL){
                res.push_back(root->val);
                root = root->right;
            }else{
                TreeNode* lefti = root->left;
                while (lefti->right != NULL)
                    lefti = lefti->right;
                lefti->right = root;
                TreeNode* next = root->left;
                root->left = NULL;
                root = next;
            }
        }
        return res;
    }
};
```
