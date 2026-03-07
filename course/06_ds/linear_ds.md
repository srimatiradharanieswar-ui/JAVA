# Module 6: Data Structures in Java - Linear Deep Dive

## Topic: Arrays vs. Linked Lists

### Deep Explanation
Arrays and Linked Lists are the building blocks of most other data structures. Arrays provide (1)$ random access, while Linked Lists allow for (1)$ insertions and deletions at known positions.

### Code Example: Performance Comparison
```java
List<Integer> arrayList = new ArrayList<>();
List<Integer> linkedList = new LinkedList<>();

// ArrayList is much faster for search
arrayList.get(5000); // O(1)
linkedList.get(5000); // O(n) - must traverse 5000 nodes
```

### Internal Working: Cache Locality
- **Arrays**: Stored in contiguous memory. When the CPU fetches `arr[i]`, it also fetches `arr[i+1]` into the L1 cache, leading to high "Spatial Locality".
- **Linked Lists**: Each node is a separate object on the heap. Traversing a list involves following pointers to random memory locations, causing "Cache Misses" and slowing down the CPU.

### Real Use Case
**Large Data Buffers**: Video players and network stacks use primitive arrays (or `ByteBuffer`) to store data because the sequential access pattern perfectly matches how CPU caches work.

### Exercise
1. Implement a Doubly Linked List from scratch in Java.
2. What is the time complexity of `ArrayList.add(0, value)`? Explain why.

---

## Topic: Stack & Queue Implementation

### Deep Explanation
Stacks (LIFO) and Queues (FIFO) are linear structures with restricted access patterns.

### Code Example: Custom Array-based Stack
```java
public class MyStack {
    private int[] data = new int[10];
    private int top = -1;
    public void push(int x) { data[++top] = x; }
    public int pop() { return data[top--]; }
}
```

### Internal Working: Memory vs. Performance
- **ArrayDeque**: Java's recommended implementation for both Stack and Queue. It uses a circular array that resizes when full. It is faster than `Stack` (which is synchronized) and `LinkedList` (which has node overhead).

### Real Use Case
**Undo/Redo Logic**: Every modern text editor uses a Stack to keep track of user actions. Pressing Ctrl+Z pops the last action from the stack and reverses it.

### Exercise
1. Explain how a "Circular Buffer" works for a Queue implementation.
2. Why is `java.util.Stack` considered deprecated in modern Java development?
