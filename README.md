# OSS Audit — Linux Kernel
**Student Name:** Rishi Raj  
**Registration Number:** 24BCE10149  
**Course:** CSE0002 — Open Source Software | VIT Bhopal University  
**Software Audited:** Linux Kernel (GPL v2)  
**Repository:** `OSS-Audit`

---

## About This Project

This repository contains the five shell scripts for the Open Source Software Capstone Project — *The Open Source Audit*. The project audits the **Linux Kernel**, examining its origin story, GPL v2 license, philosophy, Linux footprint, FOSS ecosystem, and a comparison with proprietary alternatives (Windows NT Kernel).

---

## Repository Contents

| File | Description |
|------|-------------|
| `script1_system_identity.sh` | Displays system info: kernel version, distro, uptime, user, and GPL v2 license details |
| `script2_package_inspector.sh` | Checks if a FOSS package is installed, shows version/license, and prints a philosophy note (case statement) |
| `script3_disk_permission_auditor.sh` | Audits key system directories: permissions, ownership, and disk usage using a for loop |
| `script4_log_analyzer.sh` | Reads a log file line by line, counts keyword matches, and displays the last 5 matches |
| `script5_manifesto_generator.sh` | Interactively generates and saves a personalised open-source philosophy statement |
| `README.md` | This file |

The project report PDF is submitted separately via the VITyarthi portal.

---

## Environment Requirements

- **OS:** Ubuntu 22.04 LTS or any Debian-based Linux (or similar)
- **Shell:** Bash (version 4.0+)
- **Dependencies:** All scripts use standard Linux utilities: `uname`, `whoami`, `uptime`, `dpkg`, `apt-cache`, `ls`, `du`, `grep`, `awk`, `cut`, `date` — no additional installation required
- **Permissions:** Script 4 may require `sudo` to read `/var/log/syslog` depending on your system configuration

---

## Setup Instructions

### Step 1 — Clone the repository
```bash
git clone https://github.com/RishiRaj1495/oss-audit-24BCE10149.git
cd oss-audit-24BCE10149
```

### Step 2 — Make all scripts executable
```bash
chmod +x script1_system_identity.sh
chmod +x script2_package_inspector.sh
chmod +x script3_disk_permission_auditor.sh
chmod +x script4_log_analyzer.sh
chmod +x script5_manifesto_generator.sh
```

Or make all at once:
```bash
chmod +x *.sh
```

---

## Running Each Script

### Script 1 — System Identity Report
Displays your Linux system info and kernel license details.
```bash
./script1_system_identity.sh
```
**Expected output:** Kernel version, distribution name, uptime, user info, date/time, and GPL v2 license statement.

---

### Script 2 — FOSS Package Inspector
Checks if a package is installed and prints a philosophy note.
```bash
# Inspect the current kernel package (default)
./script2_package_inspector.sh

# Inspect a specific package by name
./script2_package_inspector.sh linux-image-generic
./script2_package_inspector.sh git
./script2_package_inspector.sh vlc
```
**Expected output:** Package install status, version, and a one-paragraph philosophy note about the package.

---

### Script 3 — Disk and Permission Auditor
Audits key system directories and kernel-specific paths.
```bash
./script3_disk_permission_auditor.sh
```
**Expected output:** A formatted table of directories showing permissions, owner, group, and disk size. Also checks `/boot`, `/lib/modules`, and `/proc/version`.

---

### Script 4 — Log File Analyzer
Reads a log file and counts keyword matches. Requires read access to the log file.
```bash
# Analyse syslog for 'kernel' messages (default)
sudo ./script4_log_analyzer.sh /var/log/syslog kernel

# Analyse kern.log for errors
sudo ./script4_log_analyzer.sh /var/log/kern.log error

# Analyse with a custom keyword
sudo ./script4_log_analyzer.sh /var/log/syslog usb
```
**Expected output:** Total lines scanned, match count, and the last 5 matching lines.

> **Note:** On some Ubuntu systems, `/var/log/syslog` requires sudo or the user must be in the `adm` group: `sudo usermod -aG adm $USER` (then log out and back in).

---

### Script 5 — Open Source Manifesto Generator
Interactive — asks you three questions and saves a personalised manifesto.
```bash
./script5_manifesto_generator.sh
```
**Follow the prompts:**
1. Enter a tool you use every day (e.g., `bash`, `git`, `Linux`)
2. Enter one word for what freedom means (e.g., `choice`, `transparency`)
3. Enter something you would build and share (e.g., `a music player`)

**Expected output:** A manifesto printed to the terminal and saved as `manifesto_[yourusername].txt` in the current directory.

---

## Troubleshooting

| Issue | Solution |
|-------|----------|
| `Permission denied` on script | Run `chmod +x scriptname.sh` |
| `sudo: command not found` | You may be running as root already — remove `sudo` |
| Log file not found (Script 4) | The script auto-detects fallback logs; or run `dmesg > /tmp/kern.log && ./script4_log_analyzer.sh /tmp/kern.log error` |
| `dpkg: not found` (Script 2) | You are on a non-Debian system; replace `dpkg -l` with `rpm -qa` for RPM-based systems |
| Script outputs nothing | Ensure you are running on Linux with Bash: `echo $SHELL` should show `/bin/bash` |

---

## License

These scripts are written for educational purposes as part of the VIT Bhopal OSS course. They may be freely used and modified.

---

*VIT Bhopal University | CSE0002 — Open Source Software | Capstone Project*
