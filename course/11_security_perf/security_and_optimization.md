# Module 11: Security & Performance

## Topic: Android App Security & KeyStore

### Deep Explanation
Security is a multi-layered approach in Android. The system uses process isolation, encryption, and the KeyStore to protect user data.

### Code Example: Secure Storage with KeyStore
```java
MasterKey masterKey = new MasterKey.Builder(context)
        .setKeyScheme(MasterKey.KeyScheme.AES256_GCM)
        .build();

SharedPreferences sharedPreferences = EncryptedSharedPreferences.create(
    context, "secret_prefs", masterKey,
    EncryptedSharedPreferences.PrefKeyEncryptionScheme.AES256_SIV,
    EncryptedSharedPreferences.PrefValueEncryptionScheme.AES256_GCM
);
```

### Internal Working: Hardware-Backed Security
The **Android KeyStore** system allows you to store cryptographic keys so they cannot be extracted from the device. On modern devices, keys are stored in a **TEE (Trusted Execution Environment)** or a **Secure Element**, which are isolated from the main Android OS. Even if the kernel is compromised, the keys remain safe.

### Real Use Case
**Banking Apps**: Apps like Chase or Venmo use the KeyStore and BiometricPrompt to ensure that sensitive operations (like sending money) are authorized by the user and protected by hardware-backed encryption.

### Exercise
1. What is the difference between ProGuard and R8?
2. Explain "Certificate Pinning" and why it is used in network security.

---

## Topic: Performance Optimization & Memory Leaks

### Deep Explanation
Performance optimization involves making the app use fewer resources (CPU, Memory, Battery) while remaining responsive to user input.

### Code Example: Detecting Leaks
```java
// Bad: Static reference to an Activity
public class MySingleton {
    private static Activity leakedActivity; // This causes a leak!
    public static void setActivity(Activity activity) { leakedActivity = activity; }
}
```

### Internal Working: GC Roots & Reachability
A memory leak occurs when an object is no longer needed but is still reachable from a **GC Root** (like a static variable or a running thread). The Garbage Collector cannot reclaim the memory, eventually leading to an `OutOfMemoryError`.

### Real Use Case
**Large-Scale Apps**: Developers at Facebook and Instagram use custom "LeakCanary" integrations to detect and fix memory leaks during the development process, ensuring the app doesn't slow down over time.

### Exercise
1. Explain how "Overdraw" affects UI performance.
2. How do you use the Android Studio Profiler to find a memory leak?

---

## Topic: App Startup Optimization

### Deep Explanation
App startup time is a critical metric for user retention. There are three types of starts: Cold, Warm, and Hot.

### Internal Working: Cold Start Pipeline
1. **OS level**: Load the process, start Zygote.
2. **App level**: Initialize the Application object, start the ActivityThread.
3. **UI level**: Inflate the layout, measure, and perform the first draw.
**Optimization**: Using the **Baseline Profiles** tool allows the Google Play Store to pre-compile the bytecode into native code for the most frequent startup paths, reducing "Cold Start" time by up to 30%.

### Real Use Case
**Gaming & Media Apps**: Large apps (like Disney+) use splash screens and "Lazy Initialization" of heavy libraries to ensure the user sees the first frame of the UI as quickly as possible.

### Exercise
1. What is the difference between a Cold start and a Hot start?
2. How does "Lazy Initialization" help with app startup performance?
