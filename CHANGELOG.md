# Changelog

All notable changes to LocalPDF Hub will be documented here.

Format: `[version] — YYYY-MM-DD`

---

## [3.0.0] — 2026-04-12 — Network Edition 🌐

### 🎉 Major release — Multi-device support

- **Network Mode** — Host LocalPDF Hub on one computer and access it from any browser on your local network
- **Built-in health check endpoint** (`/health`) for instant connection feedback on page load
- **Connection status indicator** — Visual pill showing "Connected" or "Disconnected" with retry button
- **Relative URL resolution** — Frontend now auto-detects the server host (works in both local and network modes)

### 🧰 New tools

- **Watermark** — Add diagonal text watermark to all pages with adjustable opacity
- **Extract Images** — Extract all embedded images from a PDF into a `.zip`
- **PDF → Images** — Render each page as a PNG at 150 DPI, packaged in a `.zip`
- **PDF → Word** — Convert PDF to editable `.docx` with text recognition and image fallback

### 🎨 Interface improvements

- **Responsive sidebar** — Control panel transitions from bottom bar (mobile) to right side panel (desktop)
- **New animations** — Pulsing drop zone, success feedback transitions, smooth card loading
- **Icon redesign** — Refreshed app icon with a minimal vector design that adapts to light/dark mode

### 🏗️ Architecture

- **Migrated from PyPDF2 to pypdf 5+** — Modern, maintained PDF library
- **Compressor optimization** — New `compress_identical_objects` pass reduces file size further
- **Build script fix** — Resolved `UnicodeEncodeError` on Windows CLI environments

---

## [2.0.0] — 2026-02-18

### ✨ Added

- **Rotate PDF** with per-page rotation controls and preview
- **Compress PDF** via content stream optimization
- **Protect / Unlock PDF** with password encryption (AES-256)
- **Split PDF** by page range or individual page selection with live PDF.js preview
- **Multi-language interface** — Spanish and English with auto-detection
- **HEIC / HEIF support** for native Apple device formats
- **EXIF rotation correction** for phone photos
- **Category filtering bar** with animated transitions
- **System tray integration** via pystray

### 🔧 Changed

- Redesigned home screen with responsive CSS Grid layout
- New default color palette with per-tool accent colors
- Improved drag & drop zone with live thumbnail generation

---

## [1.0.0] — 2026-01-05

### 🎉 Initial release

- **Merge PDFs** — Combine multiple PDF files and images into a single document
- **Word → PDF conversion** — Local `.docx` to PDF via Microsoft Word (COM) or LibreOffice (headless)
- **Batch processing** — Multiple Word files returned as an auto-generated `.zip`
- **Drag & drop interface** — Modern upload with instant thumbnail previews
- **System tray service** — Silent background execution
- **Portable executable** — Single `.exe` file, no installation required
- **Auto-cleanup** — Temporary files deleted immediately after download
