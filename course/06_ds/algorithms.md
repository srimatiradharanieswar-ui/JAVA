# Module 6: Data Structures in Java - Algorithms Deep Dive

## Topic: Sorting Internals (TimSort)

### Deep Explanation
Sorting is the process of arranging data in a specific order. Java's default sort for objects, `Arrays.sort()`, is a highly optimized version of Merge Sort called TimSort.

### Code Example: Custom Sorting
```java
List<String> list = Arrays.asList("Banana", "Apple", "Cherry");
list.sort((a, b) -> a.compareTo(b));
```

### Internal Working: TimSort Algorithm
TimSort is a hybrid algorithm (Merge Sort + Insertion Sort).
1. It identifies "Runs" (naturally sorted sub-sequences).
2. It uses **Insertion Sort** for small sub-arrays (very fast due to low overhead).
3. It merges these runs using a stable Merge Sort approach.
**Stability**: TimSort is stable, meaning elements with equal keys maintain their relative order.

### Real Use Case
**E-commerce Product Listings**: When a user sorts by "Price" and then by "Rating", a stable sort ensures that the price-based order is preserved for items with the same rating.

### Exercise
1. What is the Big O complexity of TimSort in the best and worst cases?
2. Why is QuickSort generally faster than Merge Sort for primitive arrays, even though they have the same average Big O?

---

## Topic: Binary Search (Internal Optimization)

### Deep Explanation
Binary search is a fast way to find an element in a **sorted** array by repeatedly dividing the search interval in half.

### Code Example: The "Mid" Bug
```java
// The wrong way (can overflow)
int mid = (low + high) / 2;

// The correct way
int mid = low + (high - low) / 2;
// OR using bit shift
int mid = (low + high) >>> 1;
```

### Internal Working: The Overflow Fix
In the old `(low + high) / 2` approach, if the sum exceeds ^{31}-1$, it overflows into a negative number, leading to an `ArrayIndexOutOfBoundsException`. Using the unsigned right shift `>>>` or the subtraction method avoids this overflow.

### Real Use Case
**Large Scale Search**: Git uses binary search (`git bisect`) to find the exact commit that introduced a bug in a codebase with thousands of commits.

### Exercise
1. Implement a recursive version of Binary Search in Java.
2. What is the maximum number of comparisons for a list of 1 million elements using binary search?

---

## Topic: Big O - Space vs Time Complexity

### Deep Explanation
Big O notation is used to describe the efficiency of an algorithm as the input size grows.

### Internal Working: Complexity Classes
- **O(1)**: Constant (e.g., `array[i]`).
- **O(log n)**: Logarithmic (e.g., Binary Search).
- **O(n)**: Linear (e.g., for-loop).
- **O(n log n)**: Linearithmic (e.g., TimSort).
- **O(n²)**: Quadratic (e.g., Nested loops).

### Real Use Case
**Dynamic Programming**: Algorithms like "Fibonacci with Memoization" use Space Complexity ((n)$) to drastically reduce Time Complexity from (2^n)$ to (n)$. This "Space-Time Tradeoff" is a fundamental concept in engineering.

### Exercise
1. What is the Big O of `HashMap.get()` in the best, average, and worst cases?
2. Analyze the time and space complexity of your favorite sorting algorithm.
