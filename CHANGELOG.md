# Changelog

All notable changes to this project are documented in this file.

This changelog is organized by release tag, based on git commit history.

> 中文版：[CHANGELOG.zh-CN.md](CHANGELOG.zh-CN.md)

## 2.0.0.8 - 2026-06-26

### Added
- **List preview length setting**: a new Clipboard option controls the maximum text length shown per entry in the history list (8 KB – 1 MB); the preview window always shows the full content.
- **Hide empty fields in the structured preview**: a toggle in the JSON/YAML tree view hides fields whose value is null or an empty string.
- The structured preview now keeps the `[OUTGOING]` / `[INCOMING]` (and similar) line labels found in captured logs, wrapping each frame under its label so the direction stays visible.

### Fixed
- Clipboard content was sometimes not captured. Fixed a suppression flag that leaked when the clipboard could not be opened, and added retries for remote-desktop / Cloud PC clipboard sync that uses delayed rendering.


## 2.0.0.7 - 2026-06-26

### Added
- **Structured preview for JSON / YAML**: text detected as JSON or a YAML mapping is shown as a collapsible, syntax-highlighted tree, with expand-all / collapse-all controls. The preview can be switched between Structured / Rich text / Plain text.
- **Encode/Decode tools in the preview**: Base64, Base64Url, URL, Hex and Quoted-Printable encode & decode, MD5 hash, SAML (deflate) encode/decode, Pretty JSON, UTF16 and pwdLastSet/FILETIME decode, with one-click copy of the result.

### Changed
- The software-update check now shows the detailed failure reason (e.g. the HTTP status and message) instead of a generic "network" error.

## 2.0.0.6 - 2026-06-25

### Added
- **Preview window**: click "Preview" below a history entry or in its right-click menu to view the full content in a separate, resizable window. The window can be maximized / restored / minimized / closed, opens centered on screen, supports text selection, offers a rich text / plain text toggle, and lets you click links to open them in the default browser.
- **Markdown rendering**: plain text detected as Markdown is rendered as rich text in both the list and the preview window; when pasting as rich text, the rendered HTML is pasted instead of the raw Markdown source.
- Entries now show a small metric next to the timestamp: character count for text, pixel dimensions for images, and file/folder count for files.

## 2.0.0.5 - 2026-06-25

### Added
- **Smart content recognition** for plain-text entries in the history list: pure color values (`#rgb`/`#rrggbb`/`#rrggbbaa`, `rgb()`/`rgba()`, `hsl()`/`hsla()`) now show a color swatch preview, `http`/`https` links are highlighted and clickable to open in the default browser, and code-like text is rendered in a monospace block.
- Added a dedicated **Clipboard** settings section. The **Default rich text paste format** and **rich text/HTML preview** options moved here from General.

### Changed
- The portable package is now named `Clipwell-<version>-portable.zip` to distinguish it from the installer.

## 2.0.0.4 - 2026-06-23

### Added
- **Rich text (HTML/RTF) support**: clipboard entries now capture and restore HTML/RTF formatting, show a formatted preview in the list, and offer **Paste as plain text** in the right-click menu.
- Added a **Default rich text paste format** setting (rich/plain) and a **rich text/HTML preview** setting (rich/plain) in the settings center.
- Packaging now also produces an **NSIS installer** (`Setup.exe`) alongside the portable zip.

### Changed
- Images now use the lossless **PNG** clipboard format: captured and restored without re-encoding (preserving transparency), and **Save as file** exports images as `.png` instead of `.jpg`.
- Clicking or copying an entry no longer refreshes its timestamp.

### Fixed
- Fixed the right-click context menu lingering after the window was hidden and reopened.

## 2.0.0.3 - 2026-06-22

### Added
- Added a **Window position** setting (General) to choose where the history window appears when opened: follow cursor, screen center, or bottom-right of screen.
- Added a **network proxy** setting (Update) so update checks and downloads can go through a configured proxy.

### Changed
- The history window now returns focus to the search box after clicking any non-input element.
- Removed the exe "unlock" mode and its related logic.

## 2.0.0.2 - 2026-06-18

### Fixed
- `lastUpdateCheck` is no longer stored in `config.json`. This runtime value now lives in a separate `update_state.json`, and any legacy value left in `config.json` is migrated automatically on first launch.

## 2.0.0.1 - 2026-06-18

### Changed
- Rebranded the product from "ClipHistory" to **Clipwell**. The executable, window titles, tray tooltip, About dialog, and all bundled translations now use the new name. Existing settings, clipboard history, pinned items, and cached images are migrated automatically on first launch, and the previous auto-start entry is carried over so the app keeps launching at startup without any manual steps.

## 1.1.0.8 - 2026-06-18

### Added
- Added a built-in software updater that checks the public GitHub repository for new releases, downloads the latest package, replaces the running executable in place, and prompts to restart. A new "Update" section in Settings shows the current version, lets you choose the check frequency (Manually / On startup / Daily / Weekly), and offers a one-click "Check now" action.
- Added a "Check for Updates" entry to the tray menu that opens the Update section and starts a check.

## 1.1.0.7 - 2026-06-18

### Added
- Added MIT license and an English `README.md` (with the Chinese version moved to `README.zh-CN.md`) for the public GitHub repository.
- Added GitHub Actions workflows: a release pipeline that builds, packages, and publishes a GitHub Release with the zip artifact when a version tag is pushed, plus a CI build check for pushes and pull requests.

## 1.1.0.6 - 2026-06-18

### Changed
- Frameless windows (history, settings, about) now use a manual capture-based drag instead of the system modal move loop, so content keeps repainting in real time while dragging across monitors with different DPI.

### Fixed
- Fixed the "Add note" context-menu item having no effect, and made notes persist to disk so they survive a window reload.
- Fixed the settings and about windows changing physical size when moved across monitors with different DPI; they now keep a constant physical size like the history window.

## 1.1.0.5 - 2026-06-17

### Added
- Added a tray menu command to restart the program.
- Added "Save as file" for clipboard text and images, with images exported as `.jpg`, text saved with an auto-detected extension (`.txt`, `.md`, `.py`, `.js`, `.c`), and a configurable export save path in Settings.

### Changed
- Improved history search performance with `useMemo` and `useDeferredValue`.
- When the History window is shown, the list scrolls back to the top and the active tab resets to `All`.

### Fixed
- Fixed editor-only TypeScript diagnostics for CSS imports in the React UI by adding `vite-env.d.ts`.
- Hardened restart behavior to work more safely with the `unlock` mode and preserved startup arguments.

## 1.1.0.4 - 2026-06-05

### Changed
- The list scrolls back to the top when switching history tabs.

## 1.1.0.3 - 2026-06-02

### Changed
- History entries are now promoted to the top and the list is resent after relevant actions, keeping recently used items in order.

## 1.1.0.2 - 2026-05-27

### Changed
- Added a distinct background and hover style for pinned items.
- Unified window background and scrollbar styling to match the Fluent dark theme.
- The search box is now auto-focused when the window opens.

## 1.1.0.1 - 2026-05-26

### Added
- Global Escape key: clears the search when it has text, otherwise hides the window.
- Custom themed scrollbars and dark-mode support for native Windows menus.

### Changed
- Rewrote the entire frontend with React components.
- Recently used entries are promoted and the history is sorted by timestamp.
- The app now launches automatically after a successful build, and the tray icon shows a tooltip.

### Removed
- Removed the version display from the settings page.

## 1.0.0.5 - 2026-05-18

### Added
- Added English and Chinese user manuals (usage, system requirements, install steps, FAQ).
- The release package now includes the `docs/` folder.

## 1.0.0.4 - 2026-05-18

### Added
- Added 8 more languages: German, Spanish, French, Japanese, Korean, Brazilian Portuguese, Russian, and Traditional Chinese.
- Added a right-click context menu (paste, copy to clipboard, add note, pin, delete).
- Added per-entry notes that can be added and edited.
- Added an About window.
- Added a debug mode (`--debug`) that enables DevTools and the native context menu.
- Added an exe-unlock capability so the running executable can be overwritten while running.

### Fixed
- Fixed the auto-start registry path to always point at the correct executable.
- Prevented window dragging from starting when clicking the scrollbar area.
- Fixed the settings window not always coming to the foreground.

## 1.0.0.3 - 2026-05-13

### Added
- Redesigned the settings page with left-side group navigation and panel switching.
- Added internationalization with English and Simplified Chinese, plus automatic OS language detection.
- Added a theme setting (system / dark / light).
- Added clearing clipboard history by type (text, image, files).
- Added global hotkey registration and unregistration with custom configuration.

### Changed
- Adjusted scrollbar colors for better readability.
- Improved the build and packaging scripts (CMake location, output messages, error handling).

## 1.0.0.2 - 2026-05-11

### Added
- Added single-instance protection to prevent multiple instances running at once.
- Added a file watcher that reloads data when the underlying files change.
- Added configurable global hotkey settings.
- Added "copy to clipboard" support for images and files.
- Added a maximum history count setting (including unlimited).
- Added a save-interval setting and auto-save (every 60 seconds by default).
- Added portable mode (data stored next to the executable).
- Added custom scrollbar styling.
- Added a settings window.

### Changed
- Unified the user data path across windows.
- The popup is now consistently anchored below the cursor.

## 1.0.0.1 - 2026-05-09

### Added
- Initial release of Clipwell, a Windows clipboard history manager.
- Clipboard monitor with a history window shown via the Win+Shift+V hotkey.
- Per-monitor DPI awareness, rounded corners, and a flicker-free background.
- History deduplication with pinned-entry preservation, and drag-to-move for the window.
