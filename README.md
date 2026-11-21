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


## Timelapse video export

In the **Command studio**, enable **Generation timelapse → Record with Run all** before running a script. Choose:

- **Commands / second:** 60 or 120 for the nominal playback speed.
- **Video frame rate:** 60 or 120 FPS. Actual encoded frame delivery may be limited by the browser/device.
- **Max video duration:** 10, 20, or 30 seconds. Long scripts are automatically accelerated to fit the cap, so they do **not** play for hours.
- **Resolution:** up to 540p or 720p, preserving the canvas aspect ratio.
- **Auto-download:** optionally save a PNG as soon as the image is complete and a separate WebM video when encoding finishes. Manual download buttons remain available.

The video is generated **locally in your browser**, not uploaded to YouTube, GitHub, or an external server. WebCodecs VP8 is used where available for offline encoding; otherwise MediaRecorder is used for a real-time fallback. Leave the tab open until the recording finishes. Browser permissions may be required for multiple automatic downloads.

For large `//rect` scripts and `//pixels` scripts, Pixel Board generates the image via the existing fast path first, allowing the PNG to be saved before the video is done encoding. For standard drawing commands, it captures frames while executing the commands. The native image resolution and editable script are unaffected by the video settings.

## Development notes

The editor is currently a **single self-contained HTML application** with its JavaScript and bundled sprite-presets embedded. This initial repository import keeps it simple to run and review. Larger reference-image experiments and screenshots that may contain personal information are intentionally not included in the public repository.

Lossless PNG reconstruction is distinct from semantic editing: a `//pixels` command preserves pixel data but does not automatically convert text or objects into editable shapes. Similarly, rectangle-traced reconstructions can preserve pixels yet require many individual instructions.

## License and credits

No license has been declared for this repository. The WorldEdit name refers to the inspiration for the command vocabulary; this project is not an official EngineHub product. Third-party sprite and art assets retain their original creators' rights and licenses.
