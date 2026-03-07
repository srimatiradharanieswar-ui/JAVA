# Module 8: Android Development - UI Development

## Topic: View System & Layouts

### Deep Explanation
The Android View system is a tree structure of UI components. Each component (`View`) is responsible for measuring, laying out, and drawing itself.

### Code Example: Custom View Drawing
```java
@Override
protected void onDraw(Canvas canvas) {
    super.onDraw(canvas);
    canvas.drawCircle(centerX, centerY, radius, paint);
}
```

### Internal Working: The UI Loop
1. **Measure**: The system traverses the view tree to determine how large each view wants to be.
2. **Layout**: The system determines the coordinates for each view.
3. **Draw**: Each view draws itself onto a `Canvas`.
**Optimization**: The system uses a **Display List** to record drawing commands, which allows the GPU to redraw the UI at 60 (or 120) FPS without re-executing the Java `onDraw` logic every time.

### Real Use Case
**Custom Analytics Dashboards**: Many financial apps use custom Views to draw high-performance charts and graphs that are more efficient than nesting dozens of standard XML views.

### Exercise
1. What is the difference between `View.GONE` and `View.INVISIBLE`?
2. Explain the "View Holder" pattern in RecyclerView.

---

## Topic: Jetpack Compose (Modern UI)

### Deep Explanation
Jetpack Compose is a modern, declarative UI toolkit. Instead of modifying XML views, you describe what the UI should look like based on the current state.

### Code Example: Composable Function
```kotlin
@Composable
fun Greeting(name: String) {
    Text(text = "Hello $name")
}
```

### Internal Working: Recomposition
When state changes, Compose re-executes only the functions whose inputs have changed. This process is called **Recomposition**. It uses a sophisticated "Gap Buffer" data structure (the Slot Table) to efficiently track and update the UI tree.

### Real Use Case
**Rapid Prototyping**: Modern apps (like the New York Times) have transitioned to Compose to speed up UI development and reduce the amount of boilerplate code.

### Exercise
1. What is "State Hoisting" in Jetpack Compose?
2. How does Compose's declarative approach differ from the imperative XML approach?
