# Module 11: Security & Performance

## Topic: Android App Security

### 1. App Sandboxing
**Concept**: Every Android app runs in its own Linux process with a unique User ID (UID). An app cannot access another app's memory or files without permission.

### 2. Encryption
- **EncryptedSharedPreferences**: Encrypts keys and values.
- **KeyStore**: A system-level service that stores cryptographic keys so they cannot be extracted from the device.

### 3. Network Security
- **HTTPS/TLS**: Required for all network traffic (Android 9.0+).
- **Certificate Pinning**: Ensures the app only communicates with a specific, trusted server.

---

## Topic: Performance Optimization

### 1. Memory Profiling
**Concept**: Using Android Studio Profiler to find **Memory Leaks**.
**Internal Working**: A leak happens when an object is held in memory by a "GC Root" (e.g., a static reference to an Activity) after its lifecycle has ended.

### 2. Battery Optimization
Avoid waking the device frequently. Use **WorkManager** to batch tasks.

### 3. UI Optimization
- **Overdraw**: Occurs when the system draws the same pixel multiple times in a single frame.
- **R8/ProGuard**: Shrinks and obfuscates bytecode to reduce app size and protect source code.

---

## Topic: App Startup Optimization

### Concept Explanation
- **Cold Start**: App starts from scratch.
- **Warm Start**: App is in memory but needs to re-create Activities.
- **Hot Start**: App is already in the foreground.

### Code Example: Secure Storage
```java
MasterKey masterKey = new MasterKey.Builder(context)
        .setKeyScheme(MasterKey.KeyScheme.AES256_GCM)
        .build();

SharedPreferences sharedPreferences = EncryptedSharedPreferences.create(
    context,
    "secret_shared_prefs",
    masterKey,
    EncryptedSharedPreferences.PrefKeyEncryptionScheme.AES256_SIV,
    EncryptedSharedPreferences.PrefValueEncryptionScheme.AES256_GCM
);
```

### Exercises
1. What is the difference between ProGuard and R8?
2. Explain how to detect a memory leak using LeakCanary.
