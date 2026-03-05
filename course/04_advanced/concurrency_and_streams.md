# Module 4: Advanced Java - Concurrency & Streams

## Topic: Multithreading & Concurrency
- **JMM (Java Memory Model)**: Defines how threads interact through memory. Each thread has its own **Stack** but shares the **Heap**.

---

## Topic: Lambda Expressions & Streams API
Streams are **lazy**. They don't process data until a "terminal operation" is called.

### Code Example
```java
List<String> names = Arrays.asList("Alice", "Bob");
names.stream().filter(s -> s.startsWith("A")).forEach(System.out::println);
```

---

## Topic: Advanced Concurrency
**ExecutorService**: Manage a thread pool instead of raw threads.
