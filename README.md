# 📡 Local Share

**Drop a file on your laptop, pick it up on your phone — no cloud, no cables, no account.**

A self-hosted, LAN-only file-sharing web app: drag-and-drop uploads with a live progress bar, instant image/video preview, search, rename, a QR code + auto device discovery (mDNS), a shared-password login, and every file encrypted at rest. Runs anywhere Python runs, or as a single double-click `.exe` on Windows.



[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Python 3.10+](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/built%20with-FastAPI-009688.svg)](https://fastapi.tiangolo.com/)
[![Build Windows exe]https://github.com/kiran99756/Localshare/releases/tag/v1.0.0
## Why

Sharing a file between your laptop and your phone shouldn't require uploading it to a cloud you don't control, emailing it to yourself, or plugging in a cable. If both devices are on the same Wi-Fi, this spins up a tiny private webpage every device on that network can use — nothing leaves the LAN.

## Features

- 📤 **Drag-and-drop upload** with a real per-file progress bar
- 🖼️ **Image & video preview** inline, no download needed
- 🔍 **Search** across shared files
- ✏️ **Rename** files from the browser
- 📱 **Auto discovery, two ways** — scan the QR code, use `localshare.local` (mDNS), *or* a UDP broadcast beacon (`discovery.py`) that any client on the LAN can query for the server's IP — useful when mDNS is flaky
- 🌐 **Optional internet sharing** — a "Share Over the Internet" button opens a temporary public HTTPS link (via a Cloudflare quick tunnel, no account/port-forwarding needed) for the rare case someone off your Wi-Fi needs a file. Password login still applies.
- 📲 **Installable on Android** — Add to Home Screen for an app-like icon (PWA manifest + service worker); full standalone install works once accessed over HTTPS (e.g. the internet-sharing link above)
- 🔒 **Password-protected + encrypted at rest** (AES via `cryptography`/Fernet) — a stolen laptop or leaked backup is just ciphertext
- 💬 **Live chat + online presence** over WebSockets
- 🖥️ **Single-file Windows `.exe`** — no Python required on the target machine
- 🌗 Dark mode

## Quick start

```bash
git clone https://github.com/kiran99756/Localshare.git
cd local-share
pip install -r requirements.txt
python main.py
```

The terminal prints your auto-generated password and a URL to open on your phone (or just scan the QR code shown on the page).

### Windows (no Python needed)

Grab `LocalShare.exe` from [Releases](../../releases) and double-click it. Or build it yourself — see [BUILD.md](BUILD.md).

### Internet sharing (optional, one-time setup)

The "Share Over the Internet" button needs the free `cloudflared` binary installed once on the host machine — details in [BUILD.md](BUILD.md#3-internet-sharing-feature-optional-one-time).

Full requirements/build details for every path (dev run, Windows exe, internet sharing, Android install) are in **[BUILD.md](BUILD.md)**.

## Tech stack

FastAPI + WebSockets · SQLite · vanilla JS/CSS (no build step) · `cryptography` for at-rest encryption · `zeroconf` for mDNS · PyInstaller for the Windows build.

## Roadmap / ideas

- [ ] Native Android app (currently: installable PWA via "Add to Home Screen")
- [ ] Linux/macOS `.app` / AppImage builds (Windows exists via PyInstaller already)
- [ ] Per-file expiry / auto-delete
- [ ] Folder/zip upload support

Contributions welcome — see [Contributing](#contributing).

## Contributing

Issues and PRs are welcome. Good first areas: the roadmap above, UI polish, or testing on more Android/iOS browser combos. Please open an issue before a large PR so we can align on approach first.

## License

MIT — see [LICENSE](LICENSE).
