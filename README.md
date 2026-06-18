# ClipHistory

A lightweight Windows clipboard history manager — runs in the system tray, pops up instantly via a global hotkey (default `Win + V`), and pastes back to the previous window with a single click.

This repository hosts **release downloads only**. Grab the latest build from the [Releases](https://github.com/denphon/ClipHistory/releases) page.

## Download & install

1. Open the [Releases](https://github.com/denphon/ClipHistory/releases) page.
2. Download the latest `ClipHistory-<version>.zip`.
3. Extract it anywhere and run `ClipHistory.exe`.

Requires the **WebView2 Runtime**, which ships with Microsoft Edge on Windows 10/11 (already present on most systems).

## Features

- Tracks clipboard history for **text, images, and files/folders**.
- **Click an entry to paste** it into the previously active window.
- System tray icon with a global hotkey to open the history window (default `Win + V`, customizable).
- Edge-style dark/light themes, grouping tabs (All / Text / Image / Files / Pinned), search, pin, notes, and save-as-file.
- Configurable history size, auto-save interval, export path, UI language, and theme.
- Single-instance, Per-Monitor DPI Aware, zero-latency popup.
- **Portable mode**: place an empty `portable` file next to the exe to store all data under `<exe dir>\data\`.

## Changelog

See [CHANGELOG.md](CHANGELOG.md) for release notes.

## License

[MIT](LICENSE)
