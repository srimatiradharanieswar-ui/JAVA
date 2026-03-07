# Module 8: Android Development - Core Components

## Topic: The Four Pillars of Android

### Deep Explanation
Every Android app is built using four main components: Activities, Services, Broadcast Receivers, and Content Providers. These are managed by the Android system through Intents.

### Code Example: Declaring an Activity
```xml
<activity android:name=".MainActivity"
          android:exported="true">
    <intent-filter>
        <action android:name="android.intent.action.MAIN" />
        <category android:name="android.intent.category.LAUNCHER" />
    </intent-filter>
</activity>
```

### Internal Working: The Manifest
The `AndroidManifest.xml` is the "contract" between your app and the OS. When you install an app, the **Package Manager Service** parses this file to know which components your app has and which permissions it requires.

### Real Use Case
**Deep Linking**: By defining a custom `intent-filter` in the manifest, your app can respond to specific web URLs (e.g., clicking an Instagram link opens the Instagram app instead of the browser).

### Exercise
1. What is the difference between an "Explicit Intent" and an "Implicit Intent"?
2. Why must all core components be declared in the Manifest?

---

## Topic: Services & Background Processing

### Deep Explanation
A Service is a component that performs long-running operations in the background without a UI.

### Code Example: Foreground Service
```java
public class MyService extends Service {
    @Override
    public int onStartCommand(Intent intent, int flags, int startId) {
        // Must show notification for Foreground Service
        startForeground(NOTIFICATION_ID, notification);
        return START_STICKY;
    }
}
```

### Internal Working: Service Lifecycle
Unlike Activities, Services do not have a UI. However, they still run on the **Main Thread** by default. To perform heavy tasks, you must create a separate background thread within the service.

### Real Use Case
**Music Players**: Apps like Spotify use Foreground Services to continue playing music even when the user switches to another app or locks the screen.

### Exercise
1. What is a "Bound Service" and when would you use one?
2. Explain why a Service is killed by the OS under memory pressure even if it's currently working.
