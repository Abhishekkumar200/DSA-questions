# Normal BST To Balanced BST

### Problem Statement:
---
You have been given a `binary search tree` of integers with `n` nodes your task is to convert it into a balanced `bst` with the minimum height possible.

### Code:
---
```C++
void inorderTraversal(TreeNode<int>* root, vector<int> &v)
{
    if(root==NULL)
    {
        return;
    }
    inorderTraversal(root->left, v);
    v.push_back(root->data);
    inorderTraversal(root->right, v);
}

TreeNode<int>* createBst(vector<int> &v, int start, int end)
{
    if(start>end)
    {
        return NULL;
    }
    int mid = (end+start)/2;
    TreeNode<int>* root = new TreeNode<int>(v[mid]);
    root->left = createBst(v, start, mid-1);
    root->right = createBst(v, mid+1, end);
}

TreeNode<int>* balancedBst(TreeNode<int>* root) {
    // Write your code here.
    vector<int> v;
    inorderTraversal(root, v);
    int size = v.size();
    TreeNode<int>* ans = createBst(v, 0, size-1);
    return ans;
}
```
