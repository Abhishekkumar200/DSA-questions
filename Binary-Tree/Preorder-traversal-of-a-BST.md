# Preorder traversal of a BST.
### Problem Statement:
You have been given an array/list `PREORDER` representing the preorder traversal of a BST with `N` nodes. All the elements in the given array have distinct values.
Your task is to construct a binary search tree that matches the given preorder traversal.
A binary search tree (BST) is a binary tree data structure that has the following properties:
* `The left subtree of a node contains only nodes with data less than the node's data.`
* `The right subtree of a node contains only nodes with data greater than the node's data.`
* `Both the left and right subtrees must also be binary search trees.`

### Code:

```C++
BinaryTreeNode<int>* constructBst(vector<int> &preorder, int mini, int maxi, int &count)
{
    if(count>=preorder.size())
    {
        return NULL;
    }
    else if(preorder[count]<mini || preorder[count]>maxi)
    {
        return NULL;
    }
    // cout<<"count->"<<count<<endl;
    BinaryTreeNode<int>* root = new BinaryTreeNode<int>(preorder[count++]);
    root->left = constructBst(preorder, mini, root->data, count);
    root->right = constructBst(preorder, root->data, maxi, count);
}

BinaryTreeNode<int>* preorderToBST(vector<int> &preorder) {
    // Write your code here.
    int count = 0;
    BinaryTreeNode<int>* ans = constructBst(preorder, INT_MIN, INT_MAX, count);
    return ans;
}

```
