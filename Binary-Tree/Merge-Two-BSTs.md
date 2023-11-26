# Merge Two BSTs
### Problem Statement:
- - - -
You are given two `balanced binary search trees` of integers having `N` and `M` nodes. You have to merge the two `BSTs` into a `balanced binary search tree` and return the root node to that balanced `BST`.
A `binary search tree` (BST) is a binary tree data structure with the following properties. 
* The left subtree of a node contains only nodes with data less than the node's data.
* The right subtree of a node contains only nodes with data greater than the node's data.
* Both the left and right subtrees must also be binary search trees.

### Code:
- - - -

```C++
#include <bits/stdc++.h> 
/*************************************************************
    
    Following is the Binary Tree node structure:
    class TreeNode{
        public :
            int data;
            TreeNode *left;
            TreeNode *right;
            TreeNode(int data) {
                this -> data = data;
                left = NULL;
                right = NULL;
            }
            ~TreeNode() {
            if (left){
            delete left;
            }
            if (right){
            delete right;
            }
        }   
    };
*************************************************************/

void inorderTraversal(TreeNode<int> *root, vector<int> &v)
{
    if(root==NULL)
    {
        return;
    }
    inorderTraversal(root->left, v);
    v.push_back(root->data);
    inorderTraversal(root->right, v);
}

vector<int> mergeTwoVector(vector<int> &v1, vector<int> &v2)
{
    int i=0, j=0, k=0;
    vector<int> v3(v1.size()+v2.size());
    while(i<v1.size() && j<v2.size())
    {
        if(v1[i]<v2[j])
        {
            v3[k] = v1[i];
            i++;
            k++;
        }
        else
        {
            v3[k] = v2[j];
            j++;
            k++;
        }
    }
    while(i<v1.size())
    {
        v3[k] = v1[i];
        i++;
        k++;
    }
    while(j<v2.size())
    {
        v3[k] = v2[j];
        j++;
        k++;
    }
    return v3;
}

TreeNode<int> * createBst(vector<int> &v, int start, int end)
{
    if(start>end)
    {
        return NULL;
    }
    int mid = (start+end)/2;
    TreeNode<int> * root = new TreeNode<int>(v[mid]);
    root->left = createBst(v, start, mid-1);
    root->right = createBst(v, mid+1, end);
    // return root;
}

TreeNode<int> *mergeBST(TreeNode<int> *root1, TreeNode<int> *root2){
    // Write your code here.
    vector<int> v1;
    vector<int> v2;
    vector<int> v3;
    inorderTraversal(root1, v1);
    inorderTraversal(root2, v2);
    v3 = mergeTwoVector(v1, v2);
    
    TreeNode<int> *ans = createBst(v3, 0, v3.size()-1);
    return ans;
}

```
