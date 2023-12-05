# [Is Binary Tree Heap](https://www.geeksforgeeks.org/problems/is-binary-tree-heap/1)

### Problem Statement:
Given a `binary tree`. The task is to check whether the given tree follows the `max heap` property or not.

#### Note: 
Properties of a `tree` to be a `max heap` - *Completeness and Value of node greater than or equal to its child.*


#### Example 1:

**Input:**

<img width="101" alt="image" src="https://github.com/Abhishekkumar200/DSA-questions/assets/84954320/cd65fd00-0c97-42eb-bc70-0cd764de2972">

**Output:** 1

**Explanation:** The given `tree` follows `max-heap` property since 5, is root and it is greater than both its children.


#### Example 2:

**Input:**

<img width="108" alt="image" src="https://github.com/Abhishekkumar200/DSA-questions/assets/84954320/d5f87777-927e-4e4a-a139-80822a9667a9">

**Output:** 0


#### Your Task:
You don't need to read input or print anything. Your task is to complete the function `isHeap()` which takes the root of `Binary Tree` as parameter returns **True** if the given `binary tree` is a `heap` else returns **False**.

* `Expected Time Complexity: O(N)`
* `Expected Space Complexity: O(N)`


### Constraints:
* `1 ≤ Number of nodes ≤ 100`
* `1 ≤ Data of a node ≤ 1000`


### Code:

```C++

// Structure of node
/*struct Node {
    int data;
    Node *left;
    Node *right;

    Node(int val) {
        data = val;
        left = right = NULL;
    }
};*/

class Solution {
  public:
  
    int count(struct Node* tree)
    {
        if(tree==NULL)
        {
            return 0;
        }
        
        int ans = 1 + count(tree->left) + count(tree->right);
        
        return ans;
    }
    
    bool countBinaryTree(struct Node* tree, int index, int count)
    {
        if(tree==NULL)
        {
            return true;
        }
        
        if(index>=count)
        {
            return false;
        }
        else
        {
            bool left = countBinaryTree(tree->left, 2*index+1, count);
            bool right = countBinaryTree(tree->right, 2*index+2, count);
            return left && right;
        }
    }
    
    bool isMax(struct Node* root)
    {
        if(root->left==NULL && root->right==NULL)
        {
            return true;
        }
        
        if(root->right == NULL)
        {
            return (root->data > root->left->data);
        }
        else
        {
            bool left = isMax(root->left);
            bool right = isMax(root->right);
            
            return left && right && (root->data > root->left->data) && (root->data > root->right->data);
        }
    }
    
    bool isHeap(struct Node* tree) {
        // code here
        int index =0;
        
        int cnt = count(tree);
        
        if((countBinaryTree(tree, index, cnt))&&isMax(tree))
        {
            return true;
        }
        else
        {
            return false;
        }
    }
};

//{ Driver Code Starts.

int main() {
    int tc;
    scanf("%d ", &tc);
    while (tc--) {
        string treeString;
        getline(cin, treeString);
        Solution ob;
        Node *root = buildTree(treeString);
        if (ob.isHeap(root))
            cout << 1 << endl;
        else
            cout << 0 << endl;
    }

    return 0;
}
// } Driver Code Ends

```
