# LocalPDF Hub

> Your files never leave your device.

**LocalPDF Hub** is a Windows desktop app that brings a full suite of PDF tools to your computer — merge, split, compress, convert, protect and watermark documents, all running 100% offline. No cloud uploads, no tracking, no servers. Just pure local power.

---

## ⬇️ Download

Go to the [**Releases**](https://github.com/alaancuevas/LocalPDF-Hub-releases/releases/latest) page to download the latest version.

**System requirements:**
- Windows 7 SP1, Windows 10 or Windows 11 (64-bit recommended)
- ~100MB free disk space
- Microsoft Word or LibreOffice (optional — required for Word ↔ PDF conversion)

---

## ⚡ Features

- **10 powerful tools** — Merge, Split, Compress, Rotate, Word→PDF, PDF→Word, PDF→Images, Extract Images, Watermark, Protect PDF
- **100% offline** — All processing happens on your device. No files ever leave your computer
- **Portable** — Single `.exe` file, no installation required
- **Runs in the system tray** — Silent background service, close anytime from the taskbar
- **Multi-language** — Fluent Spanish / English interface with automatic preference saving
- **Multi-format support** — PDF, PNG, JPG, JPEG, JFIF and native Apple formats (HEIC/HEIF)
- **EXIF rotation correction** — Automatically fixes orientation from phone photos
- **Batch processing** — Convert multiple Word files to PDF in one go (returns a `.zip`)
- **Drag & drop interface** — Modern, intuitive UI with instant thumbnail generation
- **Dark mode** — Full light/dark theme support

---

## 🌐 Network Mode — share across your office

Run LocalPDF Hub on one computer, let everyone in your local network access it from their browser. **No client installs, no user accounts, no cloud.** Works on any device: Windows, Mac, Linux, even phones and tablets.

**Ideal for:**
- Small offices that share a common PDF toolkit
- Administrative teams handling sensitive documents locally
- Anyone who needs a private, self-hosted PDF toolkit

> ⚠️ Network Mode is designed for **trusted internal networks** (home or office LAN) and does not include authentication. **Never expose the service port to the public internet.**

---

## ⚙️ Background Processes & Transparency

To guarantee a smooth user experience and keep your system clean, **LocalPDF Hub** performs several critical operations completely invisibly and automatically:

- **Silent Conversion Engine** — When converting a Word file to PDF, the system internally communicates with Microsoft Word (via COM interface) or activates a fallback engine using LibreOffice (headless mode). **No window from these applications will ever open during the process** — the document is rendered and exported to PDF completely opaquely and transparently.
- **Local Server in the System Tray** — The application is not just a web page, it's a genuine local server. On launch, it silently docks into the system tray (next to the Windows clock). This means you can safely close the browser tab — the processing engine stays alive in the background until you right-click the icon and select "Close LocalPDF Hub".
- **Automatic Residue Cleanup (Zero Clutter)** — The system uses scheduled tasks (`BackgroundTasks`) to manage storage. Immediately after you download your final PDF or ZIP, a hidden process **permanently deletes all temporary files** used during the session, ensuring no traces of sensitive documents remain on your hard drive and no junk files occupy space.
- **Automatic Health Check** — On page load, the frontend silently verifies connectivity to the server through the `/health` endpoint. A small visual indicator confirms the status, so you know immediately if something isn't working before you try to process a file.

---

## 🛠 Installation

1. Download `LocalPDF-Hub.exe` from the [Releases](https://github.com/alaancuevas/LocalPDF-Hub-releases/releases/latest) page.
2. Double-click the file. It's a portable app — no installer, no registry changes.
3. A local server starts silently in your system tray (next to the clock).
4. Your default browser opens automatically at `http://127.0.0.1:8000`.
5. Drag your files in and start working.

To close the app completely, right-click the tray icon and select **"Close LocalPDF Hub"**.

### ⚠️ Windows SmartScreen warning

Because LocalPDF Hub is an indie app without a paid Microsoft code-signing certificate, Windows SmartScreen may show a warning on first launch. This is a false positive.

To proceed:
- Click **"More info"**
- Then click **"Run anyway"**

LocalPDF Hub does not contain malware and does not make any outbound network connections.

### 🛡️ Windows Defender flagged the file?

Some users report that Windows Defender may flag `LocalPDF-Hub.exe` as a virus (typically as `Trojan:Win32/Wacatac.B!ml` or similar). **This is a well-known false positive** affecting many legitimate indie apps packaged with PyInstaller.

**👉 See the full explanation and step-by-step instructions:** [ANTIVIRUS.md](./ANTIVIRUS.md)

The guide covers:
- Why it happens (technical explanation)
- How to verify the file is safe yourself (VirusTotal, SHA256, TCPView)
- How to allow the file on Windows 10 / 11 (3 different methods)

### Windows 7 compatibility

Windows 7 requires the **KB3063858** update to be installed beforehand (provides `api-ms-win-core-path-l1-1-0.dll`). Download it from Microsoft's official site:

| Architecture | Link |
|---|---|
| 64-bit (x64) | https://www.microsoft.com/en-us/download/details.aspx?id=47442 |
| 32-bit (x86) | https://www.microsoft.com/en-us/download/details.aspx?id=47409 |

Windows 7 must also have **Service Pack 1 (SP1)** installed. Reboot after applying the update.

---

## 🔒 Privacy & Data Handling

LocalPDF Hub is built around one principle: **your files never leave your device.**

- All processing happens on your local CPU
- No telemetry, no analytics, no crash reporting
- No outbound connections to any server
- Temporary files are automatically deleted right after you download the result
- The app works with Wi-Fi completely disabled

---

## 💬 Support & Contact

All communication happens through **GitHub Issues** — it's public, searchable, and keeps the conversation transparent for everyone.

- **🐛 Report a bug:** [Open a new issue](https://github.com/alaancuevas/LocalPDF-Hub-releases/issues/new?labels=bug)
- **💡 Request a feature:** [Open a feature request](https://github.com/alaancuevas/LocalPDF-Hub-releases/issues/new?labels=enhancement)
- **❓ Ask a question:** [Browse existing issues](https://github.com/alaancuevas/LocalPDF-Hub-releases/issues) or open a new one

Before opening an issue, please check if someone else already reported the same thing — it saves time for everyone.

### ❤️ Support the project

If LocalPDF Hub saved you time or helped your work, consider buying me a coffee:

- [**MercadoPago**](https://link.mercadopago.com.ar/alaancuevas) (for Argentina / LATAM)
- [**PayPal**](https://paypal.me/jinji102) (international)

Every contribution helps keep the project alive and free forever.

---

## 📄 License

The source code of LocalPDF Hub is proprietary and not publicly available.  
The application is free to use for personal and commercial purposes.

Third-party components used under their respective licenses:
- **PDF.js** — Mozilla Public License 2.0
- **Tailwind CSS** — MIT
- **FastAPI, Uvicorn, Pillow, pypdf, pywin32, pillow-heif, pystray** — see individual package licenses
