# Virtual Machine Installation

## Purpose

This document explains how the Kali Linux and Windows 11 virtual machines were installed and configured for the Windows 11 Adversary Simulation Lab.

The two virtual machines run inside Oracle VirtualBox on a Windows host computer.

Kali Linux is used as the authorized security-testing system, while Windows 11 is used as the monitored endpoint.

---

## Virtualization Platform

The virtual machines were created and managed using:

```text
Oracle VirtualBox
```

VirtualBox allows both operating systems to run separately from the physical host computer.

It also provides:

* Virtual CPU and memory allocation
* Virtual storage
* Virtual network adapters
* Snapshot and recovery features
* Separation between the lab and the physical computer
* The ability to restore a virtual machine after a controlled exercise

---

## Virtual Machines Used

The lab includes two virtual machines:

| Virtual Machine | Purpose                             |
| --------------- | ----------------------------------- |
| Kali Linux      | Authorized security-testing machine |
| Windows 11      | Monitored lab endpoint              |

Both virtual machines are owned and controlled by the lab operator.

---

# Kali Linux Virtual Machine Installation

## Kali Linux Purpose

Kali Linux is used for authorized security testing inside the isolated lab.

It provides security tools that can be used for:

* Network discovery
* Port scanning
* Service enumeration
* Controlled attack simulations
* Network traffic analysis
* Vulnerability testing
* Security research
* Defensive investigation support

---

## Kali Linux Installation Source

Kali Linux was installed using an official Kali Linux image.

Possible installation formats include:

* Kali Linux VirtualBox image
* Kali Linux ISO file

The installation file should only be downloaded from the official Kali Linux website or another trusted source.

---

## Kali Linux Virtual Machine Resources

The following resources were assigned to the Kali Linux virtual machine:

| Setting          | Allocation                                    |
| ---------------- | --------------------------------------------- |
| Operating System | Kali Linux 64-bit                             |
| Processor Cores  | 2                                             |
| Memory           | 4 GB RAM                                      |
| Virtual Disk     | Approximately 50 GB                           |
| Graphics Memory  | VirtualBox default or recommended setting     |
| Network Adapter  | Configured later for the isolated lab network |

These settings provide enough resources for normal Kali Linux operation while leaving memory and processing power available for the Windows 11 virtual machine and the host computer.

The resource values should be updated in this document if the actual virtual-machine settings are different.

---

## Kali Linux Virtual Machine Creation

The Kali Linux virtual machine was created using the following general process:

1. Opened Oracle VirtualBox.
2. Selected the option to create or import a virtual machine.
3. Entered a descriptive virtual-machine name.
4. Selected Linux as the operating-system type.
5. Selected the appropriate 64-bit Linux version.
6. Assigned processor cores and memory.
7. Created or attached a virtual hard disk.
8. Attached the Kali Linux ISO or imported the VirtualBox image.
9. Started the virtual machine.
10. Completed the operating-system installation.
11. Created a Kali Linux user account.
12. Confirmed that Kali Linux started successfully.

Suggested virtual-machine name:

```text
Kali-Linux-Attacker
```

A professional alternative is:

```text
Kali-Security-Testing
```

---

## Kali Linux User Account

A local Kali Linux account was created during installation.

The username and password are not included in the public GitHub repository.

Credentials should never be included in:

* Screenshots
* Markdown files
* Configuration files
* Scripts
* Commit messages
* Public repository descriptions

---

## Kali Linux Verification

After installation, the following items were checked:

* Kali Linux successfully reached the desktop.
* The terminal opened correctly.
* The assigned CPU and memory were recognized.
* The virtual disk was available.
* Basic system commands worked.
* Security tools such as Nmap and Metasploit were available.
* The virtual machine could be shut down and restarted.
* The system time and keyboard layout were correct.

Example verification commands:

```bash
uname -a
```

This displays information about the Linux operating system and kernel.

```bash
free -h
```

This displays the amount of memory available to the virtual machine.

```bash
df -h
```

This displays available storage space.

```bash
ip address
```

This displays the network interfaces and IP addresses.

These commands are used only to confirm that the virtual machine is functioning properly.

---

## Kali Linux Updates

Kali Linux may be updated after installation while temporary internet access is available.

The system should only be updated using trusted repositories.

After required updates and tool installations are complete, the virtual machine can be returned to the isolated lab network.

Any major update should be documented because software versions may affect the results of later exercises.

---

# Windows 11 Virtual Machine Installation

## Windows 11 Purpose

Windows 11 is used as the monitored endpoint in the lab.

It represents a workstation that a security analyst or penetration tester may evaluate in an authorized environment.

The Windows 11 virtual machine is used for:

* Windows security testing
* Endpoint monitoring
* Windows Defender observations
* Event Viewer analysis
* Process monitoring
* Network connection monitoring
* Controlled reverse-connection exercises
* Defensive investigation practice
* Incident-response simulations

---

## Windows 11 Installation Source

Windows 11 was installed using a Windows 11 ISO file.

The ISO file should be downloaded from an official or trusted Microsoft source.

The ISO file was attached to the virtual optical drive in VirtualBox during installation.

---

## Windows 11 Virtual Machine Resources

The following resources were assigned to the Windows 11 virtual machine:

| Setting          | Allocation                                    |
| ---------------- | --------------------------------------------- |
| Operating System | Windows 11 64-bit                             |
| Processor Cores  | 2                                             |
| Memory           | 6 GB RAM                                      |
| Virtual Disk     | Approximately 70 GB                           |
| Graphics Memory  | VirtualBox default or recommended setting     |
| Network Adapter  | Configured later for the isolated lab network |

These settings were selected because the host computer has 16 GB of RAM.

The allocation leaves memory available for:

* Kali Linux
* The Windows host operating system
* VirtualBox
* Documentation tools
* Screenshot tools

The resource values should be updated in this document if the actual Windows 11 virtual-machine settings are different.

---

## Windows 11 Virtual Machine Creation

The Windows 11 virtual machine was created using the following general process:

1. Opened Oracle VirtualBox.
2. Selected **New** to create a virtual machine.
3. Entered a descriptive name for the machine.
4. Selected Microsoft Windows as the operating-system type.
5. Selected Windows 11 64-bit as the version.
6. Assigned processor cores and memory.
7. Created a virtual hard disk.
8. Attached the Windows 11 ISO file.
9. Started the virtual machine.
10. Completed the Windows installation process.
11. Created a local Windows account.
12. Completed the initial Windows setup.
13. Confirmed that Windows started successfully.

Suggested virtual-machine name:

```text
Windows-11-Target
```

A professional alternative is:

```text
Windows-11-Monitored-Endpoint
```

---

## Windows 11 Installation Requirements

Windows 11 may require:

* UEFI support
* Secure Boot support
* TPM 2.0
* Sufficient processor cores
* Sufficient RAM
* Sufficient storage space

VirtualBox settings may need to be adjusted to support these requirements.

The exact settings used should be documented if changes were necessary during installation.

---

## Windows 11 User Account

A local Windows account was created for the lab.

The account is used only inside the isolated virtual environment.

The username and password are not included in the GitHub repository.

Real personal accounts, work accounts, school accounts, and reused passwords should not be used inside the lab.

---

## Windows 11 Administrator Access

Administrator access is needed for some lab configuration tasks, including:

* Changing network settings
* Installing monitoring tools
* Reviewing security settings
* Running administrative commands
* Adjusting Windows Defender settings
* Viewing certain Event Viewer logs
* Installing software used in the lab

Administrator credentials must remain private.

---

## Windows 11 Verification

After installation, the following items were checked:

* Windows 11 successfully reached the desktop.
* The virtual machine restarted correctly.
* The assigned CPU and memory were recognized.
* The virtual disk was available.
* Command Prompt opened successfully.
* PowerShell opened successfully.
* Windows Defender was available.
* Windows Event Viewer opened successfully.
* Task Manager opened successfully.
* Network settings were accessible.

Useful Windows verification commands include:

```powershell
systeminfo
```

This displays information about the Windows operating system, processor, memory, and system configuration.

```powershell
ipconfig
```

This displays the Windows network adapters and IP addresses.

```powershell
Get-ComputerInfo
```

This displays detailed system information in PowerShell.

```powershell
Get-NetAdapter
```

This displays the network adapters recognized by Windows.

---

## Windows Updates

Windows 11 may temporarily be connected to the internet for:

* Windows updates
* Security updates
* Windows Defender updates
* Required software downloads

After updates are complete, the virtual machine should be returned to the isolated lab network before controlled security simulations begin.

Any Windows updates that significantly change the testing environment should be documented.

---

# VirtualBox Guest Additions

VirtualBox Guest Additions may be installed on both virtual machines.

Guest Additions can provide:

* Improved display resolution
* Better mouse integration
* Improved keyboard support
* Shared clipboard functionality
* Drag-and-drop support
* Better virtual-machine performance

Guest Additions are optional for the basic lab.

Shared clipboard and drag-and-drop features should be used carefully because they can increase interaction between the virtual machine and the host computer.

For a more isolated environment, these features may be disabled during controlled security exercises.

---

# Virtual Disk Configuration

Each virtual machine uses a virtual hard disk stored on the host computer.

The disks may be configured as:

* Dynamically allocated
* Fixed size

A dynamically allocated disk grows as data is added, up to its assigned maximum size.

This option can reduce initial storage use but does not remove the need to monitor available host storage.

The approximate virtual disk allocations are:

```text
Kali Linux:
Approximately 50 GB

Windows 11:
Approximately 70 GB
```

VirtualBox snapshots may use additional storage beyond these amounts.

---

# Virtual Machine Resource Management

The physical host computer has 16 GB of RAM.

Both virtual machines should not be assigned the entire amount of available memory.

A reasonable allocation is:

```text
Host Windows operating system:
Approximately 6 GB or more available

Kali Linux:
4 GB RAM

Windows 11:
6 GB RAM
```

This allocation helps prevent:

* Host system freezing
* Slow virtual-machine performance
* Excessive disk usage
* VirtualBox crashes
* Memory shortages

Only the virtual machines needed for the current exercise should be running.

---

# Initial Network Adapter Configuration

During the installation and update stages, a NAT adapter may temporarily be used to provide internet access.

NAT may be used for:

* Downloading updates
* Installing approved software
* Updating antivirus definitions
* Confirming basic internet connectivity

Before controlled security testing begins, the machines should be moved to an isolated network configuration.

The final network configuration is documented in:

```text
04-isolated-network-configuration.md
```

The isolated network may use:

* Host-Only Adapter
* Internal Network

Bridged networking should not be used during controlled attack simulations.

---

# Initial Security Checks

Before performing any security exercises, the following checks should be completed:

* Confirm both virtual machines belong to the lab owner.
* Confirm no real personal files are stored inside either machine.
* Confirm no personal accounts are signed in.
* Confirm no sensitive credentials are stored.
* Confirm the virtual machines are not using bridged networking.
* Confirm Windows Defender is available.
* Confirm Windows Event Viewer is working.
* Confirm both machines can be shut down safely.
* Confirm enough host storage remains for snapshots.
* Confirm the operating systems start without errors.

---

# Screenshots to Collect

The following screenshots should be saved as evidence of the installation:

```text
03-virtualbox-main-window.png
03-kali-vm-settings.png
03-kali-running.png
03-windows11-vm-settings.png
03-windows11-running.png
03-kali-system-information.png
03-windows11-system-information.png
```

Recommended screenshots include:

* VirtualBox showing both virtual machines
* Kali Linux desktop
* Windows 11 desktop
* Kali Linux processor and memory settings
* Windows 11 processor and memory settings
* Kali Linux virtual disk settings
* Windows 11 virtual disk settings
* Basic system information from both machines

Screenshots should not display:

* Passwords
* License keys
* Personal email addresses
* Personal files
* Sensitive usernames
* Public IP addresses
* Authentication tokens

---

# Installation Results

The following installation results were achieved:

| Installation Task                   | Status                      |
| ----------------------------------- | --------------------------- |
| Oracle VirtualBox installed         | Completed                   |
| Kali Linux virtual machine created  | Completed                   |
| Kali Linux started successfully     | Completed                   |
| Windows 11 virtual machine created  | Completed                   |
| Windows 11 started successfully     | Completed                   |
| Kali Linux user account created     | Completed                   |
| Windows 11 local account created    | Completed                   |
| Kali Linux system tools available   | Completed                   |
| Windows Defender available          | Completed                   |
| Windows Event Viewer available      | Completed                   |
| Virtual-machine resources confirmed | To be verified              |
| Guest Additions installed           | To be verified              |
| Operating systems updated           | To be verified              |
| Installation screenshots collected  | To be completed             |
| Clean snapshots created             | Documented in a later stage |

---

# Problems Encountered

Any installation problems should be documented using the following format:

```text
Problem:
Describe what did not work.

Cause:
Explain the reason for the problem, if known.

Solution:
Explain the steps used to correct the problem.

Result:
Explain whether the issue was resolved.

Lesson:
Explain what was learned from the issue.
```

Example:

```text
Problem:
The Windows 11 virtual machine did not start correctly.

Cause:
The virtual machine did not have enough assigned memory.

Solution:
The memory allocation was increased in the VirtualBox settings.

Result:
Windows 11 started successfully.

Lesson:
Windows 11 requires enough memory and processor resources to run properly inside a virtual machine.
```

Only include problems that actually occurred during the project.

---

# Installation Completion Criteria

This stage is complete when:

* Oracle VirtualBox is installed and working.
* Kali Linux has been installed or imported.
* Windows 11 has been installed.
* Both virtual machines start successfully.
* Both systems have local user accounts.
* CPU, memory, and virtual disk resources are assigned.
* Command-line tools open successfully.
* Windows Defender and Event Viewer are available.
* No sensitive personal information is stored inside the virtual machines.
* Installation screenshots have been collected.
* The machines are ready for isolated network configuration.

---

# Next Step

After both virtual machines are installed and functioning, continue to:

```text
04-isolated-network-configuration.md
```

The next stage documents how Kali Linux and Windows 11 are placed on the same isolated VirtualBox network.
