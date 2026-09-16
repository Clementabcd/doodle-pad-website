# Doodle Pad

A native macOS drawing and painting application built with SwiftUI and Core Graphics.

## Features

- **Freehand Drawing** — Smooth bezier strokes with configurable width, opacity, and color
- **Shape Tools** — Line, Rectangle, and Ellipse via click-and-drag
- **Flood Fill** — Scanline-based fill with tolerance control; creates a new layer per fill
- **Eye Dropper** — Sample any pixel color from the canvas
- **Eraser** — Draws at 8× the normal line width using the background color
- **Selection** — Tap to select strokes; drag to reposition; Delete key to remove
- **Layer System** — Add, delete, reorder, hide/show layers with individual opacity
- **Undo / Redo** — Full layer-state history (`Cmd+Z` / `Cmd+Shift+Z`)
- **Zoom & Pan** — 10%–500% zoom with slider, keyboard shortcuts, and Fit to Window
- **Grid Overlay** — Toggleable 50px spacing grid
- **Drag & Drop** — Drop image files onto the canvas to create image layers
- **Export** — PNG, JPEG, TIFF, BMP, or vector PDF
- **Print** — Full-resolution canvas via macOS print panel
- **Auto-save** — Every 30 seconds (configurable in Preferences)

## System Requirements

- macOS 14 (Sonoma) or later
- Apple Silicon or Intel

## Installation

### Option A — Open the pre-built app

```bash
open "Doodle Pad.app"
```

### Option B — Build from source

```bash
swift build -c release
```

Or use the included build script (which also assembles the `.app` bundle with icon and localizations):

```bash
chmod +x build-app.sh
./build-app.sh
```

## Usage

### Getting started

1. Launch the app and use **File → New Canvas** (or `Cmd+N`) to create a new document
2. Pick a canvas preset (Square, HD, Full HD, 4K, A4) or enter a custom size
3. Start drawing with the **Draw** tool selected in the sidebar

### Tools sidebar

| Tool | Description |
|---|---|
| **Draw** | Freehand brush |
| **Line** | Straight line |
| **Rectangle** | Filled rectangle |
| **Ellipse** | Filled ellipse |
| **Fill** | Flood fill (click an area) |
| **Eyedropper** | Pick a color from the canvas |
| **Eraser** | Erase by drawing (toggled with `E`) |
| **Select** | Tap a stroke to select, then drag or delete |

### Layers

The layers panel lists layers from top to bottom. Use the **+** / **−** buttons to add or remove layers, and the arrow buttons to reorder. Toggle the eye icon to show/hide a layer.

### Keyboard shortcuts

| Shortcut | Action |
|---|---|
| `Cmd+N` | New canvas |
| `Cmd+O` | Open file |
| `Cmd+S` | Save |
| `Cmd+Shift+S` | Save As |
| `Cmd+Shift+E` | Export |
| `Cmd+P` | Print |
| `Cmd+Shift+C` | Copy canvas to clipboard |
| `Cmd+Z` | Undo |
| `Cmd+Shift+Z` | Redo |
| `Cmd+K` | Clear active layer |
| `Cmd+G` | Toggle grid |
| `Cmd+Shift+L` | Add layer |
| `Cmd+=` / `Cmd+-` | Zoom in / out |
| `E` | Toggle eraser |
| `Delete` | Delete selected stroke |

## File format

Doodle Pad uses its own `.doodlepad` format — a JSON-based document that preserves all strokes, layers, colors, and canvas settings. Export to standard image formats via **File → Export**.

## Localization

Available in English, French, German, Spanish, and Japanese. The app automatically matches your system language.

## Project structure

```
Sources/DrawingApp/
├── App.swift                 # App entry point and menu commands
├── ContentView.swift         # Main layout, keyboard handling, status bar
├── CanvasView.swift          # Canvas rendering and drag-and-drop
├── SidebarView.swift         # Tools, colors, shapes, layers, view options
├── DrawingDocument.swift     # Core data model, export, I/O, undo
├── Layer.swift               # Layer struct
├── CanvasSize.swift          # Canvas size presets
├── NewCanvasSheet.swift      # New canvas dialog
├── PreferencesView.swift     # Settings window
└── Info.plist                # Bundle metadata
```

## Building from source

The project uses Swift Package Manager with no external dependencies.

```bash
swift build              # debug build
swift build -c release   # release build
```

The `build-app.sh` script automates creating a complete `.app` bundle with icon and localizations.

## License

See `LICENSE` (if present) or contact the author.
