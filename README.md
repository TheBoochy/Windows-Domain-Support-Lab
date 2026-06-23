# Windows Domain Support Lab

## Overview

Windows Domain Support Lab is a voluntary portfolio project focused on Windows client administration, Active Directory domain support, user login testing, shared folder access, printer access, basic Group Policy and troubleshooting. Since i'm trying to learn a bit more about sysadmin related cases.

The project continues from the earlier Björklunda Admin Lab server environment. The server-side environment already included Active Directory, DNS, users, groups, shared folders and a shared printer. This project focuses on the client-side support work by adding a Windows client computer and testing common IT support tasks from a user and technician perspective.

---

## Scenario

A small organization has a Windows Server domain environment.

The organization uses:

* Active Directory for users and groups
* DNS for domain services
* SMB shared folders for department file access
* a shared printer hosted on the server
* Group Policy for centralized client/user settings

The goal of this project was to join a Windows client to the domain and verify that common domain support tasks work correctly.

---

## Lab environment

| System         | Role                                                        |
| -------------- | ----------------------------------------------------------- |
| `srv-dc01`     | Domain controller, DNS server, file server and print server |
| `client-win01` | Windows client computer joined to the domain                |

| Item                 | Value                  |
| -------------------- | ---------------------- |
| Domain               | `bjorklunda.local`     |
| Domain controller    | `srv-dc01`             |
| Client computer      | `client-win01`         |
| Test user            | `bjorklunda\it.user01` |
| Client OS            | Windows 11 Pro         |
| Network type         | VMware NAT             |
| Domain controller IP | `192.168.80.12`        |

---

## Completed project parts

| Part    | Topic                                            | Status    |
| ------- | ------------------------------------------------ | --------- |
| Part 1  | Repository setup and planning                    | Completed |
| Part 2  | Windows client VM installation                   | Completed |
| Part 3  | Network and DNS configuration                    | Completed |
| Part 4  | Domain join                                      | Completed |
| Part 5  | Domain user login testing                        | Completed |
| Part 6  | Shared folder access testing and troubleshooting | Completed |
| Part 7  | Printer connection testing                       | Completed |
| Part 8  | Basic Group Policy                               | Completed |
| Part 9  | Troubleshooting support cases                    | Completed |
| Part 10 | Security and support reflection                  | Completed |
| Part 11 | Final README and GitHub polish                   | Completed |

---

## What was tested

### Windows client setup

A Windows 11 Pro client VM named `client-win01` was created and configured.

The client was verified with:

```powershell
hostname
whoami
ipconfig /all
```

---

### DNS and domain discovery

The client DNS server was set to the domain controller:

```text
192.168.80.12
```

Domain discovery was tested with:

```powershell
nslookup srv-dc01.bjorklunda.local
nslookup -type=SRV _ldap._tcp.dc._msdcs.bjorklunda.local
nltest /dsgetdc:bjorklunda.local
```

This confirmed that the client could locate the domain controller before domain join.

---

### Domain join

The client `client-win01` was joined to the Active Directory domain:

```text
bjorklunda.local
```

The first domain join attempt failed because the username format was not accepted. The successful format was:

```text
administrator@bjorklunda.local
```

This was documented as a realistic troubleshooting point.

---

### Domain user login

The domain user below was tested on the domain-joined client:

```text
bjorklunda\it.user01
```

Login was verified with:

```powershell
whoami
hostname
systeminfo | findstr /B /C:"Domain"
```

---

### Shared folder access

The IT user was tested against department SMB shares.

The user could access and write to:

```text
\\srv-dc01\IT
```

The user unexpectedly had access to:

```text
\\srv-dc01\Finance
```

This was investigated and fixed by checking:

```powershell
cmdkey /list
whoami /groups
icacls C:\Shares\Finance
Get-SmbShareAccess Finance
```

The Finance permissions were corrected so only the Finance group had access.

After the fix, `bjorklunda\it.user01` was denied access to the Finance share as expected.

---

### Printer connection testing

The client connected to the shared printer:

```text
\\srv-dc01\Bjorklunda-Test-Printer
```

The test showed that a normal domain user needed administrator approval to install the printer driver.

The printer connection was verified with:

```powershell
Get-Printer
```

The printer was also confirmed in Windows Settings under:

```text
Settings > Bluetooth & devices > Printers & scanners
```

---

### Basic Group Policy

A Group Policy Object was created and linked to the `Bjorklunda` OU.

The GPO was named:

```text
GPO_Block_Control_Panel_For_Users
```

The policy enabled was:

```text
User Configuration > Policies > Administrative Templates > Control Panel > Prohibit access to Control Panel and PC settings
```

The policy was applied on the client with:

```powershell
gpupdate /force
```

The applied GPO was verified with:

```powershell
gpresult /r
```

The test confirmed that the domain user was blocked from opening Control Panel and Settings.

---

## Documentation

The project includes several documentation files.

| File                                      | Purpose                                        |
| ----------------------------------------- | ---------------------------------------------- |
| `README.md`                               | Main project overview                          |
| `logbook.md`                              | Step-by-step project log                       |
| `docs/support_cases.md`                   | Troubleshooting and support case documentation |
| `docs/security_and_support_reflection.md` | Security and support reflection                |
| `screenshots/`                            | Screenshot evidence from the lab               |

---

## Support cases documented

The file `docs/support_cases.md` includes realistic support cases based on the lab.

Covered cases include:

* client cannot find the domain
* domain join fails because username format is invalid
* IT user can access the IT share
* IT user unexpectedly accesses the Finance share
* printer connection requires administrator approval
* user cannot open Control Panel or Settings because of Group Policy

These cases show how common Windows domain problems can be investigated step by step.

---

## Skills demonstrated

This project demonstrates:

* Windows 11 client administration
* VMware virtual machine setup
* Active Directory domain join
* DNS and domain controller discovery
* domain user login testing
* SMB shared folder access testing
* NTFS permission troubleshooting
* SMB share permission troubleshooting
* printer connection testing
* basic Group Policy configuration
* `gpupdate` and `gpresult` usage
* support case documentation
* security and support reflection
* Git and GitHub documentation workflow

---

## Commands used

Examples of commands used during the lab:

```powershell
hostname
whoami
ipconfig /all
nslookup srv-dc01.bjorklunda.local
nslookup -type=SRV _ldap._tcp.dc._msdcs.bjorklunda.local
nltest /dsgetdc:bjorklunda.local
cmdkey /list
whoami /groups
icacls C:\Shares\Finance
Get-SmbShareAccess Finance
Get-Printer
gpupdate /force
gpresult /r
```

---

## Final result

The final result is a completed Windows domain support lab where:

* a Windows 11 client was installed
* the client was configured for domain DNS
* the client joined the `bjorklunda.local` domain
* a domain user logged in successfully
* shared folder access was tested
* incorrect Finance share permissions were found and fixed
* shared printer access was tested
* a basic Group Policy restriction was applied and verified
* support cases were documented
* security and support lessons were reflected on

This project shows practical Windows client support skills in an Active Directory environment.
