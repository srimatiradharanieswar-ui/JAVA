# Module 3: OOP Deep Dive - Advanced Concepts

## Topic: Interfaces vs Abstract Classes

### Deep Explanation
Abstract classes allow you to create a partial implementation that subclasses can complete, while interfaces define a strict contract that a class must fulfill. Since Java 8, interfaces can also have default and static methods.

### Code Example: Abstract Class vs Interface
```java
abstract class Database {
    abstract void connect();
    void log(String msg) { System.out.println("Log: " + msg); }
}

interface Encryptable {
    default void encrypt() { System.out.println("Encrypting..."); }
}
```

### Internal Working: Method Resolution
Abstract class methods are resolved via the **vtable** (just like normal classes). Interface methods are resolved via an **itable** (Interface Table). Finding a method in an itable is slightly slower than a vtable because a class can implement multiple interfaces, requiring a search.

### Real Use Case
**Plugin Architectures**: Interfaces are used to define plugins. The main application doesn't know the implementation details, only that the plugin "can-do" the tasks defined in the interface.

### Exercise
1. When should you prefer an abstract class over an interface?
2. How did the introduction of `default` methods in Java 8 affect the "diamond problem"?

---

## Topic: Composition vs Inheritance

### Deep Explanation
Inheritance (`is-a`) is a powerful tool but often leads to rigid and fragile class hierarchies. Composition (`has-a`) allows for greater flexibility by combining simple objects to create complex behavior.

### Code Example: Composition in Action
```java
class Engine { void start() { } }
class Car {
    private final Engine engine = new Engine(); // Composition
    void start() { engine.start(); }
}
```

### Internal Working: Memory & Linking
Inheritance creates a strong link at the bytecode level (`extends` attribute). Composition is just a reference to another object on the heap. This makes composed objects easier to mock during testing and easier to swap at runtime.

### Real Use Case
**Strategy Pattern**: Instead of having `SortableArrayList` and `SortableLinkedList`, you have a `List` that *has-a* `SortStrategy`. This is composition.

### Exercise
1. Why is "favor composition over inheritance" a core design principle?
2. Refactor a deep inheritance hierarchy into a composition-based design.
