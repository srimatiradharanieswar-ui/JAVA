# Section 2: Java Language Mastery

## Module 1: History of Java & Architecture

### Deep Explanation
Java was created by James Gosling at Sun Microsystems in 1995. Its primary goal was "Write Once, Run Anywhere" (WORA), focusing on portability, security, and object-oriented principles.

### Internal Working
- **JDK (Java Development Kit):** The full environment for developing Java apps (Compilers, Debuggers, JRE).
- **JRE (Java Runtime Environment):** The environment for running Java apps (JVM, Core Classes, Supporting Files).
- **JVM (Java Virtual Machine):** The engine that executes bytecode.

### JVM Behavior
The JVM provides a hardware-independent platform. It handles memory management (GC), security checks, and JIT compilation.

### Code Example
```java
// Check Java version
System.out.println(System.getProperty("java.version"));
```

### Interview Questions
- JDK vs JRE vs JVM.
- Why is Java platform independent?

---

## Module 2: Java Program Structure & Compilation

### Deep Explanation
A Java program consists of classes. Every application must have a `main` method as an entry point.

### Compilation Process
1. `Source Code (.java)` -> `javac` compiler -> `Bytecode (.class)`.
2. `Bytecode` -> `JVM` -> `Machine Code`.

### Internal Working of main()
`public static void main(String[] args)`
- `public`: Accessible from outside the class (by the JVM).
- `static`: Can be called without creating an instance of the class.
- `void`: Does not return any value.
- `String[] args`: Command-line arguments.

### Code Example
```java
public class HelloJava {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```

---

## Module 3: Java Basics - Variables, Data Types & Operators

### Deep Explanation
- **Variables:** Named memory locations.
- **Data Types:** Define the type of data (Primitive vs Reference).
- **Operators:** Symbols that perform operations on variables.

### Memory Behavior
- **Primitives** (int, double, char, boolean): Stored directly on the **Stack**.
- **References** (String, Object): The reference is on the **Stack**, the actual object is on the **Heap**.

### Data Types in Java
- `byte` (1 byte), `short` (2), `int` (4), `long` (8)
- `float` (4), `double` (8)
- `char` (2 - UTF-16)
- `boolean` (JVM dependent)

### Code Example
```java
int count = 10; // Primitive on stack
String message = "Hello"; // Reference on stack, object on heap
```

---

## Module 4: Control Flow & Loops

### Deep Explanation
Deciding which path a program takes based on conditions and repeating tasks.

### Internal Working
- `if/else`, `switch`: Conditional branching.
- `for`, `while`, `do-while`: Iterative execution.

### Best Practices
- Use `switch` for multiple discrete values (more readable and sometimes faster due to `tableswitch` or `lookupswitch` bytecode).
- Use `enhanced for-loop` (for-each) for collections.

### Code Example
```java
for (int i = 0; i < 5; i++) {
    if (i % 2 == 0) {
        System.out.println(i + " is even");
    }
}
```

---

## Module 5: Arrays & Strings

### Deep Explanation
- **Arrays:** Fixed-size collections of elements of the same type.
- **Strings:** Objects representing a sequence of characters.

### Memory Behavior
- **Arrays:** Objects stored on the **Heap**.
- **Strings:** In Java, Strings are **Immutable**. They are often stored in the **String Constant Pool** (part of the Heap) to save memory.

### Code Example
```java
int[] numbers = {1, 2, 3};
String s1 = "Java"; // Constant pool
String s2 = new String("Java"); // Forces new object on heap
```

### Exercises
1. Create a program that finds the maximum value in an array.
2. Compare two strings using `==` and `.equals()` and explain the difference.

### Interview Questions
- Why are Strings immutable in Java?
- Difference between `String`, `StringBuilder`, and `StringBuffer`.
