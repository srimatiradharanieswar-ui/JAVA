# Module 4: Advanced Java - System & Meta-programming

## Topic: Java NIO (New I/O)

### Deep Explanation
While standard I/O (`java.io`) is blocking and stream-oriented, NIO (`java.nio`) is non-blocking and buffer-oriented. This allows a single thread to manage multiple concurrent connections.

### Code Example: ByteBuffer Usage
```java
RandomAccessFile file = new RandomAccessFile("test.txt", "rw");
FileChannel channel = file.getChannel();
ByteBuffer buffer = ByteBuffer.allocate(48);
int bytesRead = channel.read(buffer);
```

### Internal Working: Selectors & Channels
NIO uses **Selectors**. A thread can register multiple **Channels** (sockets or files) with a Selector and then "select" only those that are ready for reading or writing. This is the foundation of high-performance servers like **Netty**.

### Real Use Case
**Web Servers**: Modern web servers (like Tomcat or Undertow) use NIO to handle thousands of concurrent HTTP connections without creating thousands of threads, which would exhaust memory.

### Exercise
1. What is the difference between a "Direct Buffer" and a "Heap Buffer"?
2. Explain how a Selector can reduce the number of threads needed for a networking app.

---

## Topic: Reflection & Annotations

### Deep Explanation
Reflection allows a program to inspect and modify its own structure at runtime. Annotations provide metadata that can be read by the compiler or at runtime via reflection.

### Code Example: Accessing Private Fields
```java
Field field = MyClass.class.getDeclaredField("privateSecret");
field.setAccessible(true);
String value = (String) field.get(instance);
```

### Internal Working: Inflation
Reflection is initially slow because the JVM has to check permissions and perform lookups. To optimize, after several calls to the same method, the JVM "inflates" the call by generating a custom accessor class in bytecode, making subsequent calls almost as fast as direct calls.

### Real Use Case
**Dependency Injection (Dagger/Hilt)**: These frameworks use reflection (or compile-time code generation based on annotations) to automatically "inject" dependencies into your classes.

### Exercise
1. Why is reflection generally slower than direct code?
2. Create a custom annotation `@LogTime` and a processor that measures how long a method takes to execute.
