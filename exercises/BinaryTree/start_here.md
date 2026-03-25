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

## Key Vocabulary

| Term          | Meaning                                  |
|---------------|------------------------------------------|
| Root          | Top Node (Has no parent)                 |
| Leaf          | Node with no children                    |
| Depth of u    | Number of edges from u up to root        |
| Height of u   | Longest path downward from u to a leaf   |
| External Node | Nil placeholder child                    |
| Root          | u + all of its descendants               |
| Size          | Nodes in the subtree (including u itself |

## Defining a node

```java
class BTNode<Node extends BTNode<Node>> {
    Node left; // Left node | Set to nil if no data exist (External node)
    Node right; // Right node | Set to nil if no data exist (External node)
    Node parent; // Original node | Set to nil if no data exist (External node)
}
```

## Basic Operations

- ###depth(u) | How far is an input node (u) to the root?
```java

int depth(Node u) {
    int d = 0;
    while (u!=r) {
        u = u.parent;
        d++;
    }
    return d;
}
```

- ###size(u) | How many nodes are in the subtree rooted at u?
```java
int size(Node u){
    if (u == nil) return 0;
    return 1 + size(u.left) + size(u.right);
}
```

- ###height(u) | What is the longest path down from u?
```
int height(Node u){
    if (u == nil) return - 1;
    return 1 + Math.max(height(u.left), height(u.right));
}

## Important Theorems

- ### Chapter 6.0 [ODS]
    - A binary tree with n real nodes has exactly n+1 external nodes (nil nodes) 
