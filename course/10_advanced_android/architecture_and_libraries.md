# Module 10: Advanced Android Engineering - Library Internals

## Topic: Hilt / Dagger Code Generation

### Concept Explanation
Dependency Injection libraries like Hilt aren't just "Magic." They generate regular Java code to handle object creation.

### Internal Working: Annotation Processing
When you use `@Inject` or `@Module`, Hilt runs an **Annotation Processor** during compilation.
1.  **Factories**: For every class with `@Inject`, Hilt generates a `Factory` class that knows how to call `new MyClass(deps)`.
2.  **MembersInjectors**: For Activities/Fragments, Hilt generates a `MembersInjector` that sets the fields of your Activity since the system (AMS) creates the Activity instance, not Hilt.
3.  **Hilt_MainActivity**: Hilt actually creates a hidden base class that your Activity extends to perform the injection during `onCreate()`.

### Performance Behavior
Because Hilt generates code at **Compile-Time**, there is zero reflection overhead at runtime, making it significantly faster than libraries like Guice.

---

## Topic: Room Query Plans & SQLite

### Concept Explanation
Room is more than an ORM; it's a sophisticated SQL verification engine.

### Internal Working: The Generator
At compile-time, Room:
1.  **Validates SQL**: It checks your `@Query` strings against the database schema. If you mistype a column name, the app **won't compile**.
2.  **Generated Implementation**: Room creates a class (`MyDao_Impl`) that handles all the boilerplate:
    - Opening/Closing cursors.
    - Converting Cursor rows into Java Objects.
    - Handling Threading (Ensuring Room doesn't run on the Main Thread).

### Advanced: FTS (Full-Text Search)
Room supports SQLite's **FTS4/FTS5** modules for extremely fast text searching across millions of records.

---

## Topic: Retrofit Dynamic Proxies

### Concept Explanation
How does Retrofit implement an interface you only defined?

### Internal Working: `java.lang.reflect.Proxy`
When you call `retrofit.create(ApiService.class)`:
1.  Retrofit creates a **Dynamic Proxy** at runtime.
2.  When you call `api.getUser()`, the Proxy's `InvocationHandler` catches the call.
3.  Retrofit looks at the annotations (`@GET`), builds an OkHttp request, executes it, and parses the result using Gson/Moshi.

### Best Practices
- Use `@Binds` instead of `@Provides` in Hilt to reduce code generation size.
- Always use `EXPLAIN QUERY PLAN` for complex Room queries to identify slow table scans.

### Exercises
1. Look at the `build/generated` folder in an Android project and find a Hilt `Factory` class.
2. Explain the difference between `@Component` and `@Module` in Dagger/Hilt.
