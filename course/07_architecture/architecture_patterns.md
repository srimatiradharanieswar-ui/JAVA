# Module 7: Software Architecture in Java

## Topic: Clean Architecture & SOLID in Java

### Deep Explanation
Clean Architecture, proposed by Robert C. Martin, aims to create a system that is independent of frameworks, UI, and external agencies. It organizes the system into concentric layers where dependencies only point inwards.

### Code Example: Use Case Layer
```java
public class GetUserUseCase {
    private final UserRepository repository; // Interface
    public GetUserUseCase(UserRepository repository) { this.repository = repository; }

    public User execute(String id) {
        return repository.findById(id);
    }
}
```

### Internal Working: Dependency Inversion
The core business logic (Entities and Use Cases) defines interfaces for the data it needs. The outer layers (Frameworks and Drivers) implement these interfaces. This is the **Dependency Inversion Principle** in action, ensuring the core doesn't depend on the database or UI.

### Real Use Case
**Enterprise Backend Systems**: Large-scale Java applications (using Spring Boot) use Clean Architecture to ensure that if they decide to switch from PostgreSQL to MongoDB, the core business logic remains untouched.

### Exercise
1. Draw a diagram of the Clean Architecture layers.
2. Why is the "Domain" layer often referred to as the "purest" part of the application?

---

## Topic: Architecture Patterns (MVC, MVP, MVVM)

### Deep Explanation
These patterns separate the UI (View) from the logic (Model) to improve testability and maintainability.

### Code Example: MVVM with ViewModel
```java
public class UserViewModel {
    private User model;
    private View view; // In Android, this would be LiveData/State

    public void onLoginClicked() {
        if (model.isValid()) {
            // Update UI
        }
    }
}
```

### Internal Working: Data Binding
In MVVM, the View and ViewModel are often linked via Data Binding. The ViewModel doesn't have a direct reference to the View; instead, it exposes observables. When the ViewModel's state changes, the View automatically updates itself by observing these changes.

### Real Use Case
**Android Development**: Google recommends MVVM as the standard architecture for Android apps, using Jetpack Compose or XML with LiveData/StateFlow to handle the reactive UI updates.

### Exercise
1. Compare and contrast MVP (Model-View-Presenter) and MVVM (Model-View-ViewModel).
2. What is "State Hoisting" and how does it relate to these patterns?
