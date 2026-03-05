# Section 6: Data Structures in Java

## Module 1: Linear Data Structures

### 1. Linked List
**Explanation:** A sequence of nodes where each node contains data and a reference to the next node.
**Internal Working:** Non-contiguous memory allocation.
**Complexity:** Access O(n), Insertion O(1).

### 2. Stack & Queue
- **Stack:** LIFO (Last In First Out). Used in method calls and undo operations.
- **Queue:** FIFO (First In First Out). Used in task scheduling.

---

## Module 2: Non-Linear Data Structures

### 1. HashMap (Revisited)
**Concept:** Associative array using hashing.
**Real Use Case:** Caching, database indexing.

### 2. Trees (Binary Search Tree)
**Concept:** Hierarchical structure.
**Complexity:** Search O(log n).

### 3. Graphs
**Concept:** Collection of nodes (vertices) and edges.
**Implementation:** Adjacency List or Matrix.

---

## Module 3: Algorithms

### 1. Sorting
- **Bubble Sort:** O(n^2).
- **Quick Sort:** O(n log n).
- **Merge Sort:** O(n log n). Stable.

### 2. Searching
- **Linear Search:** O(n).
- **Binary Search:** O(log n) - Requires sorted input.

---

## Module 4: Big O Notation

### Deep Explanation
Used to describe the performance or complexity of an algorithm.
- **O(1):** Constant.
- **O(log n):** Logarithmic.
- **O(n):** Linear.
- **O(n^2):** Quadratic.

### Code Example (Binary Search)
```java
public int binarySearch(int[] arr, int target) {
    int low = 0, high = arr.length - 1;
    while (low <= high) {
        int mid = low + (high - low) / 2;
        if (arr[mid] == target) return mid;
        if (arr[mid] < target) low = mid + 1;
        else high = mid - 1;
    }
    return -1;
}
```

### Interview Questions
- Compare ArrayList and LinkedList.
- How to detect a cycle in a Linked List?
- Explain the difference between BFS and DFS.

### Exercise
1. Implement a Stack using an Array.
2. Implement a Queue using two Stacks.
