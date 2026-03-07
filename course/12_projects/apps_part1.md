# Module 12: Real World Projects - Part 1

## Project 1: Notes Application (MVVM + Room)

### Deep Explanation
This project focuses on the core Android Jetpack components. It demonstrates how to build a robust, persistent application using the recommended MVVM architecture.

### Code Example: Note Entity
```java
@Entity(tableName = "note_table")
public class Note {
    @PrimaryKey(autoGenerate = true)
    private int id;
    private String title;
    private String description;
}
```

### Internal Working: Reactive UI Flow
1. The **View** (Activity) observes **LiveData** from the **ViewModel**.
2. The **ViewModel** requests data from the **Repository**.
3. The **Repository** fetches data from the **Room DAO**.
4. When the database updates, Room automatically notifies the LiveData, which triggers a UI refresh in the Activity.

### Real Use Case
**Task Management**: This architecture is the foundation of every productivity app (like Todoist or Microsoft To Do), ensuring data is always in sync and survives app restarts.

### Exercise
1. Implement a search feature that filters the notes list in real-time.
2. Add a "Priority" field to the Note entity and sort the notes by priority.

---

## Project 2: Secure DNS App (VpnService)

### Deep Explanation
This project explores system-level Android development. It shows how to use the `VpnService` API to intercept and secure network traffic.

### Code Example: VpnService Setup
```java
public class MyVpnService extends VpnService {
    @Override
    public int onStartCommand(Intent intent, int flags, int startId) {
        Builder builder = new Builder();
        builder.addAddress("10.0.0.2", 32);
        builder.addRoute("0.0.0.0", 0);
        builder.establish();
        return START_STICKY;
    }
}
```

### Internal Working: Packet Interception
The `VpnService` creates a virtual network interface (TUN). All outgoing IP packets are routed to this interface. The app reads raw packets from a file descriptor, modifies them (e.g., encrypting DNS requests), and then forwards them to a real network socket.

### Real Use Case
**Privacy & Security**: Apps like "1.1.1.1" (Cloudflare) use this technique to provide DNS-over-HTTPS (DoH) for all apps on the device, preventing ISPs from tracking user browsing history.

### Exercise
1. Explain why a "Foreground Service" is necessary for a VPN app.
2. What are the battery implications of processing every network packet in Java?
