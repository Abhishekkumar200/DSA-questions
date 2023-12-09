# Convert BST to Min Heap

#### Problem Statement:
You are given a **root** of a `binary search tree` of integers. The given `BST` is also a `complete binary tree`.
Your task is to convert the given `binary search tree` into a `Min Heap` and print the __*preorder traversal*__ of the updated `binary search tree`.

#### Note:

**Binary Search Tree is a node-based binary tree data structure that has the following properties:**

1. The left _subtree_ of a node contains only nodes with keys _lesser_ than the node's key.

2. The right _subtree_ of a node contains only nodes with keys _greater_ than the node's key.

3. The left and right _subtree_ each must also be a `binary search tree`.

**A Binary Heap is a Binary Tree with the following:**

1. It's a complete tree (*all levels are filled except possibly the last level and the last level has all keys as left as possible*). This property of `Binary Heap` makes them suitable to be stored in an `array`.

A `Binary Heap` is either `Min Heap` or `Max Heap`. In a `Min Binary Heap`, the key at the root must be *minimum* among all keys present in `Binary Heap`. The same property must be recursively *true* for all nodes in `Binary Tree`. `Max Binary Heap` is similar to `Min Heap`.

#### Code:

```C++

#include <bits/stdc++.h> 
/*************************************************************
    
    Following is the Binary Tree node structure:
    class BinaryTreeNode {
        
    public :
        int data;
        BinaryTreeNode* left;
        BinaryTreeNode* right;
        BinaryTreeNode(int data) {
        this -> left = NULL;
        this -> right = NULL;
        this -> data = data;
        }
    };
*************************************************************/
void inorderTraversal(BinaryTreeNode* &root, vector<int> &v)
{
    if(root==NULL)
    {
        return;
    }
    
    inorderTraversal(root->left, v);
    v.push_back(root->data);
    inorderTraversal(root->right, v);
}
void createHeap(BinaryTreeNode* &root, vector<int> &v, int &index)
{
    if(root==NULL)
    {
        return;
    }
    root->data = v[index];
    index++;
    createHeap(root->left, v, index);
    createHeap(root->right, v, index);
}
BinaryTreeNode* convertBST(BinaryTreeNode* root)
{
    // Write your code here.
    if(root==NULL || (root->left==NULL && root->right==NULL))
    {
        return root;
    }
    
    vector<int> v;
    BinaryTreeNode* temp = root;
    int index = 0;
    inorderTraversal(temp, v);
    createHeap(root, v, index);
    return root;
}

```
