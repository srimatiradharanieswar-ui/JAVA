# Module 2: Java Language Mastery - Fundamentals

## Topic: History & Philosophy of Java

### Concept Explanation
Java was created by James Gosling at Sun Microsystems in 1995. Its core philosophy is **WORA**: "Write Once, Run Anywhere."

### Why It Exists
Before Java, programs were platform-specific. A program compiled for Windows wouldn't run on Mac or Linux. Java solved this by introducing an intermediate layer.

### Internal Working: JDK vs JRE vs JVM
- **JVM (Java Virtual Machine)**: The engine that runs bytecode on a specific OS.
- **JRE (Java Runtime Environment)**: JVM + Libraries. Required to *run* Java apps.
- **JDK (Java Development Kit)**: JRE + Tools (Compiler, Debugger). Required to *develop* Java apps.

### Memory Behavior
The JVM manages memory automatically. When the JDK compiles a file, it checks for syntax and type safety before generating Bytecode.

### JVM Behavior: Compilation Process
1.  **Source Code**: `.java` files.
2.  **Compiler (`javac`)**: Converts source to Bytecode (`.class`).
3.  **Class Loader**: Loads bytecode into JVM memory.
4.  **Bytecode Verifier**: Ensures code doesn't violate security or memory rules.
5.  **Interpreter/JIT**: Converts bytecode to native machine code.

---

## Topic: Java Program Structure & main() Method

### Concept Explanation
Every Java program must have at least one class and a entry point called the `main` method.

### Code Example
```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello World!");
    }
}
```

### Internal Working
When you run `java HelloWorld`, the JVM looks specifically for the signature `public static void main(String[] args)`. Without `static`, the JVM would need to instantiate the class first, which creates a "chicken and egg" problem for the entry point.

### Common Mistakes
- Forgetting to name the file exactly like the public class (`HelloWorld.java`).
- Missing `static` in the `main` method.

### Exercises
1. Compile and run a program that prints your name using the terminal.
2. Explain what happens if you change `public` to `private` in the `main` method.
