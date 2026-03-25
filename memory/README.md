# How to utilize Artificial Intelligence to maximize learning

## Understanding AI in Education

The first thing you must do is to understand that AI is not your friend but a collection of applied concepts ranging the field of mathematics, computing and neurology. Recently AI has a negative impact on education, especially in regards to academic integrity, this being said rather using it as a method to cheat on your highschool/college courses you should actually use it to maximize your learning in efficient manners. 

## How to properly use AI as a Tool and not a as a Method to Cheat (quick prompts)

- Active Learning First

```
The user prioritizes learning through direct problem solving and hands on practice. AI assistance should support this process by offering guidance, relevnt resources, and prompting critical thinking rather than providing complete solutions or final anwsers. 
```

- Guided Support, Not Substitution

```
AI should function as a supplementary tool, helping clarify concepts, break down problems, and suggest approaches all without replacing the user's own reasoning or effort.
```

- Progress Tracking

```
The user maintains a todo.txt file to document ongoing tasks and progress. AI may assist by suggesting updates or identifying next steps, but responsibility for tracking remains with user.
```

- Academic Integrity Alignment

```
All AI usage must align with academic rules stated in course outlines. This being said, even if it's agaisn't academic rules, i heavily suggest you to utilize AI ONLY if you are stuck even after reaching out for help. Your grades matter as long as you are authentic with your efforts. Do not utilize AI to cheat or pass work as your own. I am suggesting to use AI as assistance, not a learning crutch but rathger as a way to push you towards the proper learning methods instead of wasting your time recursively
```

## Specifc Field AI Usage Guidelines

- Data structure & Algorithms
    - Explain concepts
    - Request hints, edge cases, test scenarios
    - Avoid copying line by line. Prompt correctly to force the AI to push you agaisn't your limit.

- Mathematics & Physics
    - Explain concepts, step by step, theorem intuition and even verification of results
    - Ask for guiding questions when solving problems rather than direct anwsers
    - Focus on understanding derivations and reasoning, not just the final product

## Claude CLI/Original

If you wish to learn rapidly and quickly use either Claude webapp or Claude CLI to help you dig deep in understanding on the topic at hand. You do have to make sure that if you are using Claude CLI, you are also using what i call persistent memory (As of now most AI have terrible memory). One way to have persistent memory (Instance Memory | Not fully considered memory it just replicates memory) is to create a `memory.txt` file unto which you will always do a quick save every minute when chatting with your Claude CLI.

## Memory.txt Example

````
# DSA Study Notes
Date: 2026-03-24
Textbook: Open Data Structures (ODS) - Java Edition
Source: opendatastructures.org

---

## What is a Binary Tree?

A binary tree is a hierarchical data structure where each node has at most two children: left and right.

### Key Terms
- Root: top node (no parent)
- Leaf: node with no children
- Height: longest path from root to a leaf
- Depth: distance of a node from the root

### Types
- Full: every node has 0 or 2 children
- Complete: all levels filled except possibly the last (filled left to right)
- Perfect: all internal nodes have 2 children, all leaves at same level
- Binary Search Tree (BST): left child < parent < right child

---

## ODS Chapter 6: Binary Trees

---

### 6.1 — BinaryTree: A Basic Binary Tree

#### Node Structure
```java
class BTNode<Node extends BTNode<Node>> {
    Node left;
    Node right;
    Node parent;
}
```
Missing neighbours are set to nil.

#### Recursive Methods
```java
int size(Node u) {
    if (u == nil) return 0;
    return 1 + size(u.left) + size(u.right);
}

int height(Node u) {
    if (u == nil) return -1;
    return 1 + Math.max(height(u.left), height(u.right));
}

int depth(Node u) {
    int d = 0;
    while (u != r) { u = u.parent; d++; }
    return d;
}
```

#### Traversals

**Recursive:**
```java
void traverse(Node u) {
    if (u == nil) return;
    traverse(u.left);   // in-order: visit u here
    traverse(u.right);
}
```

**Non-recursive (prev/next pointer):**
```java
void traverse2() {
    Node u = r, prev = nil, next;
    while (u != nil) {
        if (prev == u.parent) {
            if (u.left != nil) next = u.left;
            else if (u.right != nil) next = u.right;
            else next = u.parent;
        } else if (prev == u.left) {
            if (u.right != nil) next = u.right;
            else next = u.parent;
        } else {
            next = u.parent;
        }
        prev = u;
        u = next;
    }
}
```

**Breadth-first (level-order) using Queue:**
```java
void bfTraverse() {
    Queue<Node> q = new LinkedList<Node>();
    if (r != nil) q.add(r);
    while (!q.isEmpty()) {
        Node u = q.remove();
        if (u.left != nil) q.add(u.left);
        if (u.right != nil) q.add(u.right);
    }
}
```

#### Traversal Orders (Pre/In/Post)
- Pre-order:  Root -> Left -> Right
- In-order:   Left -> Root -> Right
- Post-order: Left -> Right -> Root

#### ODS Theorem
A binary tree with n nodes has n+1 external (nil) nodes.

---

### 6.2 — BinarySearchTree: An Unbalanced BST

**BST Property:** left subtree values < u.x < right subtree values

#### Search
```java
T find(T x) {
    Node w = r, z = nil;
    while (w != nil) {
        int comp = compare(x, w.x);
        if (comp < 0) { z = w; w = w.left; }
        else if (comp > 0) { w = w.right; }
        else { return w.x; }
    }
    return z == nil ? null : z.x;
}
```

#### Add
```java
boolean add(T x) {
    Node p = findLast(x);
    return addChild(p, newNode(x));
}

Node findLast(T x) {
    Node w = r, prev = nil;
    while (w != nil) {
        prev = w;
        int comp = compare(x, w.x);
        if (comp < 0) w = w.left;
        else if (comp > 0) w = w.right;
        else return w;
    }
    return prev;
}

boolean addChild(Node p, Node u) {
    if (p == nil) {
        r = u;
    } else {
        int comp = compare(u.x, p.x);
        if (comp < 0) p.left = u;
        else if (comp > 0) p.right = u;
        else return false;
        u.parent = p;
    }
    n++;
    return true;
}
```

#### Remove
```java
void remove(Node u) {
    if (u.left == nil || u.right == nil) {
        splice(u);  // 0 or 1 child
    } else {
        Node w = u.right;
        while (w.left != nil) w = w.left;  // smallest in right subtree
        u.x = w.x;
        splice(w);
    }
}

void splice(Node u) {
    Node s, p;
    if (u.left != nil) s = u.left;
    else s = u.right;
    if (u == r) { r = s; p = nil; }
    else {
        p = u.parent;
        if (p.left == u) p.left = s;
        else p.right = s;
    }
    if (s != nil) s.parent = p;
    n--;
}
```

#### Theorem 6.1
find, add, remove all run in O(n) worst case.
Tree can become unbalanced (like a linked list).

Balanced alternatives:
- Ch. 7: Randomization -> O(log n) expected
- Ch. 8: Partial rebuilding -> O(log n) amortized
- Ch. 9: 2-4 trees -> O(log n) worst case

---

### 6.3 — Discussion and Exercises

#### Design Decisions
- Parent pointer: saves recursion, costs space
- Store left/right/parent in array c[3]: sibling of u.c[i] = u.c[1-i]

#### Key Exercises
- 6.4: non-recursive size(u)
- 6.5: non-recursive height(u)
- 6.6: isBalanced() in O(n)
- 6.7: assign pre/in/post-order numbers
- 6.8: nextPreOrder, nextInOrder, nextPostOrder in amortized O(1)
- 6.9: use numberings to answer size/depth/ancestor queries in O(1)
- 6.19: maintain u.size, u.depth, u.height during add/remove

---

## Rootish Array Stack

A space-efficient dynamic array using a list of growing blocks.
Block b has size b+1. Total capacity after r blocks = r(r+1)/2.

### Index Mapping
```java
int[] locate(int i) {
    int b = (int)((-3 + Math.sqrt(9 + 8.0 * i)) / 2);
    int j = i - b * (b + 1) / 2;
    return new int[]{b, j};
}
```

### Complexity
| Operation   | Time   |
|-------------|--------|
| get(i)      | O(1)   |
| set(i, x)   | O(1)   |
| add(i, x)   | O(n)   |
| remove(i)   | O(n)   |
| Space wasted| O(sqrt(n)) |
````

## Conclusion

Enjoy your life, Use AI as leverage not as a "Get rich quick scheme". Nothing is easy but being used to hardship allows you to traverse this life with ease. Go out there and make me proud!
