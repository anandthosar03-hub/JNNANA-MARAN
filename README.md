# JNNANA-MARAN
JannanaMaran is a cross-platform cybersecurity host recon &amp; posture reporting tool with CLI + Tkinter GUI. It generates a JSON report containing OS info, network snapshot, firewall status, and an optional local secrets hygiene scan for authorized assessments and purple-team evidence collection.


##  JNNANA-MARAN repo description 
**JannanaMaran** is a cross-platform cybersecurity host recon & posture reporting tool with **CLI + Tkinter GUI**. It generates a **JSON report** containing OS info, network snapshot, firewall status, and an optional **local secrets hygiene scan**—for **authorized** assessments and purple-team evidence collection.

CLI + GUI host recon & posture reporter (authorized use). JSON output, optional secrets hygiene scan.

---

## README Section

```md
# JannanaMaran

JannanaMaran is a **cross-platform (Windows/Linux)** host recon & security posture reporting tool with:
- **CLI**: `jannanamaran`
- **GUI**: `jannanamaran-gui` (Tkinter)

It is intended for **authorized security assessments / purple-team workflows**.  
It does **not** perform exploitation or payload delivery.

---

## What it collects (JSON report)

Depending on enabled checks, the report may include:

- **OS / Host info**: hostname, current user, OS version, architecture, Python version
- **Network snapshot** (best-effort): interface output, detected IPv4 addresses, DNS view
- **Firewall status** (best-effort):
  - Windows: `netsh advfirewall`
  - Linux: `ufw` and/or `firewalld` (if installed)
- **Optional secrets hygiene scan** (local directory):
  - searches for indicators like private key blocks and common API key/token patterns
  - meant for hygiene/auditing; may include false positives

---

## Requirements

- **Python 3.9+**
- GUI requires **Tkinter**
  - **Windows**: Tkinter is usually included with the official Python installer.
  - **Linux**: you may need to install it separately (see below).

---

# Setup & Run (Windows)

## 1) Install Python
Install Python 3.9+ from:
- https://www.python.org/downloads/windows/

During installation, enable:
- ✅ “Add Python to PATH”

Verify in PowerShell:
```powershell
python --version
pip --version
```

## 2) Get the project
```powershell
git clone https://github.com/anandthosar03-hub/JNNANA-MARAN.git
cd JannanaMaran
```

## 3) Create and activate a virtual environment (recommended)
```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
```

> If PowerShell blocks activation, run:
```powershell
Set-ExecutionPolicy -Scope CurrentUser RemoteSigned
```
Then activate again.

## 4) Install the tool (editable / dev install)
```powershell
pip install -e .
```

## 5) Run (CLI)
```powershell
jannanamaran -o jannanamaran_report.json
```

Optional secrets scan (only scan folders you are authorized to audit):
```powershell
jannanamaran -o report.json --secrets-root .
```

## 6) Run (GUI)
```powershell
jannanamaran-gui
```

---

# Setup & Run (Linux)

## 1) Install Python + venv + Tkinter
### Debian/Kali/BlackArch
```bash
sudo apt-get update
sudo apt-get install -y python3 python3-venv python3-pip python3-tk git
```

### Fedora
```bash
sudo dnf install -y python3 python3-pip python3-tkinter git
```

Verify:
```bash
python3 --version
pip3 --version
```

## 2) Get the project
```bash
git clone https://github.com/anandthosar03-hub/JNNANA-MARAN.git
cd JannanaMaran
```

## 3) Create and activate a virtual environment (recommended)
```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
```

## 4) Install the tool (editable / dev install)
```bash
pip install -e .
```

## 5) Run (CLI)
```bash
jannanamaran -o jannanamaran_report.json
```

Optional secrets scan (only scan folders you are authorized to audit):
```bash
jannanamaran -o report.json --secrets-root .
```

## 6) Run (GUI)
```bash
jannanamaran-gui
```

---

## Output

A JSON report is written to the output path you provide (example: `jannanamaran_report.json`).

Top-level keys typically include:
- `os_info`
- `network`
- `firewall`
- `secrets_scan` (only if enabled)

---

## Notes / Troubleshooting

- **GUI won’t start on Linux**: install Tkinter (`python3-tk` on Debian/Ubuntu, `python3-tkinter` on Fedora).
- **Command not found (`jannanamaran`)**: ensure your virtual environment is activated, and that you ran `pip install -e .`.
- **Firewall checks** are best-effort and depend on what tools exist on the system (e.g., `ufw`, `firewall-cmd`).

---

## Safety / Legal

Use only on systems and directories you **own** or where you have **explicit written permission** to assess.  
The secrets scan is a hygiene helper and may produce false positives; review findings carefully.



