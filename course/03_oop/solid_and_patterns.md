# Module 3: OOP Deep Dive - SOLID & Design Patterns

## Topic: SOLID Principles

1.  **S - Single Responsibility**
2.  **O - Open/Closed**
3.  **L - Liskov Substitution**
4.  **I - Interface Segregation**
5.  **D - Dependency Inversion**

---

## Topic: Design Patterns

### 1. Singleton Pattern
Ensures a class has only one instance.

### 2. Factory Pattern
Defines an interface for creating an object, but let subclasses decide which class to instantiate.

### 3. Observer Pattern
Defines a one-to-many dependency so that when one object changes state, all its dependents are notified automatically.

---

## Code Example: Singleton (Thread-Safe)
```java
public class DatabaseConnector {
    private static DatabaseConnector instance;
    private DatabaseConnector() {}
    public static synchronized DatabaseConnector getInstance() {
        if (instance == null) instance = new DatabaseConnector();
        return instance;
    }
}
```
