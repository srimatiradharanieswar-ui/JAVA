# Section 7: Software Architecture in Java

## Module 1: Clean Architecture

### Deep Explanation
Proposed by Robert C. Martin (Uncle Bob), it focuses on separation of concerns. The goal is to make the system independent of frameworks, UI, and databases.

### Key Layers
1. **Entities:** Business logic.
2. **Use Cases:** Application-specific logic.
3. **Interface Adapters:** Presenters, Controllers.
4. **Frameworks & Drivers:** UI, DB, External APIs.

---

## Module 2: Design Patterns

### 1. Creational Patterns
- **Singleton:** Ensuring only one instance exists.
- **Factory:** Decoupling object creation from use.
- **Builder:** Handling complex object construction.

### 2. Structural Patterns
- **Adapter:** Bridging incompatible interfaces.
- **Proxy:** Controlling access to an object.

### 3. Behavioral Patterns
- **Observer:** One-to-many notifications.
- **Strategy:** Switching algorithms at runtime.

---

## Module 3: Microservices vs Monolith

### Deep Explanation
- **Monolith:** Single deployment unit. Easy to develop but hard to scale.
- **Microservices:** Distributed system. Harder to manage but highly scalable and fault-tolerant.

---

## Module 4: Best Practices & Clean Code

### Principles
- **DRY:** Don't Repeat Yourself.
- **KISS:** Keep It Simple, Stupid.
- **YAGNI:** You Ain't Gonna Need It.

### Interview Questions
- Explain the Singleton pattern and its drawbacks.
- What is Dependency Injection?
- Difference between DAO and Repository patterns.

### Exercise
1. Refactor a messy code snippet using the Strategy pattern.
2. Design a high-level architecture for an E-commerce system.
