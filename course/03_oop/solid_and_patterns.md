# Module 3: OOP Deep Dive - SOLID & Design Patterns

## Topic: SOLID Principles

### Deep Explanation
SOLID is an acronym for five design principles intended to make software designs more understandable, flexible, and maintainable.
- **S**: Single Responsibility
- **O**: Open/Closed
- **L**: Liskov Substitution
- **I**: Interface Segregation
- **D**: Dependency Inversion

### Code Example: Dependency Inversion
```java
// Bad: High-level module depends on low-level module
class LightBulb { void turnOn() {} }
class Switch {
    private LightBulb bulb = new LightBulb();
    void operate() { bulb.turnOn(); }
}

// Good: Both depend on abstraction
interface Switchable { void turnOn(); }
class Switch {
    private Switchable device;
    Switch(Switchable device) { this.device = device; }
}
```

### Internal Working: Decoupling
By depending on abstractions, the compiled bytecode of the `Switch` class no longer contains a direct symbolic reference to `LightBulb`. This allows the JVM to load any implementation of `Switchable` at runtime without recompiling `Switch`.

### Real Use Case
**Spring Framework**: Spring's Core is essentially a massive implementation of the Dependency Inversion principle, using Dependency Injection to wire components together.

### Exercise
1. Explain the Liskov Substitution Principle using a Square and Rectangle example.
2. How does the Interface Segregation Principle relate to "fat interfaces"?

---

## Topic: Essential Design Patterns (Singleton & Factory)

### Deep Explanation
Design patterns are typical solutions to common problems in software design.

### Code Example: Thread-Safe Singleton
```java
public class DatabaseConnection {
    private static volatile DatabaseConnection instance;
    private DatabaseConnection() {}

    public static DatabaseConnection getInstance() {
        if (instance == null) {
            synchronized (DatabaseConnection.class) {
                if (instance == null) instance = new DatabaseConnection();
            }
        }
        return instance;
    }
}
```

### Internal Working: Double-Checked Locking
The `volatile` keyword is crucial here. It prevents the JVM from reordering the object construction and the assignment to the `instance` variable, ensuring that another thread doesn't see a half-initialized object.

### Real Use Case
**Android System Services**: Services like `LayoutInflater` or `NotificationManager` are accessed as singletons via `context.getSystemService()`.

### Exercise
1. What are the downsides of the Singleton pattern?
2. Implement a Factory pattern for creating different types of UI Buttons.
