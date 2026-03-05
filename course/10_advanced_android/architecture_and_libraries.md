# Module 10: Advanced Android Engineering

## Topic: Architecture (MVVM + Repository)

### Concept Explanation
The modern standard for building scalable Android apps.
- **ViewModel**: Acts as a bridge between the View and the Model. Survivors rotation.
- **Repository**: Single source of truth. Decides whether to fetch data from the Network (Retrofit) or the Local DB (Room).

### Why It Exists
To make code testable and maintainable. The View (Activity) only cares about observing data, not how it's fetched.

---

## Topic: Dependency Injection (Dagger/Hilt)

### Concept Explanation
Hilt is the recommended DI library for Android (built on top of Dagger).

### Why It Exists
Managing object dependencies manually leads to "Boilerplate Hell." Hilt automates this and provides predefined scopes for Android components (`ActivityComponent`, `ViewModelComponent`).

---

## Topic: Room Persistence Library

### Concept Explanation
An abstraction layer over SQLite.

### Key Components
1.  **Entity**: Represents a database table (`@Entity`).
2.  **DAO (Data Access Object)**: Contains methods used for accessing the database (`@Dao`).
3.  **Database**: The main entry point for the underlying connection (`@Database`).

---

## Topic: Networking with Retrofit

### Concept Explanation
A type-safe HTTP client for Android and Java.

### Internal Working
Retrofit uses **Reflection** and **Dynamic Proxies** to convert an interface into a network caller. It uses **OkHttp** for the actual connection and **Gson** or **Moshi** for JSON parsing.

### Code Example: Retrofit Interface
```java
public interface ApiService {
    @GET("users/{id}")
    Call<User> getUser(@Path("id") String userId);
}
```

### Exercises
1. What is the difference between `LiveData` and `StateFlow`?
2. Implement a simple Room DAO for a "Task" entity.
