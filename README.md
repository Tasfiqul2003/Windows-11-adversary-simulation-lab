# Windows 11 Adversary Simulation Lab

## Project Overview

This project documents the creation of an isolated cybersecurity lab containing a Kali Linux testing machine and a Windows 11 target machine.

The purpose of the lab is to practice authorized adversary simulation, observe how security events appear on a Windows endpoint, and study how defensive tools can detect and investigate suspicious activity.

All testing is performed only inside virtual machines that I own and control. The lab is isolated from production devices and external systems.

## Project Objectives

* Build a safe and isolated virtual cybersecurity environment.
* Configure Kali Linux as the security-testing machine.
* Configure Windows 11 as the monitored endpoint.
* Practice network discovery and service enumeration.
* Simulate controlled command-and-control behavior.
* Study reverse-shell activity in an authorized lab.
* Examine keystroke-logging behavior from a defensive detection perspective.
* Collect screenshots, logs, and indicators of compromise.
* Document detection, investigation, and remediation steps.
* Improve practical networking, Linux, Windows, and incident-response skills.

## Lab Environment

| Component                  | Purpose                                         |
| -------------------------- | ----------------------------------------------- |
| Kali Linux                 | Authorized security-testing machine             |
| Windows 11                 | Monitored lab endpoint                          |
| VirtualBox                 | Virtualization platform                         |
| Host-only/Internal Network | Isolated communication between virtual machines |
| Windows Defender           | Endpoint protection and alert observation       |
| Wireshark                  | Network traffic analysis                        |
| Sysmon                     | Detailed Windows event logging                  |
| Event Viewer               | Windows log investigation                       |

## Lab Architecture

```text
┌──────────────────────┐
│     Kali Linux       │
│ Security Testing VM  │
│                      │
│ Reconnaissance       │
│ Traffic Generation   │
│ Attack Simulation    │
└──────────┬───────────┘
           │
           │ Isolated Virtual Network
           │
┌──────────▼───────────┐
│     Windows 11       │
│ Monitored Endpoint   │
│                      │
│ Event Logs           │
│ Defender Alerts      │
│ Sysmon Telemetry     │
└──────────────────────┘
```

## Activities Documented

### 1. Virtual Lab Creation

* Installed Kali Linux and Windows 11 as virtual machines.
* Configured an isolated virtual network.
* Confirmed communication between the machines.
* Created virtual-machine snapshots before testing.

### 2. Network Reconnaissance

* Identified the lab endpoint.
* Examined available services in the isolated environment.
* Documented the commands used and their results.
* Compared expected and unexpected network activity.

### 3. Reverse-Shell Simulation

* Studied how an authorized reverse connection behaves inside an isolated lab.
* Observed network connections and endpoint activity.
* Recorded relevant logs and detection results.
* Documented defensive recommendations.

### 4. Keystroke-Logging Detection Exercise

* Studied the security risks associated with unauthorized input capture.
* Focused on detection indicators rather than collecting real credentials.
* Examined relevant process, file, and endpoint activity.
* Documented prevention and mitigation methods.

### 5. Detection and Investigation

* Reviewed Windows Event Viewer logs.
* Examined Sysmon telemetry.
* Reviewed Windows Defender alerts.
* Analyzed network traffic with Wireshark.
* Recorded indicators of compromise.
* Documented investigation and remediation steps.

## Skills Demonstrated

* VirtualBox
* Kali Linux
* Windows 11
* TCP/IP networking
* Network reconnaissance
* Windows Event Viewer
* Sysmon
* Windows Defender
* Wireshark
* Security event analysis
* Incident investigation
* Technical documentation
* Adversary simulation
* Defensive security monitoring

## Safety and Authorization

This repository is intended strictly for education, defensive security research, and authorized testing.

All activities were performed inside an isolated virtual environment using systems that I own and control. Nothing in this project should be used against systems without clear and explicit authorization.

Sensitive information, credentials, weaponized malware, persistence mechanisms, and deployable malicious payloads are not included in this repository.

## Evidence of Completion

The repository includes:

* Lab architecture diagrams
* Virtual-machine configuration screenshots
* Connectivity-testing results
* Sanitized command output
* Windows security logs
* Network-analysis screenshots
* Detection findings
* Troubleshooting notes
* Lessons learned

## Key Lessons Learned

This project helped me understand how offensive activity can appear from both the attacker and defender perspectives. I gained experience building an isolated cyber range, troubleshooting connectivity, examining network traffic, reviewing Windows logs, and documenting security findings.

## Future Improvements

* Add a SIEM platform for centralized log collection.
* Create detection rules for suspicious network connections.
* Add PowerShell logging.
* Map observed activity to MITRE ATT&CK techniques.
* Build an incident-response playbook.
* Automate selected log-analysis tasks with Python.

## Disclaimer

This project is for authorized educational use only. Do not test techniques against systems, accounts, networks, or applications without explicit permission.



















