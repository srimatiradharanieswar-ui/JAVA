# Module 4: Advanced Java - Concurrency & JMM

## Topic: The Java Memory Model (JMM)

### Concept Explanation
The JMM defines how the Java runtime interacts with the computer's memory. It handles the complexities of CPU caches and instruction reordering.

### Internal Working: Happens-Before Relationship
To ensure visibility and order, the JMM defines "Happens-Before" rules:
1.  **Monitor Lock Rule**: A release of a lock happens-before every subsequent acquisition of the same lock.
2.  **Volatile Variable Rule**: A write to a volatile field happens-before every subsequent read of that same field.
3.  **Thread Start Rule**: Calling `Thread.start()` happens-before any action in the started thread.

### Why It Exists: Instruction Reordering
The CPU and Compiler can swap the order of instructions to improve performance. The JMM prevents this reordering from breaking multi-threaded logic when using synchronization.

---

## Topic: CAS (Compare-And-Swap) & Lock-Free Data Structures

### Concept Explanation
Standard `synchronized` locks are "Pessimistic" and heavy. CAS is an "Optimistic" alternative.

### Internal Working: The atomic hardware instruction
CAS uses a single CPU instruction that:
1.  Takes a memory location.
2.  Takes an expected value.
3.  Takes a new value.
4.  **Atomically** swaps the values ONLY if the current value matches the expected one.

### Java Implementation: `AtomicInteger`
```java
AtomicInteger counter = new AtomicInteger(0);
counter.incrementAndGet(); // Uses CAS in a loop
```

---

## Topic: AQS (AbstractQueuedSynchronizer)

### Concept Explanation
AQS is the framework behind most of Java's concurrency utilities (`ReentrantLock`, `Semaphore`, `CountDownLatch`).

### Internal Working
AQS maintains a **volatile state** integer and a **FIFO Wait Queue** of threads.
- If a thread fails to acquire the state (e.g., the lock is held), AQS enqueues the thread and parks it.
- When the lock is released, AQS unparks the head of the queue.

### Interview Questions
1. What is the difference between `volatile` and `atomic`? (`volatile` ensures visibility; `atomic` ensures visibility AND atomicity).
2. Explain the "False Sharing" problem and how `@Contended` solves it.

### Exercises
1. Implement a thread-safe Singleton using the "Double-Checked Locking" pattern. Why is `volatile` mandatory here?
2. Create a high-concurrency counter and compare the speed of `synchronized` vs `LongAdder`.
