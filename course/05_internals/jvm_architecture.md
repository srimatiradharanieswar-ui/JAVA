# Module 5: Java Internals & JVM

## Topic: JVM Architecture & Runtime Data Areas

### Deep Explanation
The JVM is a virtual machine that provides a platform-independent execution environment for Java bytecode. It manages memory, executes code, and interacts with the host operating system.

### Code Example: Monitoring JVM Memory
```java
public class RuntimeInfo {
    public static void main(String[] args) {
        Runtime runtime = Runtime.getRuntime();
        System.out.println("Total Memory: " + runtime.totalMemory() / (1024 * 1024) + "MB");
        System.out.println("Free Memory: " + runtime.freeMemory() / (1024 * 1024) + "MB");
    }
}
```

### Internal Working: The Three Subsystems
1. **Class Loader Subsystem**: Responsible for loading (`.class` files), linking (verifying, preparing, resolving), and initializing classes.
2. **Runtime Data Areas**:
   - **Method Area**: Stores class-level data (constants, static variables).
   - **Heap**: Stores all objects and arrays.
   - **JVM Stack**: Stores local variables and partial results for each thread.
   - **PC Registers**: Stores the address of the current instruction being executed.
   - **Native Method Stack**: Stores state for native methods (JNI).
3. **Execution Engine**: Contains the **Interpreter** (reads bytecode), **JIT Compiler** (compiles hot code to native), and **Garbage Collector**.

### Real Use Case
**Application Server Tuning**: In enterprise environments (like Spring Boot on Kubernetes), understanding the Method Area (Metaspace) is crucial for preventing `OutOfMemoryError: Metaspace` errors caused by loading too many dynamic classes.

### Exercise
1. What is the difference between the Method Area and the Heap?
2. Explain the role of the PC (Program Counter) register in a multi-threaded JVM.

---

## Topic: Class Loader Delegation Model

### Deep Explanation
Java uses a hierarchical delegation model to load classes. This ensures security and prevents core classes (like `java.lang.Object`) from being overridden by malicious code.

### Code Example: ClassLoader Hierarchy
```java
public class LoaderCheck {
    public static void main(String[] args) {
        System.out.println("App Loader: " + LoaderCheck.class.getClassLoader());
        System.out.println("Platform Loader: " + LoaderCheck.class.getClassLoader().getParent());
        System.out.println("Bootstrap Loader: " + LoaderCheck.class.getClassLoader().getParent().getParent());
    }
}
```

### Internal Working: The Delegation Hierarchy
1. **Bootstrap Class Loader**: Loads core Java API (`rt.jar` or `java.base`). Written in native code (C++).
2. **Extension (Platform) Class Loader**: Loads classes from `ext` directory.
3. **Application (System) Class Loader**: Loads classes from the environment's Classpath.
**Mechanism**: When asked for a class, a loader first delegates the request to its parent. Only if the parent fails does the loader attempt to find the class itself.

### Real Use Case
**OSGi & Plugin Systems**: Advanced systems like Eclipse or IntelliJ use custom class loaders to allow multiple versions of the same library to coexist in the same JVM without conflicts.

### Exercise
1. Why does the "Bootstrap Class Loader" return `null` in Java code?
2. Research what a "NoClassDefFoundError" is and how it differs from a "ClassNotFoundException".
