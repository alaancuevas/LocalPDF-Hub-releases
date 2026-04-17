# Security Policy

## Supported versions

| Version | Supported |
|---------|-----------|
| 3.0.x   | ✅ Yes     |
| 2.0.x   | ⚠️ Security fixes only |
| 1.0.x   | ❌ End of life |

## Reporting a vulnerability

If you find a security issue in LocalPDF Hub, please do **not** open a public issue.

Contact directly: localpdfhub.contact@gmail.com

Include:
- Description of the vulnerability
- Steps to reproduce
- Potential impact
- Version affected

You will receive a response within 72 hours.

## Scope

LocalPDF Hub processes documents entirely on the user's local machine. The following are considered in-scope for security reports:

- Vulnerabilities that allow remote code execution via the local HTTP server
- Path traversal or arbitrary file read/write through the API endpoints
- Denial of service that persists after the process terminates
- Issues related to temporary file handling that could leak document contents
- Vulnerabilities in the document processing pipeline (malicious PDFs, crafted DOCX, etc.)

## Out of scope

- Accessing the service from another machine on the same LAN when **Network Mode** is intentionally enabled (this is a documented feature, not a vulnerability)
- Issues that require physical access to the user's device
- Social engineering, phishing, or password guessing
- Vulnerabilities in third-party dependencies already reported upstream

## Network Mode disclosure

LocalPDF Hub can be optionally configured to listen on all network interfaces (`0.0.0.0`) for use within a local network. This mode:

- **Does not include authentication** — it is designed for trusted internal networks
- **Must never be exposed to the public internet** — doing so would allow anyone to process, download and access documents on the server
- Is disabled by default (the app listens only on `127.0.0.1`)

Users who enable Network Mode are responsible for ensuring their LAN is properly firewalled.

## Third-party components

Security issues in the following dependencies should be reported upstream to their respective maintainers:

- **FastAPI / Uvicorn** — https://github.com/tiangolo/fastapi
- **pypdf** — https://github.com/py-pdf/pypdf
- **Pillow / pillow-heif** — https://github.com/python-pillow/Pillow
- **PDF.js** — https://github.com/mozilla/pdf.js
- **pystray** — https://github.com/moses-palmer/pystray
