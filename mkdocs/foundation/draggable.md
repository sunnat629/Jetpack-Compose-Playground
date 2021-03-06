# Draggable 

https://developer.android.com/reference/kotlin/androidx/ui/foundation/gestures/package-summary#draggable

<p align="left">
  <img src ="../../images/DraggableDemo.png" height=500 />
</p>

```kotlin

@Composable
fun DraggableSample() {

    val max = 300.dp
    val min = 0.dp
    val (minPx, maxPx) = with(DensityAmbient.current) {
        min.toPx().value to max.toPx().value
    }
    var position by state { 0f }

    Box(
        modifier = Modifier
            .draggable(dragDirection = DragDirection.Horizontal) { delta ->
                // consume only delta that needed if we hit bounds
                val old = position
                position = (position + delta).coerceIn(minPx, maxPx)
                position - old
            }
    ) {
        Column {
            Text("Drag me ",modifier = Modifier.padding(start = position.dp))
            Text("Dragvalue: "+position.dp)
        }

    }
}
```