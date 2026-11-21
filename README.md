# Pixel Board

Pixel Board is a browser-based 2D pixel art editor inspired by [WorldEdit](https://worldedit.enginehub.org/). It combines interactive drawing tools with a coordinate-based command editor.

## Run locally

Open [index.html](index.html) in a modern browser. No build step or server is required for the core editor. Fonts may be loaded from Google Fonts when connected to the internet.

## Features

- Interactive canvas with pencil, eraser, line, rectangle, fill, color picker, and selection tools
- Scriptable shapes and editing operations using WorldEdit-style commands such as `//rect`, `//line`, `//cyl`, `//replace`, and `//stroke`
- Four built-in canvas aspect ratios, coordinate rulers, and image export
- Brush types, widths, procedural color patterns, masks, undo/redo, and palette controls
- Embedded 48×48 sprite library and `//sprite <id> <x> <y> [scale]` placement
- Design-to-output resolution scaling with nearest-neighbor pixel preservation
- Precision text commands for font, weight, alignment, outlines, and shadows
- Compressed RGBA `//pixels` commands for round-trip PNG pixel data
- A fast `//rect` batch runner for large coordinate scripts

## Sample commands

```text
//design 2560 1440
//output 5120 2880
//fit contain
//sampling nearest
//canvas #101827
//rect 400 400 1000 800 #3366FF
//cyl 1280 720 200 #FFCC00
//line 200 200 1400 900 #FFFFFF 8
```

The editor provides an in-app command reference with the supported argument order and syntax.

## Development notes

The editor is currently a **single self-contained HTML application** with its JavaScript and bundled sprite-presets embedded. This initial repository import keeps it simple to run and review. Larger reference-image experiments and screenshots that may contain personal information are intentionally not included in the public repository.

Lossless PNG reconstruction is distinct from semantic editing: a `//pixels` command preserves pixel data but does not automatically convert text or objects into editable shapes. Similarly, rectangle-traced reconstructions can preserve pixels yet require many individual instructions.

## License and credits

No license has been declared for this repository. The WorldEdit name refers to the inspiration for the command vocabulary; this project is not an official EngineHub product. Third-party sprite and art assets retain their original creators' rights and licenses.
