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
