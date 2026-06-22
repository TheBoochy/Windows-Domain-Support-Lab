# Windows Domain Support Lab

## Overview

Windows Domain Support Lab is a voluntary portfolio project focused on Windows client administration, Active Directory domain support, user login testing, shared folder access, printer access, basic Group Policy and troubleshooting.

The lab continues from the Björklunda Admin Lab server environment.

## Scenario

A small organization already has a Windows Server domain environment with Active Directory, DNS, users, groups, shared folders and a shared printer.

The goal of this project is to add a Windows client computer to the domain and test common IT support tasks from a client and user perspective.

## Planned environment

| System | Role |
|---|---|
| `srv-dc01` | Domain controller, DNS server, file server and print server |
| `client-win01` | Windows client computer joined to the domain |

## Planned tasks

- Create a Windows client VM
- Configure hostname and network settings
- Join the client to the `bjorklunda.local` domain
- Log in with domain users
- Test shared folder access
- Test denied access for wrong department users
- Connect to a shared printer
- Configure basic Group Policy
- Document troubleshooting and support cases

## Skills demonstrated

- Windows client administration
- Active Directory domain join
- DNS and network troubleshooting
- User login testing
- File share permission testing
- Printer support
- Group Policy basics
- IT support documentation
- Git and GitHub documentation workflow