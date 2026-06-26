# Clipwell

A lightweight Windows clipboard history manager — runs in the system tray, pops up instantly via a global hotkey (default `Win + V`), and pastes back to the previous window with a single click.

This repository hosts **release downloads only**. Grab the latest build from the [Releases](https://github.com/denphon/clipwell/releases) page.

## Download & install

1. Open the [Releases](https://github.com/denphon/clipwell/releases) page.
2. Choose how to install:
   - **Installer**: download `Clipwell-<version>-Setup.exe` and run it (adds Start menu / desktop shortcuts and an uninstall entry).
   - **Portable**: download `Clipwell-<version>-portable.zip`, extract it anywhere, and run `Clipwell.exe` (data stays next to the exe).

Requires the **WebView2 Runtime**, which ships with Microsoft Edge on Windows 10/11 (already present on most systems).

## Features

- Tracks clipboard history for **text, images, and files/folders**.
- **Rich text (HTML/RTF)** is captured and restored, with a formatted preview in the list and a "paste as plain text" option.
- Images use the lossless **PNG** format (transparency preserved) and export as `.png`.
- **Smart recognition** for plain text: color values show a swatch preview, links are clickable to open in the browser, and code is shown in a monospace block.
- **Markdown rendering**: text recognized as Markdown is rendered as rich text in both the list and the preview, and a rich paste pastes the rendered result.
- **Preview window**: open an entry's full content in a separate resizable window (centered, text selection, rich/plain toggle, clickable links).
- **Structured preview**: JSON / YAML is shown as a collapsible, syntax-highlighted tree (expand/collapse all).
- **Encode/Decode tools** in the preview: Base64 / Base64Url / URL / Hex / Quoted-Printable, MD5, SAML, Pretty JSON, UTF16 and FILETIME decode, with one-click copy.
- **Click an entry to paste** it into the previously active window.
- System tray icon with a global hotkey to open the history window (default `Win + V`, customizable).
- Edge-style dark/light themes, grouping tabs (All / Text / Image / Files / Pinned), search, pin, notes, and save-as-file.
- Configurable history size, paste/preview format, auto-save interval, export path, UI language, and theme.
- Single-instance, Per-Monitor DPI Aware, zero-latency popup.
- **Portable mode**: place an empty `portable` file next to the exe to store all data under `<exe dir>\data\`.

## Changelog

See [CHANGELOG.md](CHANGELOG.md) for release notes.

## License

[MIT](LICENSE)
