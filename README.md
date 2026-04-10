# Network Port Scanner GUI

A lightweight, fast, and user-friendly TCP port scanner with a graphical interface. Built with Python and Tkinter—no external dependencies required.

![Python 3.7+](https://img.shields.io/badge/Python-3.7%2B-blue)
![License: MIT](https://img.shields.io/badge/License-MIT-green)
![Platform](https://img.shields.io/badge/Platform-Windows%20%7C%20macOS%20%7C%20Linux-lightgrey)

## ✨ Features

- **Intuitive 3-field interface** – Enter target, start port, and end port; no configuration needed
- **Blazing-fast multi-threaded scanning** – Up to 500 concurrent connections for rapid results
- **Smart service detection** – Automatically identifies 13+ well-known services (FTP, SSH, HTTP, HTTPS, MySQL, RDP, and more)
- **Real-time feedback** – Live progress bar, elapsed-time counter, and instant port discovery display
- **Graceful interruption** – Stop any scan mid-progress without hanging or data loss
- **Export results** – Save discovered open ports to a clean, shareable `.txt` file
- **Cross-platform** – Runs seamlessly on Windows, macOS, and Linux
- **Zero external dependencies** – Uses only Python's standard library

## 🚀 Quick Start

### Prerequisites

- **Python 3.7** or newer
- **Tkinter** (included by default on Windows/macOS; [install separately on Linux](#linux-setup))

### Installation

```bash
# Clone the repository
git clone https://github.com/techtrainer20/nmap_portscan_gui.git
cd nmap_portscan_gui

# Run the application
python portscanergui.py
```

#### Linux Setup

If Tkinter is not installed:

```bash
# Debian/Ubuntu
sudo apt-get install python3-tk

# Fedora/RHEL
sudo dnf install python3-tkinter

# Arch
sudo pacman -S tk
```

## 📖 Usage Guide

### Basic Scanning

1. **Enter Target** – Type an IP address (`192.168.1.1`) or hostname (`scanme.nmap.org`)
2. **Set Port Range** – Define start and end ports (default: `1`–`1024`)
3. **Click "Start Scan"** – Watch results appear in real time
4. **View Results** – Open ports are displayed instantly as they're discovered
5. **Stop Scan** – Click "Stop" to cancel at any time
6. **Save Results** – Click "Save Results" to export to a `.txt` file

### Example Scenarios

| Scenario | Start Port | End Port | Use Case |
|----------|-----------|----------|----------|
| Quick check | 1 | 1024 | Scan common ports (~30 seconds) |
| Full range | 1 | 65535 | Complete scan (~5-10 minutes) |
| Web services | 80 | 443 | Check HTTP/HTTPS only |
| Database | 3306 | 3306 | Verify single port |
| SSH + HTTPS | 22 | 22 | Then 443 | Check multiple specific ports |

## 🔍 Recognized Services

The scanner automatically labels these common ports:

| Port | Service | Purpose |
|------|---------|---------|
| 21 | FTP | File Transfer Protocol |
| 22 | SSH | Secure Shell (remote access) |
| 23 | Telnet | Unencrypted remote access (legacy) |
| 25 | SMTP | Mail sending |
| 53 | DNS | Domain Name System |
| 80 | HTTP | Web traffic (unencrypted) |
| 110 | POP3 | Email retrieval |
| 143 | IMAP | Email synchronization |
| 443 | HTTPS | Web traffic (encrypted) |
| 3306 | MySQL | Database server |
| 3389 | RDP | Remote Desktop (Windows) |
| 5900 | VNC | Virtual Network Computing |
| 8080 | HTTP-Alt | Alternate HTTP port |

Unknown ports are labeled as `Unknown Service`.

## 🏗️ Project Structure

```
nmap_portscan_gui/
├── portscanergui.py          # Main application (scanner logic + GUI)
├── README.md                 # This file
└── LICENSE                   # MIT License
```

## 🔧 Technical Details

### Performance

- **Concurrency:** 500 configurable worker threads
- **Timeout:** Connection timeout set to prevent hanging
- **Typical Speed:** 1,000 ports in ~30–60 seconds (varies by network)

### Threading Model

The scanner uses Python's `threading` module to test multiple ports in parallel, dramatically improving scan speed over sequential connections.

### Resource Usage

- **Memory:** < 50 MB typical
- **CPU:** Scales with thread count (fully utilizes multi-core systems)
- **Network:** Minimal bandwidth; only TCP SYN/RST packets

## ⚠️ Ethical & Legal Notice

**Important:** This tool is for authorized use only. You must have explicit permission to scan any host or network you do not own. Unauthorized port scanning is illegal in many jurisdictions and may violate:

- Computer Fraud and Abuse Act (CFAA) in the U.S.
- Computer Misuse Act in the UK
- Similar laws in other countries

**Always:**
- ✅ Scan only your own devices and networks
- ✅ Obtain written permission before scanning third-party systems
- ✅ Use in controlled, authorized environments only

Misuse of this tool is the user's sole responsibility.

## 🐛 Troubleshooting

### "Module Tkinter not found"
Install Tkinter for your platform (see [Linux Setup](#linux-setup) above).

### "Connection refused" on all ports
The target may be down, unreachable, or blocking ICMP. Verify connectivity with:
```bash
ping <target>
```

### Scan is very slow
- Reduce the port range (e.g., scan 1–1024 first)
- Check your network connection
- The target may rate-limit or block rapid connections

### Results not saving
Ensure you have write permissions in the directory where you're running the app. Try saving to your home directory.


# 📄 License

This project is released under the [MIT License](LICENSE). See the LICENSE file for full details.

## 📚 Resources

- [Python Tkinter Documentation](https://docs.python.org/3/library/tkinter.html)
- [Python Socket Programming](https://docs.python.org/3/library/socket.html)
- [IANA Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/)
- [Nmap Project](https://nmap.org/) – Industry-standard network scanning tool

## 👨‍💻 Author

**WisteriaM7**

---

**Disclaimer:** This tool is provided as-is for educational and authorized testing purposes only. The author assumes no responsibility for misuse or damage caused by this software.
