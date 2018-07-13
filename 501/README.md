## Find Mode in Binary Search Tree

[Description](https://leetcode.com/problems/find-mode-in-binary-search-tree/description/)

Given a binary search tree (BST) with duplicates, find all the mode(s) (the most frequently occurred element) in the given BST.

Assume a BST is defined as follows:

    The left subtree of a node contains only nodes with keys less than or equal to the node's key.
    The right subtree of a node contains only nodes with keys greater than or equal to the node's key.
    Both the left and right subtrees must also be binary search trees.

For example:
Given BST [1,null,2,2],
```
   1
    \
     2
    /
   2
```
return [2]. 

[Solution]()
Go _in order_ in two passes:
1) count mode_count
2) return mode(s)
