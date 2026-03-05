# Module 6: Data Structures in Java - Algorithms Deep Dive

## Topic: Sorting Internals (TimSort)

### Concept Explanation
Java's `Arrays.sort()` for objects doesn't use pure Merge Sort. It uses **TimSort**.

### Internal Working
TimSort is a hybrid algorithm (Merge Sort + Insertion Sort).
1.  It finds "Runs" (sequences of already sorted data).
2.  It uses **Insertion Sort** for small runs (very fast for small $).
3.  It merges these runs using a modified **Merge Sort**.

---

## Topic: Binary Search (Internal Optimization)

### Concept Explanation
Finding an element in a sorted list.

### Internal Working: The "Mid" Overflow Bug
Old implementation: `int mid = (low + high) / 2;`
**Bug**: If `low + high` exceeds ^{31}-1$, it overflows to a negative number.
**Fix**: `int mid = low + (high - low) / 2;` or `int mid = (low + high) >>> 1;`.

---

## Topic: Big O - Space vs Time Complexity

### Concept Explanation
- **Time**: How many operations.
- **Space**: How much extra memory.

### Real World Use Case: Trade-offs
A **Memoization** table (Dynamic Programming) uses extra Space ((n)$) to drastically reduce Time (from (2^n)$ to (n)$).

### Exercises
1. Compare the space complexity of iterative DFS vs recursive DFS.
2. What is the Big O of `HashMap.get()` in the best, average, and worst cases?
