# Lab Requirements

## Purpose

This document lists the hardware, software, virtual machines, security tools, and storage requirements needed to build the Windows 11 Adversary Simulation Lab.

The lab uses Kali Linux as the authorized security-testing machine and Windows 11 as the monitored endpoint. Both machines run inside Oracle VirtualBox and communicate through an isolated virtual network.

---

## Host Computer

The host computer is the physical computer running VirtualBox and the virtual machines.

### Host System Specifications

| Component               | Host Computer                                  |
| ----------------------- | ---------------------------------------------- |
| Computer Model          | Dell G7 7700                                   |
| Operating System        | Windows                                        |
| Processor               | Intel Core i7-10750H                           |
| Memory                  | 16 GB RAM                                      |
| Storage                 | 512 GB NVMe SSD                                |
| Graphics                | NVIDIA GeForce RTX 2070 and Intel UHD Graphics |
| Virtualization Platform | Oracle VirtualBox                              |

### Recommended Host Requirements

The host computer should have:

* A 64-bit processor
* Hardware virtualization support
* At least 16 GB of RAM
* At least 100 GB of available storage
* A stable internet connection for initial downloads
* Administrator access to install software
* Virtualization enabled in the BIOS or UEFI settings

My computer meets the main processor and memory requirements for running the two virtual machines. Available storage should be checked before creating or expanding the virtual machines.

---

## Virtualization Software

### Oracle VirtualBox

Oracle VirtualBox is used to create and manage the virtual lab.

VirtualBox provides:

* Virtual-machine creation
* Virtual network adapters
* Isolated networking
* Snapshot creation
* Resource allocation
* Virtual disk management
* Recovery to previous machine states

### VirtualBox Extension Pack

The VirtualBox Extension Pack may be installed for additional features.

It is not required for the basic lab but may provide:

* Improved USB support
* Remote display features
* Additional VirtualBox functionality

---

## Virtual Machines

The lab requires two virtual machines.

### Kali Linux Virtual Machine

Kali Linux is used as the authorized security-testing machine.

Recommended Kali Linux resources:

| Resource         | Allocation                    |
| ---------------- | ----------------------------- |
| Processor Cores  | 2                             |
| Memory           | 4 GB RAM                      |
| Virtual Disk     | 40–60 GB                      |
| Network Adapter  | Host-Only or Internal Network |
| Operating System | Kali Linux 64-bit             |

Kali Linux is used for:

* Network discovery
* Service enumeration
* Authorized attack simulation
* Network traffic generation
* Security testing
* Traffic analysis

---

### Windows 11 Virtual Machine

Windows 11 is used as the monitored endpoint.

Recommended Windows 11 resources:

| Resource         | Allocation                    |
| ---------------- | ----------------------------- |
| Processor Cores  | 2–4                           |
| Memory           | 6–8 GB RAM                    |
| Virtual Disk     | 64–80 GB                      |
| Network Adapter  | Host-Only or Internal Network |
| Operating System | Windows 11 64-bit             |

Windows 11 is used for:

* Endpoint monitoring
* Windows Event Viewer analysis
* Windows Defender testing
* Process monitoring
* Network connection monitoring
* Controlled security simulations

Because the host computer has 16 GB of RAM, both virtual machines should not be assigned excessive memory at the same time.

A reasonable starting allocation is:

```text
Kali Linux:
- 4 GB RAM
- 2 processor cores
- 50 GB virtual disk

Windows 11:
- 6 GB RAM
- 2 processor cores
- 70 GB virtual disk
```

This leaves memory available for the host operating system.

---

## Operating-System Installation Files

The following installation files are required:

* Kali Linux VirtualBox image or ISO file
* Windows 11 ISO file
* Oracle VirtualBox installer
* Optional VirtualBox Extension Pack

The operating-system files should only be downloaded from official or trusted sources.

The ISO and installer files should be stored in a clearly labeled folder on the host computer.

Example:

```text
Cyber-Lab-Installers/
├── Kali-Linux/
├── Windows-11/
├── VirtualBox/
└── Security-Tools/
```

---

## Network Requirements

The Kali Linux and Windows 11 virtual machines must be connected to the same isolated virtual network.

Recommended network modes:

* Host-Only Adapter
* Internal Network

These network modes allow the virtual machines to communicate without directly exposing the testing environment to the physical home network.

Bridged networking should not be used during controlled attack simulations.

Internet access may temporarily be enabled for:

* Operating-system updates
* Tool installation
* Security definition updates

Internet access should be disabled or separated from the testing adapter before performing controlled simulations.

---

## Windows Security and Monitoring Tools

### Windows Defender

Windows Defender is included with Windows 11.

It is used to:

* Detect suspicious files
* Identify potentially malicious activity
* Generate endpoint alerts
* Perform antivirus scans
* Review protection history

Windows Defender should remain enabled unless a specific lab exercise requires testing its behavior.

Any temporary security changes must be documented and reversed after testing.

---

### Windows Event Viewer

Windows Event Viewer is built into Windows 11.

It is used to review:

* Security events
* System events
* Application events
* Logon activity
* Service activity
* PowerShell activity
* Errors and warnings
* Other system activity related to the lab exercises

Windows Event Viewer provides the main source of Windows logs during the first version of this project.

---

### PowerShell Logging

PowerShell logging may be enabled to improve visibility into PowerShell activity.

Relevant logging features may include:

* Script block logging
* Module logging
* PowerShell transcription
* Process creation auditing

These settings can be documented in the Windows security logging setup file if they are enabled during the project.

---

### Windows Task Manager

Windows Task Manager can be used to observe:

* Running processes
* CPU and memory usage
* Applications currently running
* User sessions
* Startup programs
* Basic network usage

Task Manager can help identify changes that occur during a controlled simulation.

---

### Resource Monitor

Windows Resource Monitor can provide additional information about:

* Running processes
* Active network connections
* Listening ports
* Disk activity
* Memory usage
* CPU activity

It can be used to observe which processes communicate with the Kali Linux machine during the lab.

---

## Network Analysis Tools

### Wireshark

Wireshark can be used to capture and analyze network traffic between the virtual machines.

Wireshark can help identify:

* Source and destination IP addresses
* TCP and UDP connections
* Port numbers
* Connection timing
* Protocol activity
* Unexpected network connections

Wireshark may be installed on the host computer, Kali Linux, or Windows 11.

Wireshark is helpful but is not required to begin the basic virtual-machine setup.

---

### Nmap

Nmap is included with Kali Linux and is used for authorized network reconnaissance.

It can help identify:

* Active systems
* Open ports
* Running services
* Service versions
* Basic network exposure

Nmap will only be used against virtual machines that are part of this controlled lab.

---

### Metasploit Framework

Metasploit Framework is included with Kali Linux and may be used for controlled security testing.

It may be used to:

* Perform authorized vulnerability checks
* Test approved modules inside the isolated lab
* Create controlled security events
* Observe how the Windows system responds
* Support defensive investigation exercises

Metasploit will only be used against systems that belong to the lab owner and are included in the isolated virtual environment.

---

## Optional SIEM Platform

A Security Information and Event Management platform may be added during a future version of the project.

Possible platforms include:

* Splunk
* Wazuh
* Elastic Security

A SIEM platform is not required for the first stage of the lab.

Adding a SIEM later would allow the project to include:

* Centralized log collection
* Log searching
* Dashboard creation
* Alert creation
* Detection rules
* Incident investigation
* Event correlation
* Security automation

Splunk or Wazuh may be added as a future improvement after the Kali Linux and Windows 11 environment is fully operational.

---

## Supporting Software

Additional tools that may be used include:

| Tool             | Purpose                                       |
| ---------------- | --------------------------------------------- |
| GitHub           | Project documentation and portfolio evidence  |
| Markdown         | Writing project documentation                 |
| Draw.io          | Creating architecture and network diagrams    |
| Windows Terminal | Running Windows commands                      |
| PowerShell       | Windows administration and logging            |
| Command Prompt   | Basic Windows and network testing             |
| Task Manager     | Viewing running processes and system activity |
| Resource Monitor | Viewing network and resource activity         |
| Hashing Utility  | Calculating file hashes                       |
| Screenshot Tool  | Capturing lab evidence                        |

---

## Storage Requirements

The lab requires storage for:

* Virtual-machine disks
* VirtualBox snapshots
* Operating-system ISO files
* Packet captures
* Screenshots
* Windows logs
* Documentation
* Tool installers

Estimated storage usage:

| Item                         | Estimated Space |
| ---------------------------- | --------------: |
| Kali Linux VM                |        40–60 GB |
| Windows 11 VM                |        64–80 GB |
| Snapshots                    |       20–50+ GB |
| Installation Files           |        10–20 GB |
| Screenshots and Logs         |         1–10 GB |
| Total Recommended Free Space | At least 100 GB |

Snapshot files can become large. Old or unnecessary snapshots should be removed carefully after confirming that they are no longer needed.

---

## Required Accounts

The following accounts may be needed:

* GitHub account
* Local Windows administrator account
* Kali Linux user account
* Optional Splunk account
* Optional Wazuh account
* Optional Microsoft account for Windows activation or downloads

No passwords or account credentials will be stored in the public GitHub repository.

---

## Safety Requirements

Before beginning the lab:

* Confirm that both virtual machines belong to the lab owner.
* Use only private virtual-machine IP addresses.
* Keep the testing network isolated.
* Create clean snapshots before simulations.
* Do not use real passwords during testing.
* Do not test against public websites or third-party systems.
* Do not upload malware, credentials, or sensitive files to GitHub.
* Restore the environment after each controlled simulation.
* Record any security settings that were temporarily changed.
* Only use security tools against systems that are owned and authorized for testing.

---

## Evidence to Collect

The following screenshots should be collected during the requirements and setup stages:

* Host computer system specifications
* VirtualBox installed on the host computer
* Kali Linux virtual-machine settings
* Windows 11 virtual-machine settings
* CPU and RAM allocations
* Virtual disk sizes
* Network adapter settings
* Both virtual machines successfully powered on

Suggested screenshot filenames:

```text
02-host-system-specifications.png
02-virtualbox-installed.png
02-kali-resource-allocation.png
02-windows11-resource-allocation.png
02-kali-running.png
02-windows11-running.png
```

Screenshots should not reveal passwords, license keys, personal email addresses, usernames containing personal information, or other sensitive details.

---

## Requirement Status

| Requirement                        | Status                      |
| ---------------------------------- | --------------------------- |
| Compatible host computer           | Completed                   |
| 16 GB RAM available                | Completed                   |
| Hardware virtualization available  | To be verified              |
| At least 100 GB free storage       | To be verified              |
| Oracle VirtualBox installed        | Completed                   |
| Kali Linux VM available            | Completed                   |
| Windows 11 VM available            | Completed                   |
| Isolated network available         | Completed                   |
| Windows Defender available         | Completed                   |
| Windows Event Viewer available     | Completed                   |
| Windows Task Manager available     | Completed                   |
| Windows Resource Monitor available | Completed                   |
| Nmap available                     | Completed                   |
| Metasploit Framework available     | Completed                   |
| Wireshark installed                | To be verified              |
| GitHub repository created          | Completed                   |
| SIEM platform installed            | Optional/Future improvement |

---

## Completion Criteria

This stage is complete when:

* VirtualBox is installed and working.
* Kali Linux and Windows 11 are available as virtual machines.
* Both machines have sufficient CPU, memory, and storage.
* The host computer has enough free storage for snapshots.
* Required installation files are available.
* The machines can be placed on an isolated network.
* Windows Defender and Event Viewer are available.
* The required Kali Linux security tools are available.
* Screenshots of the system requirements have been saved.
* No sensitive information has been added to GitHub.

