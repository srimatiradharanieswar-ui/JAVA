# Module 6: Data Structures in Java - Complex Deep Dive

## Topic: HashMap (Internal Collision Handling)

### Deep Explanation
A HashMap uses hashing to store key-value pairs. It is the most commonly used data structure for (1)$ lookups.

### Code Example: Custom Key for HashMap
```java
class User {
    int id;
    @Override
    public int hashCode() { return Objects.hash(id); }
    @Override
    public boolean equals(Object obj) { ... }
}
```

### Internal Working: Treeification
1. **Hash**: Calculates bucket index using `(n-1) & hash`.
2. **Collision**: Multiple keys in one bucket are initially stored in a Linked List.
3. **Treeification**: If a bucket exceeds 8 elements (and map size > 64), Java 8+ converts the list to a **Red-Black Tree**. This improves worst-case performance from (n)$ to (\log n)$, preventing Hash Collision DoS attacks.

### Real Use Case
**Database Indexing**: Databases use structures similar to HashMaps and B-Trees to provide instant lookups for records based on their primary key.

### Exercise
1. Explain the "Load Factor" and why it defaults to 0.75.
2. What happens if two different keys have the same `hashCode()`?

---

## Topic: Trees & Balanced BSTs

### Deep Explanation
Binary Search Trees (BST) allow for fast search, insertion, and deletion. However, they must be "balanced" to maintain (\log n)$ performance.

### Code Example: TreeMap Usage
```java
TreeMap<String, Integer> map = new TreeMap<>();
map.put("Z", 1);
map.put("A", 2);
System.out.println(map.firstKey()); // Prints "A"
```

### Internal Working: Red-Black Trees
Java's `TreeMap` uses a Red-Black tree. It maintains balance through color properties and **Rotations** during insertions. This ensures the tree never becomes too deep on one side.

### Real Use Case
**File Systems**: Many file systems (like NTFS) use balanced trees to manage the structure of directories and files on a disk, ensuring that finding a file is fast regardless of how many files are in a folder.

### Exercise
1. What is the difference between a Binary Tree and a Binary Search Tree?
2. Perform a "Left Rotation" on a simple tree on paper.

---

## Topic: Graphs (BFS vs DFS)

### Deep Explanation
Graphs represent relationships between entities (nodes and edges).

### Internal Working: Traversal Algorithms
- **DFS (Depth First Search)**: Uses a **Stack** (or recursion). It goes deep into one branch before backtracking. Best for finding paths and solving puzzles (backtracking).
- **BFS (Breadth First Search)**: Uses a **Queue**. It visits all neighbors first. Best for finding the **Shortest Path** in an unweighted graph.

### Real Use Case
**Social Networks**: LinkedIn uses BFS to find "1st, 2nd, and 3rd-degree" connections. Google Maps uses versions of BFS (like Dijkstra's) to find the fastest route between two locations.

### Exercise
1. Represent a graph using an Adjacency List.
2. Implement BFS in Java to find if a path exists between two nodes.
