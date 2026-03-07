# Module 10: Advanced Android Engineering - Library Internals

## Topic: Hilt / Dagger Code Generation

### Deep Explanation
Hilt is a Dependency Injection (DI) library for Android that reduces the boilerplate of manual DI. It is built on top of Dagger.

### Code Example: Hilt Injection
```java
@AndroidEntryPoint
public class MainActivity extends AppCompatActivity {
    @Inject AnalyticsService analytics;
}
```

### Internal Working: Annotation Processing
Hilt uses an **Annotation Processor** to generate code at compile-time.
1. **Factories**: For every `@Inject` class, Hilt generates a `Factory` that knows how to instantiate it.
2. **MembersInjectors**: For Android components (Activities), it generates a `MembersInjector` to set fields since the OS creates the Activity instance.
**Benefit**: Because code is generated at compile-time, there is zero reflection overhead, making it faster than runtime DI libraries.

### Real Use Case
**Large-Scale Modular Apps**: Companies like Uber use Dagger/Hilt to manage dependencies across hundreds of modules, ensuring that components are decoupled and testable.

### Exercise
1. Look at the `build/generated` folder in an Android project and find a Hilt `Factory` class.
2. Explain the difference between `@Provides` and `@Binds` in Dagger.

---

## Topic: Room Query Plans & SQLite

### Deep Explanation
Room is a persistence library that provides an abstraction layer over SQLite. It provides compile-time verification of SQL queries.

### Code Example: Room DAO
```java
@Dao
public interface UserDao {
    @Query("SELECT * FROM user WHERE id = :userId")
    LiveData<User> getById(String userId);
}
```

### Internal Working: The Implementation Generator
At compile-time, Room:
1. **Validates SQL**: It checks queries against the schema. If a column is missing, the build fails.
2. **Generated Code**: Room generates an implementation (`UserDao_Impl`) that handles opening cursors, mapping rows to Java objects, and switching to background threads.

### Real Use Case
**Offline-First Apps**: Apps like Evernote use Room to store all user data locally. When the user is offline, the app continues to work using the local SQLite cache managed by Room.

### Exercise
1. What is a "Migration" in Room and why is it necessary?
2. Explain how Room's `LiveData` integration works under the hood.

---

## Topic: Retrofit Dynamic Proxies

### Deep Explanation
Retrofit is a type-safe HTTP client for Android and Java. It allows you to define API endpoints as interfaces.

### Code Example: Retrofit Interface
```java
public interface ApiService {
    @GET("users/{id}")
    Call<User> getUser(@Path("id") String id);
}
```

### Internal Working: java.lang.reflect.Proxy
When you call `retrofit.create(ApiService.class)`:
1. Retrofit creates a **Dynamic Proxy** at runtime.
2. When you call `api.getUser()`, the proxy's `InvocationHandler` intercepts the call.
3. Retrofit reads the annotations (`@GET`), builds an OkHttp request, executes it, and converts the JSON response using a converter (like Gson).

### Real Use Case
**Modern Mobile APIs**: Almost every major Android app (Twitter, Netflix) uses Retrofit to communicate with their backend services due to its ease of use and high performance.

### Exercise
1. Why does Retrofit use Dynamic Proxies instead of code generation?
2. What is the role of an `Interceptor` in OkHttp?
