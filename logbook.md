# Windows Domain Support Lab

**Name:** Vulkan  
**GitHub:** TheBoochy  
**Project:** Windows Domain Support Lab  
**Focus:** Windows client administration, Active Directory support, domain login testing, shared folders, printers, Group Policy and troubleshooting  

---

## Work log

### 2026-06-22

**Worked on:**  
Project setup and planning.

**What I did:**  
I created the project folder, prepared the folder structure, started the README file and started the logbook for the Windows Domain Support Lab.

**Problems and solutions:**  
No major technical problems occurred during the initial setup.

**Decisions I made:**  
I decided to continue from the Björklunda Admin Lab server environment and create a separate project focused on Windows client and domain support.

**Sources I used:**

* Previous Björklunda Admin Lab environment
* Microsoft documentation about Windows client domain join and Active Directory basics

---

## Part 1 — Repository setup and project planning

In this part I created the local project structure for the Windows Domain Support Lab.

The project continues from the Björklunda Admin Lab server environment. The previous lab created the server side with Active Directory, DNS, users, groups, shared folders and a shared printer. This new lab focuses on the client and support side.

The main goal is to add a Windows client computer to the domain and test common support tasks such as login, shared folder access, printer access, Group Policy and troubleshooting.

### Folder structure

The project folder is:

`Windows-Domain-Support-Lab`

The folder structure is:

| Folder or file | Purpose |
|---|---|
| `docs/` | Extra project documentation |
| `screenshots/` | Screenshot evidence |
| `scripts/` | PowerShell scripts |
| `results/` | Test output and exported results |
| `logbook.md` | Main step-by-step project logbook |
| `README.md` | GitHub project overview |

### Planned lab systems

| System | Role |
|---|---|
| `srv-dc01` | Domain controller, DNS server, file server and print server |
| `client-win01` | Windows client computer joined to the domain |

### Planned project parts

| Part | Topic |
|---|---|
| Part 1 | Repository setup and planning |
| Part 2 | Windows client VM installation |
| Part 3 | Network and DNS configuration |
| Part 4 | Domain join |
| Part 5 | Domain user login testing |
| Part 6 | Shared folder access testing |
| Part 7 | Printer connection testing |
| Part 8 | Basic Group Policy |
| Part 9 | Troubleshooting support cases |
| Part 10 | Security and support reflection |
| Part 11 | Final README and GitHub polish |

### Part 1 status

Part 1 is completed when the local project folder, subfolders, README file and logbook file have been created.