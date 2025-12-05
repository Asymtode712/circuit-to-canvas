# circuit-to-canvas

Draw [Circuit JSON](https://github.com/tscircuit/circuit-json) into a Canvas- works with any canvas object (Node/Vanilla)

```tsx
const drawer = new CircuitToCanvasDrawer(canvasOrCanvasRenderingContext2d)

// Sets the internal transformation matrix for all operations
drawer.setCameraBounds({ minX: 0, maxX: 100, minY: 0, maxY: 100 })

drawer.configure({
  colorOverrides: {
    topCopper: "#ff0000"
  }
})

drawer.drawElement(pcbPlatedHole, {
  layers: ["top_copper"]
})



drawer.drawCopper(circuitJsonArray, { layers: ["top"] })

// Draws all layers by default, soldermask etc.
drawer.drawCircuitJson(circuitJsonArray)
```

## Implementation Notes

There are two "types" of layers:

- Specific drawing layers e.g. "top_copper"
- Layer groups "top" (includes "top_copper", "top_soldermask")

inner layers go by the name inner1, inner2 etc.
