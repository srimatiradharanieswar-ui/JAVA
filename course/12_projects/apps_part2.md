# Module 12: Real World Projects - Part 2

## Project 3: File Manager (Scoped Storage)

### Deep Explanation
This project covers the complexities of the Android file system, focusing on the modern "Scoped Storage" model introduced in Android 10+.

### Code Example: Storage Access Framework
```java
Intent intent = new Intent(Intent.ACTION_OPEN_DOCUMENT_TREE);
startActivityForResult(intent, REQUEST_CODE);
```

### Internal Working: DocumentProvider
Android uses the **DocumentsUI** system process to handle file picking. When a user selects a folder, the system grants your app a persistent URI permission. Your app then uses a `ContentResolver` to list and modify files within that folder without needing broad "Read External Storage" permissions.

### Real Use Case
**File Explorers**: Modern file managers (like Files by Google) use Scoped Storage to ensure user privacy while still allowing the user to manage their downloads and media files across different apps.

### Exercise
1. What is the difference between "Internal Storage" and "External Storage" in Android?
2. Implement a feature that displays the MIME type (e.g., image/jpeg) of a selected file.

---

## Project 4: Real-time Chat (WebSockets)

### Deep Explanation
This project demonstrates how to build a real-time communication system using WebSockets and background services.

### Code Example: WebSocket Listener
```java
OkHttpClient client = new OkHttpClient();
Request request = new Request.Builder().url("ws://chat.example.com").build();
WebSocket ws = client.newWebSocket(request, new WebSocketListener() {
    @Override
    public void onMessage(WebSocket webSocket, String text) {
        // Handle incoming message
    }
});
```

### Internal Working: Connection Management
Unlike HTTP, which is request-response, a WebSocket is a persistent, two-way connection. The app must handle "Heartbeats" (Pings/Pongs) to ensure the connection is still alive and automatically reconnect if the network drops.

### Real Use Case
**Collaborative Tools**: Apps like Slack or Microsoft Teams use WebSockets to provide instant messaging and "typing..." indicators, ensuring a seamless real-time experience.

### Exercise
1. Why are WebSockets better than "Polling" for a chat application?
2. How would you handle incoming messages when the app is in the background?

---

## Project 5: Offline-First App (Sync Strategy)

### Deep Explanation
This project teaches advanced data synchronization patterns, ensuring the app works perfectly even without an internet connection.

### Internal Working: The Repository Pattern
The Repository acts as the "Single Source of Truth."
1. **Request**: UI asks for data.
2. **Local First**: Repository returns data from the local Room database immediately.
3. **Remote Fetch**: In the background, it fetches fresh data from the API.
4. **Update**: It saves the new data to Room, which automatically updates the UI.

### Real Use Case
**Field Service Apps**: Apps used by technicians in remote areas (like utility workers) must allow them to perform work offline and then "Sync" all changes back to the server once they return to an area with connectivity.

### Exercise
1. Explain the "Conflict Resolution" problem in data synchronization.
2. Implement a "Sync Status" indicator (e.g., a cloud icon) in the UI.
