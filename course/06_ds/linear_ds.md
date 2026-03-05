# Module 6: Data Structures in Java - Linear Deep Dive

## Topic: Arrays vs. Linked Lists (Internal Working)

### Concept Explanation
- **Array**: A contiguous block of memory. Accessing `arr[i]` is a simple address calculation: `base_address + (index * element_size)`.
- **Linked List**: A non-contiguous collection of nodes. Each node is an object on the heap containing a reference to the next.

### Why It Exists
Arrays are great for fast access, but resizing them is expensive ((n)$). Linked Lists allow for (1)$ insertion/deletion if the position is known.

### Internal Working: Cache Locality
- **Arrays**: High spatial locality. When you access `arr[0]`, the CPU fetches the next few elements into the cache automatically.
- **Linked Lists**: Poor spatial locality. Each node could be anywhere in the heap, causing frequent **Cache Misses**.

---

## Topic: Stack & Queue Implementation

### Concept Explanation
- **Stack**: LIFO (Last-In-First-Out).
- **Queue**: FIFO (First-In-First-Out).

### Internal Working
- **Array-based Stack**: Uses a `top` pointer. Very fast but has a fixed capacity.
- **List-based Stack**: Dynamic size but has object overhead for every push.

### Code Example: Custom Stack
```java
public class MyStack {
    private int[] data = new int[10];
    private int top = -1;
    public void push(int x) { data[++top] = x; }
    public int pop() { return data[top--]; }
}
```

### Exercises
1. Implement a Doubly Linked List from scratch.
2. What is the time complexity of `ArrayList.add(0, value)`? (Answer: (n)$ because all elements must be shifted).
