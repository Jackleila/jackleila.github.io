---
title: "USB Detection in Windows"
date: 2024-01-09T00:02:24+01:00
math: false
tags: [windows,forensics]
categories: [forensics]
draft: false
---

# Windows Event Logs

## Security Event Logs

* **6416** – A new external device was recognized by the system.
* **4663** – An attempt was made to access an object (useful to monitor file access on USB drives).
* **4656** – A handle to an object was requested.
* **4624 / 4634** – Logon/logoff events to correlate user activity with USB usage.

### System Event Logs

From the Microsoft-Windows-DriverFrameworks-UserMode/Operational log:

* **20001** – A USB device was connected.
* **2100 / 2102** – USB mass storage device installed/removed.

## Registry Locations

Relevant registry keys for tracking USB usage:

* `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Enum\USBSTOR`
* `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\USBSTOR`
* `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Enum\USB`


## Useful Tools

* **Nirsoft USBDriveLog** – Lists all USB drives plugged into the system with timestamps.
* **USBDeview** – Detailed info on current and past USB devices.
* **Velociraptor** – DFIR tool to collect USB artifacts at scale.
* **Sysmon** – Can be configured to log USB events via driver load monitoring.
