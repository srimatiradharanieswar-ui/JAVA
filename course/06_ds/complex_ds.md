# Module 6: Data Structures in Java - Complex Deep Dive

## Topic: HashMap (Internal Collision Handling)

### Concept Explanation
HashMap uses an array of buckets to store entries.

### Internal Working: The Transformation
1.  **Hash**: `index = (n - 1) & hash(key)`.
2.  **Chaining**: Initially, collisions are handled via a Linked List.
3.  **Treeification**: If a bucket exceeds 8 elements (TREEIFY_THRESHOLD) and the total map capacity is > 64, Room converts the list into a **Red-Black Tree**.
4.  **Untreeification**: If the count drops below 6, it converts back to a list.

### Why It Exists
To prevent **Denial of Service (DoS)** attacks where an attacker sends many keys with the same hash code to force (n)$ performance. Treeification ensures (\log n)$ even in the worst case.

---

## Topic: Trees (Balanced BSTs)

### Concept Explanation
A simple Binary Search Tree can become "Skewed" (like a linked list) if elements are added in order, making search (n)$.

### Internal Working: AVL & Red-Black Trees
These trees use **Rotations** during insertion and deletion to ensure the height remains (\log n)$. Java's `TreeMap` and `TreeSet` use **Red-Black Trees**.

---

## Topic: Graphs (BFS vs DFS)

### Concept Explanation
- **DFS (Depth First Search)**: Uses a **Stack** (or recursion). Explores as far as possible along each branch.
- **BFS (Breadth First Search)**: Uses a **Queue**. Explores all neighbors at the current depth before moving deeper.

### Exercises
1. Explain the "Load Factor" in HashMap and how it affects performance.
2. Implement a Depth-First Search for a Graph represented by an Adjacency List.
