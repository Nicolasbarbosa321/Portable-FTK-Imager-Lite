# Portable FTK Imager (Imager Lite)

![Forensics](https://img.shields.io/badge/Forensics-DFIR-blue)
![WinFE](https://img.shields.io/badge/Environment-WinFE-informational)
![Windows](https://img.shields.io/badge/Platform-Windows-0078D6)
![USB](https://img.shields.io/badge/Deployment-Portable%20USB-success)
![Status](https://img.shields.io/badge/Status-Operational-green)
![License](https://img.shields.io/badge/License-Documentation%20Only-lightgrey)

##  Overview
This repository documents how to create and run a **portable version of FTK Imager**—commonly referred to as **“Imager Lite”**—from a removable flash drive or WinFE USB.

This approach is ideal for forensic acquisition and triage on systems where **software installation is restricted, undesirable, or prohibited**.



##  Purpose
Running FTK Imager from a portable flash drive enables Security Operations and Digital Forensics teams to:

- Perform forensic imaging **without installing software** on the target system
- Minimize system impact and avoid installation artifacts
- Maintain **field-ready portability** for live response and incident handling
- Support forensic acquisition within **WinFE or live Windows environments**


##  Prerequisites

Before proceeding, ensure you have the following:

- A **separate preparation machine** (never the forensic target)
- A removable **USB flash drive** (FAT32 or NTFS recommended)
- A **licensed or standard installation of FTK Imager** on the preparation machine
- Administrator access on the preparation system


##  Procedure

### Step 1 — Install FTK Imager
Install FTK Imager on the **preparation machine only**. Do **not** install FTK Imager on the forensic target system.

---

### Step 2 — Prepare the Flash Drive

- Insert the **WinFE USB or dedicated forensic flash drive** into the preparation system
- Ensure sufficient free space for the FTK Imager directory and output images

---

### Step 3 — Copy FTK Imager to the Flash Drive

Copy the **entire FTK Imager installation directory** from the preparation system to the flash drive.

Common installation paths:

```text
C:\Program Files\AccessData\FTK Imager
```

or

```text
C:\Program Files (x86)\AccessData\FTK Imager
```

📁 Recommended destination on USB:
```text
X:\Tools\FTK_Imager
```

---

### Step 4 — Load on Target System

- Insert the prepared flash drive into the **target system**
- Boot into **WinFE** or the live Windows environment (as authorized)

---

### Step 5 — Navigate to the Application Folder

Browse to the FTK Imager directory on the flash drive:

```text
X:\Tools\FTK_Imager
```

---

### Step 6 — Run FTK Imager as Administrator

- Right-click `FTK Imager.exe`
- Select **Run as Administrator**
- Use FTK Imager normally to acquire forensic images

---

## ⚠️ Important Operational Note

> **Live-system imaging may produce non-replicable results** due to system activity.

During execution, FTK Imager may:
- Write data to system RAM
- Trigger pagefile or temporary file changes
- Interact with active processes

Analysts **must evaluate and document these risks** prior to acquisition.

---

##  Additional Requirements for Specific Versions

### Microsoft Foundation Class (MFC) Files

FTK Imager **v3.4.3 and later** require MFC runtime files. If these are missing on the target system, FTK Imager will fail to launch.

Copy the following files from the preparation system:

```text
C:\Windows\System32
```

To the FTK Imager directory on the flash drive:

- `mfc100.dll`
- `mfc110.dll`
- `mfc120.dll`
- `mfc140.dll` (if required)

---

### Visual C++ 2015 Redistributable DLLs (FTK Imager 4.5.0)

For FTK Imager **v4.5.0**, also copy the following DLLs:

- `msvcp140.dll`
- `vcruntime140.dll`
- `mfc140u.dll`

Source directory:
```text
C:\Windows\System32
```

Destination:
```text
X:\Tools\FTK_Imager
```

---

##  Summary

Following this procedure allows forensic and security teams to:

- Deploy FTK Imager rapidly in the field
- Avoid installing tools on sensitive systems
- Maintain forensic defensibility
- Support live response, triage, and acquisition workflows

This **portable FTK Imager configuration** provides a reliable and flexible solution for forensic imaging without relying on traditional installation methods.

---

## 📜 License & Disclaimer

FTK Imager is a proprietary forensic tool.

This repository provides **operational guidance only** and does not redistribute FTK Imager binaries.

Use is restricted to **authorized forensic and incident response activities** with appropriate legal approval.

