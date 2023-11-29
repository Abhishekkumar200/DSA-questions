# Size of Largest BST in Binary Tree

### Problem Statement:
---
You are given a binary tree with `N` nodes. Your task is to return the size of the largest subtree of the `binary tree` which is also a `BST`.
A `binary search tree` (BST) is a `binary tree` data structure which has the following properties.

* `The left subtree of a node contains only nodes with data less than the node's data.`
* `The right subtree of a node contains only nodes with data greater than the node's data.`
* `Both the left and right subtrees must also be binary search trees.`

### Code:
---
```C++
#include <bits/stdc++.h> 
/************************************************************
    Following is the Binary Tree node structure
    
    template <typename T>
    class TreeNode {
        public :
        T data;
        TreeNode<T> *left;
        TreeNode<T> *right;
        TreeNode(T data) {
            this -> data = data;
            left = NULL;
            right = NULL;
        }
        ~TreeNode() {
            if(left)
                delete left;
            if(right)
                delete right;
        }
    };
************************************************************/
class info
{
    public:
    int size;
    int maxi;
    int mini;
    bool isBst;
};

info solution(TreeNode<int>* &root, int &maxSize)
{
    if(root==NULL)
    {
        info temp;
        temp.size = 0;
        temp.maxi = INT_MIN;
        temp.mini = INT_MAX;
        temp.isBst = true;
        return temp;
    }
    info left = solution(root->left, maxSize);
    info right = solution(root->right, maxSize);
    info current;
    current.size = left.size + right.size + 1;
    current.maxi = max(root->data, right.maxi);
    current.mini = min(root->data, left.mini);
    if(left.isBst && right.isBst && (root->data>left.maxi && root->data<right.mini))
    {
        current.isBst = true;
    }
    else
    {
        current.isBst = false;
    }
    if(current.isBst)
    {
        maxSize = max(maxSize, current.size);
    }
    return current;
}

int largestBST(TreeNode<int>* root) 
{
    // Write your code here.
    int maxSize = 0;
    info ans = solution(root, maxSize);
    return maxSize;
}

```
