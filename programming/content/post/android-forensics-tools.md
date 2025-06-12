---
title: "Android Forensics Tools"
date: 2025-05-24T13:23:21+02:00
math: false
tags: [android,forensics, tools]
categories: [forensics]
---

# Android Forensics Tools 

My personal compilation of tools for Android Forensics and Analysis. I will be extending this list.

---

## **ADB**

Useful to interact with Android devices via the command line.

🔗 [Download ADB](https://developer.android.com/studio/releases/platform-tools)

**Commands:**

```bash
adb devices                  # List connected devices
adb shell                   # Start shell on device
adb install .\app-debug.apk	# Install app
adb pull /sdcard/data.txt   # Copy file from device
adb push					# Ex (adb push .\frida-server-16.7.14-android-x86_64 /data/local/tmp/)
adb logcat                  # View device logs
```

## **LiME (Linux Memory Extractor)**

Dumping volatile memory from Android devices.

🔗 [LiME GitHub](https://github.com/504ensicsLabs/LiME)

**Usage Example:**

```bash
insmod lime.ko "path=/sdcard/mem.lime format=lime"
```


## **FTK Imager**

To open and view a forensic image

🔗 [FTK Imager Download](https://accessdata.com/product-download/ftk-imager-version-4-5)


## **ALEAPP**

Parses multiple artifact types (SMS, contacts, call logs, locations, apps, etc.)
🔗 [ALEAPP GitHub](https://github.com/abrignoni/ALEAPP)


1. Extract data from the Android device (e.g., using ADB or physical acquisition tools).
2. Run ALEAPP on the extracted data folder:

```bash
python aleapp.py -i /path/to/extracted/data -o /path/to/output/report
```
