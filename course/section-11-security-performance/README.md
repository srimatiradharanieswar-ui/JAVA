# Section 11: Security & Performance

## Module 1: Android Security

### Deep Explanation
1. **Encryption:** Using the Android Keystore system to protect cryptographic keys.
2. **Network Security:** Using HTTPS (TLS) and Certificate Pinning.
3. **App Sandboxing:** Understanding UID-based process isolation.

---

## Module 2: Performance Optimization

### 1. Memory Management
- **Memory Leaks:** Common cause: holding a reference to an Activity in a static field or background task.
- **Tools:** LeakCanary, Android Profiler.

### 2. UI Performance
- Avoid overdraw.
- Keep the main thread free from heavy work (ANR - Application Not Responding).

### 3. Battery Optimization
- Use WorkManager for background jobs.
- Reduce network requests.

---

## Module 3: Profiling

### Deep Explanation
Using the **Android Studio Profiler** to monitor:
- **CPU:** Identifying bottlenecks.
- **Memory:** Finding leaks and churn.
- **Network:** Inspecting payloads.

---

## Interview Questions
- How do you detect memory leaks in Android?
- What is ProGuard/R8?
- Explain the importance of the Android Keystore.
- What is an ANR and how do you fix it?

### Exercise
1. Use the Android Profiler to analyze the memory usage of an app and identify any potential leaks.
