# Module 4: Advanced Java - Concurrency & Streams

## Topic: The Java Memory Model (JMM)

### Deep Explanation
Concurrency is about doing multiple things at once. The JMM defines how threads interact through memory and what behaviors are allowed in a multi-threaded environment.

### Code Example: Visibility Issue
```java
class SharedData {
    boolean ready = false; // Missing 'volatile'!
}
// Thread 1 might never see the change made by Thread 2
// because the 'ready' flag is cached in the CPU register.
```

### Internal Working: Happens-Before
The JMM is based on the "Happens-Before" relationship.
- A write to a `volatile` field happens-before every subsequent read of that same field.
- Releasing a lock happens-before acquiring that same lock.
- These rules prevent the CPU and Compiler from reordering instructions in ways that break multi-threaded logic.

### Real Use Case
**Database Connection Pools**: Pools use `AtomicInteger` and `ReentrantLock` to ensure that multiple threads can safely borrow and return connections without race conditions.

### Exercise
1. What is a "Race Condition" and how can you prevent it?
2. Explain the difference between `synchronized` and `ReentrantLock`.

---

## Topic: Streams API & Functional Programming

### Deep Explanation
Streams allow for functional-style operations on collections (map, filter, reduce). They focus on *what* to do rather than *how* to do it.

### Code Example: Stream Pipeline
```java
List<String> names = Arrays.asList("Alice", "Bob", "Charlie");
long count = names.stream()
                  .filter(n -> n.startsWith("A"))
                  .count();
```

### Internal Working: Lazy Evaluation
Streams are **Lazy**. Intermediate operations (`filter`, `map`) do not perform any work. They just build a pipeline. The work is only executed when a **Terminal Operation** (`count`, `collect`) is called. This allows the JVM to optimize the entire processing chain in a single pass.

### Real Use Case
**Data Processing**: Processing large CSV files or API responses. Using `parallelStream()` can automatically distribute the work across all available CPU cores.

### Exercise
1. Convert a traditional `for-loop` that filters and sorts a list into a Stream pipeline.
2. What are the dangers of using `parallelStream()` with stateful operations?
