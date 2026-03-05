# Module 8: Android Basics - UI Development

## Topic: Layout System & XML

### Common Layouts
- **LinearLayout**: Elements in a row or column.
- **RelativeLayout**: Elements relative to each other or the parent.
- **ConstraintLayout**: (Preferred) Flexible, high-performance layout.

---

## Topic: RecyclerView & Adapter Pattern

### Concept Explanation
The most efficient way to display a list of data.

### Internal Working: View Recycling
Instead of creating a new View for every item, RecyclerView "recycles" old views that have scrolled off-screen.

### Key Components
- **Adapter**: Binds data to views.
- **ViewHolder**: Holds the references to sub-views for performance.

---

## Topic: View Lifecycle

### Internal Working
1.  **onMeasure**: Determine size.
2.  **onLayout**: Determine position.
3.  **onDraw**: Render pixels.

### Code Example: Custom View
```java
public class MyCircleView extends View {
    @Override
    protected void onDraw(Canvas canvas) {
        super.onDraw(canvas);
        Paint paint = new Paint();
        paint.setColor(Color.RED);
        canvas.drawCircle(100, 100, 50, paint);
    }
}
```

### Exercises
1. Implement a `RecyclerView` that shows a list of names.
2. Explain how to handle item clicks in a `RecyclerView`.
