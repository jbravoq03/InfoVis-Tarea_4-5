## Interactive Bar Chart Example

This example demonstrates **ODViz (Open Data Visualization)**—a lightweight format that embeds tabular data directly inside an SVG document. A bar chart and a synchronized data table are paired together, showing how to make data visualizations interactive and self‑contained.

**Online Example:** [Open Data Visualization Example](https://arce.github.io/odviz-example/)

### Interactive Features

The page includes a simple **interactive viewer** with these capabilities:

| Feature | Description |
|---------|-------------|
| **Zoom** | Scroll with the mouse wheel to zoom in and out of the SVG chart. |
| **Pan** | Click and drag to move around the zoomed‑in view. |
| **Selection** | Click on a bar in the chart to automatically highlight its row in the data table. |
| **Table Selection** | Click on a row in the table to select the corresponding bar in the chart. |
| **Reset** | Double‑click the SVG to restore the original view. |

> The selection color is `red`, and the linking between the chart and table is **bidirectional** thanks to the underlying ODViz data model.

### How to Use

1. **Clone or download** the repository.
2. **Serve the files** using any local web server (e.g., `python -m http.server 8000`).
3. **Open `index.html`** in a modern web browser.
4. **Experiment** with zoom, pan, and selection to see the bidirectional linking in action.

> **Note:** The example relies on SVG’s `object` tag and `contentDocument`; therefore, it must be served over HTTP(S) – **not** opened directly from the file system.

### File Structure

```
odviz/
├── bart-chart.svg       # SVG bar chart with embedded data
├── index.html           # Main HTML page with the split layout
├── simple-table.css     # Styles for the interactive data table
├── simple-table.js      # Table component (filtering, sorting, selection)
├── svg-controls.js      # SVG interactivity (zoom, pan, selection)
└── README.md            # This file
```

### 🔧 Implementation Details

| Component | Description |
|-----------|-------------|
| **ODViz format** | The SVG file (`bart-chart.svg`) uses the `v:` namespace to embed a `<v:table>` element containing CSV data and metadata. The `<v:row>` elements have unique `id` attributes, and each bar references its row via an `href="#row-id"` attribute. |
| **Interaction** | `svg-controls.js` handles zoom, pan, and selection within the SVG. When a bar is clicked, it triggers a selection in the table, and vice‑versa. |
| **Data Table** | `simple-table.js` renders the data from the SVG’s `<v:table>` into an interactive HTML table that supports sorting, column filtering, and row selection. |
| **Layout** | `index.html` uses `Split.js` to create a resizable vertical split between the SVG and the table. |

### Extending the Example

The same ODViz structure can be used for other types of visualizations, such as:

- **Choropleth maps** – geographical data with region‑based colors.
- **Network graphs** – nodes and edges stored in separate, related tables.
- **Radial trees** – hierarchical data displayed in a radial layout.

Simply replace the `bart-chart.svg` file with any ODViz‑compliant SVG, and the interactive viewer will automatically adapt to the new data and visual elements.

---

### Learn More

- **Project Page:** [ODViz – Open Data Visualization](https://arce.github.io/odviz/)
- **GitHub Repository:** [github.com/arce/odviz](https://github.com/arce/odviz)

- **Simple Table Library:** [arce.github.io/simple-table/](https://arce.github.io/simple-table/)
- **SVG Controls Library:** [arce.github.io/svg-controls/](https://arce.github.io/svg-controls/)

---

*This example is part of the **Open Data Science** ecosystem, promoting transparency, reproducibility, and interoperability in data analysis.*