# 🌐 Network Mode — Share LocalPDF Hub across your office

With **Network Mode**, one computer runs LocalPDF Hub and everyone else in your office or home uses it from their browser — no installation on their side.

Same `.exe` you already downloaded. You just need to know your local IP.

---

## 🎯 What you get

| | Local Mode (default) | Network Mode |
|---|---|---|
| Installation on clients | Required | **None** |
| Supported client devices | Windows only | **Windows, Mac, Linux, phones, tablets** |
| Works offline | ✅ Yes | ✅ Yes (within your LAN) |
| Files uploaded to cloud | ❌ Never | ❌ Never |
| Concurrent users | 1 | **Multiple** |

Every device on your LAN opens `http://<your-ip>:8000` and uses all 10 tools — merge, split, compress, convert, protect, watermark.

> ⚠️ **Network Mode is designed for trusted internal networks only.** It does not include authentication — anyone on your LAN can use the service. Never expose port 8000 to the public internet.

---

## 🚀 Setup in 3 steps

### Step 1 — Run LocalPDF Hub on the "server" PC

Just double-click `LocalPDF-Hub.exe` as usual. The app starts and docks into your system tray.

This computer will act as the server. Everyone else will connect to it.

---

### Step 2 — Find your local IP

On the server PC, open **CMD** or **PowerShell** and run:

```
ipconfig
```

Look for the line **"IPv4 Address"** under your active network adapter. It will look something like:

```
IPv4 Address. . . . . . . . . . . : 192.168.1.50
```

**That's your IP.** Write it down.

> 💡 If your router changes IPs often, you can set a **DHCP reservation** so this PC always gets the same IP. Most routers have this option in their admin panel.

---

### Step 3 — Connect from any other device

On any phone, tablet, or computer connected to the same Wi-Fi or LAN, open a browser and go to:

```
http://192.168.1.50:8000
```

(Replace `192.168.1.50` with the IP you got in Step 2.)

That's it. Drag, drop, done. Every tool works exactly the same as if you were using the app locally.

---

## 🧱 If the other PC can't connect

**99% of the time it's the Windows Firewall on the server.** By default, Windows blocks incoming connections on port 8000.

### Fix: allow port 8000 through the firewall

On the server PC, open **PowerShell as Administrator** and paste this command:

```powershell
New-NetFirewallRule -DisplayName "LocalPDF Hub" -Direction Inbound -LocalPort 8000 -Protocol TCP -Action Allow
```

You only need to do this once. After that, every device on your network can connect.

### Other things to check

- **Same network?** Make sure both PCs are connected to the same Wi-Fi or LAN. If one is on guest Wi-Fi and the other on the main network, they can't see each other.
- **Correct IP?** IPs can change after a reboot. If it worked yesterday and not today, run `ipconfig` again and check.
- **Port 8000 in use?** If another program is already using port 8000, LocalPDF Hub will fail to start. Close the other program or restart the PC.

---

## 💡 Tips for everyday use

### Set a DHCP reservation so the IP doesn't change

In your router's admin panel (usually `192.168.1.1` or `192.168.0.1`), look for **DHCP settings** → **Reservations** or **Static Leases**. Assign a fixed IP to the server PC's MAC address. Done — the IP won't change even after reboots.

### Share the URL with your team

Once you have the IP, just share it in your team chat:

> "The PDF tools are on `http://192.168.1.50:8000` — add it to your bookmarks."

No accounts, no setup on their end. They just click and use.

### Start the app automatically with Windows

If you want the service available 24/7:

1. Press `Win + R`, type `shell:startup`, press Enter.
2. Copy a shortcut to `LocalPDF-Hub.exe` into that folder.
3. The app will start automatically every time Windows boots.

---

## 🔒 Security notes

- **Never forward port 8000 on your router.** That would expose the service to the entire internet.
- **Keep your Wi-Fi password strong.** Anyone on your network can use the service.
- **Word → PDF conversion runs on the server.** The server PC needs to have Microsoft Word or LibreOffice installed. Clients don't.

---

## 🙋 Need help?

If you hit an issue not covered here, [open an issue on GitHub](https://github.com/alaancuevas/LocalPDF-Hub-releases/issues) with:

- Your Windows version
- The exact error message (or a screenshot)
- What the client device is (phone, Mac, another Windows, etc.)

---

**Network Mode turns LocalPDF Hub into a shared office tool — without ever sending a file to the cloud.**
