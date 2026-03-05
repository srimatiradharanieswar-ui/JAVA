# Module 7: Software Architecture - Patterns & Principles

## Topic: Clean Architecture (The Internal Layers)

### Concept Explanation
Clean Architecture is about the **Separation of Concerns**.

### Internal Working: The Circle Layers
1.  **Entities (Core)**: Pure business logic and data objects. Zero dependencies on libraries.
2.  **Use Cases (Interactors)**: Application-specific business rules.
3.  **Interface Adapters**: Presenters, ViewModels, and Gateways (Repositories).
4.  **Frameworks & Drivers**: The Web, Database, UI, Android OS.

### The Dependency Rule
Inner layers cannot know anything about outer layers. `Entity` cannot have an `import android.os.Bundle;`.

---

## Topic: Dependency Injection (DI) Internals

### Concept Explanation
DI is about giving an object what it needs, rather than letting it create it.

### Internal Working: Service Locator vs DI
- **Service Locator**: The object "asks" for a dependency: `locator.get(Service.class)`. This hides dependencies and is hard to test.
- **DI**: The dependency is "given" via the constructor. This is transparent and easy to mock.

### Real World Use Case: Unit Testing
By using DI, you can inject a `MockWebServer` into your `Repository`, allowing you to test network error handling without actually being online.

---

## Topic: Modern Architectural Patterns (MVI)

### Concept Explanation
**MVI (Model-View-Intent)** is the evolution of MVVM.
- **Intent**: An action from the user.
- **State**: A single immutable object representing the entire screen UI.
- **Effect**: One-time events like showing a Snackbar or Navigating.

### Why It Exists
To solve the "State Explosion" problem where different parts of the UI get out of sync. With MVI, there is a **Unidirectional Data Flow (UDF)**.

### Exercises
1. Refactor a "God Activity" into MVVM.
2. Explain why "Program to an Interface, not an Implementation" is the core of most design patterns.
