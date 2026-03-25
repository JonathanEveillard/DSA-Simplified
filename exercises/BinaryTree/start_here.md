# Binary Tree

## What is a Binary Tree?

A binary tree is a data structure that is set out to be hierachical where each node has at most two children. These children are broken down as the left child and the right child. The top most node (original node) is called the root node.

## Visual Example

Let's say you have the following data where 10 is the root, [10,5,20,3,7,30]


                10
               /  \
              5    20
             / \     \
            3  7      30

## Interface 

Binary Tree does not implement an interface by default as it is a standalone foundational class and not a collection (It's a structure). This being said, depending on how you're using the binary tree. This goes as shown below:

- Binary Search
    - Implements Sorted Set (SSET)
    - Implements Map (Keys,Value)
- Binary Heap
    - Priority Queue

## Supported Methods

| Method            | Description                              |
|-------------------|------------------------------------------|
| depth(Node)       | Steps from u to root                     |
| size()            | Total node count                         |
| size(Node u)      | Size of subtree at u (recursive)         |
| size2()           | Size of the tree (non-recursive)         |
| height()          | Height of the entire tree                |
| height(Node u)    | Height  of subtree at u (recurisve)      |
| traverse(Node u)  | Recursive traversal (Depth First Search) || traverse2()       | Non-recursive traversal (DFS)            |
| bfTraverse()      | Breadth First Traversal (level-order)    |
| firstNode()       | First node in traversal order            |
| nextNode(Node w)  | Next node after w in traversal order     |
| isEmpty()         | Check if tree is empty                   |
| clear()           | Empty the tre                            |

