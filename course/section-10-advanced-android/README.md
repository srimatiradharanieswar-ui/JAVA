# Section 10: Advanced Android Engineering

## Module 1: MVVM Architecture

### Deep Explanation
Model-View-ViewModel is the standard architecture for modern Android apps.
- **Model:** Data layer (Repository, Room, Retrofit).
- **View:** UI (Activity/Fragment).
- **ViewModel:** Stores UI-related data and survives configuration changes.

### Internal Working
Uses **LiveData** or **Flow** for data observation. The View observes the ViewModel, which in turn fetches data from the Model.

---

## Module 2: Dependency Injection (DI)

### Deep Explanation
Providing dependencies to a class rather than the class creating them itself.
**Tools:** Dagger2 or Hilt (Hilt is built on top of Dagger).

### Why it exists
- Decoupling.
- Easier testing (Mocking dependencies).

---

## Module 3: Local Persistence with Room

### Deep Explanation
Room is an abstraction layer over SQLite.
**Components:**
1. **Entity:** Table schema.
2. **DAO:** Data Access Object (SQL queries).
3. **Database:** Main entry point.

### Internal Working
Uses Annotation Processing to generate implementation code at compile time.

---

## Module 4: Networking with Retrofit

### Deep Explanation
A type-safe HTTP client for Android.
**Internal Working:** Uses **Dynamic Proxies** (Reflection) to turn Java interfaces into REST API calls.

### Code Example
```java
public interface ApiService {
    @GET("users")
    Call<List<User>> getUsers();
}
```

---

## Module 5: Modern UI (Jetpack Compose - Overview)

### Deep Explanation
While this course focuses on Java, Jetpack Compose is the future of Android UI. It is declarative, meaning you describe the UI state rather than the UI steps.

---

## Interview Questions
- Why use ViewModel instead of just saving state in Activity?
- What is the difference between LiveData and MutableLiveData?
- Explain the Repository pattern.
- How does Dagger/Hilt work at compile time?

### Exercise
1. Implement a simple app that fetches data from a public API using Retrofit and displays it in a RecyclerView using MVVM.
