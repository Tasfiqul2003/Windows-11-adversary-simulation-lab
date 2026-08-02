# Network Reconnaissance

## Purpose

This stage used Kali Linux to identify the Windows 11 virtual machine and examine its available network services.

All scanning was performed only against the Windows 11 machine inside the isolated VirtualBox lab.

## Lab Systems

| System     | Role                     | IP Address      |
| ---------- | ------------------------ | --------------- |
| Kali Linux | Security-testing machine | `192.168.100.3` |
| Windows 11 | Monitored endpoint       | `192.168.100.2` |

## Connectivity Check

Before scanning, Kali Linux tested whether the Windows 11 machine was reachable:

```bash
ping -c 4 192.168.100.2
```

Example:

```bash
ping -c 4 192.168.100.2
```

**Result:** `SUCCESSFUL`

## Host Discovery

The following Nmap command checked whether the Windows machine was active:

```bash
nmap -sn 192.168.100.2
```

Example:

```bash
nmap -sn 192.168.100.2
```

The `-sn` option performs host discovery without scanning ports.

**Result:** `[ENTER RESULT]`

## Service and Version Scan

The following command checked for open ports and attempted to identify running services:

```bash
nmap -sV 192.168.100.2
```

The `-sV` option attempts to identify the service and version running on each discovered port.

**Result:** `Nmap scan report for 192.168.100.2`

Example results may include:

| Port     | Service      | Status |
| -------- | -----------  | ------ |
| `135`    | msrpc        | Open   |
| `139`    | netbios-ssn  | Open   |
| `445`    | microsoft-ds | Open   |

Only include ports that were actually shown in your scan.

## Full Port Scan

A full TCP port scan may also be performed:

```bash
nmap -p- 192.168.100.2
```

The `-p-` option checks all TCP ports from 1 through 65535.

This scan may take longer than the basic service scan.

**Result:** Result from full port scan was too long and current machine not powerfull enough, this is an optional port scan.

## Findings

The reconnaissance stage showed that:

* The Windows 11 virtual machine was `REACHABLE`.
* Nmap identified three open port or ports.
* The main services discovered were Microsoft-ds, netbios-ssn and msrpc services.
* All activity remained inside the isolated virtual environment.

Finding an open port does not automatically mean that the system is vulnerable. Additional investigation is needed to understand the service and its security configuration.

## Screenshots

```markdown
![Nmap host discovery](../screenshots/05-nmap-host-discovery.png)

*Figure 1: Nmap confirming that the Windows 11 machine is active.*

![Nmap service scan](../screenshots/05 Host Discovery NMAP)

*Figure 2: Nmap identifying open ports and services.*

![Nmap full port scan](../screenshots/05-Service-and-Version Scan)

```

Remove the final image section for the full port scan if you did not perform it.

## Screenshot Checklist

```text
05-nmap-host-discovery.png
05-nmap-service-scan.png
```

## Safety

* Only the Windows 11 lab machine was scanned.
* No public systems or third-party devices were targeted.
* Both machines were connected through an isolated VirtualBox network.
* The scan results were used for authorized educational purposes.

## Completion Status

| Task                           | Status          |
| ------------------------------ | --------------- |
| Windows connectivity confirmed | Completed       |
| Host discovery scan performed  | Completed       |
| Service scan performed         | Completed       |
| Full port scan performed       | Optional        |
| Results documented             | Completed       |
| Screenshots uploaded           | Completed       |
