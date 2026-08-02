# Adversary Simulation and Detection

## Purpose

This stage documents a controlled adversary-simulation exercise performed inside my isolated VirtualBox lab.

Kali Linux was used as the authorized security-testing machine, while Windows 11 was used as the monitored endpoint. The purpose was to observe the process of establishing a controlled reverse connection and understand what evidence the activity creates for a security analyst.

All testing was performed only against virtual machines that I own and control.

---

## Lab Environment

| System | Role |
|---|---|
| Kali Linux | Authorized security-testing machine |
| Windows 11 | Monitored endpoint |
| Oracle VirtualBox | Virtualization platform |
| Host-Only Network | Isolated communication between the virtual machines |
| Metasploit Framework | Session management and controlled simulation |
| Social-Engineer Toolkit | Lab exercise configuration |
| Apache2 | Local hosting inside the isolated lab |

---

## Exercise Objective

The objectives of this exercise were to:

- Perform a controlled adversary simulation in an isolated environment.
- Observe how a reverse TCP connection is established.
- Practice using Kali Linux security-testing tools.
- Confirm access only to the authorized Windows 11 virtual machine.
- Record evidence of the session.
- Identify activity that a SOC analyst could investigate.
- Document the risks and defensive lessons associated with reverse connections.

---

## Safety Controls

The following safety controls were used:

- Both virtual machines were owned and controlled by me.
- The exercise was limited to a private VirtualBox network.
- No public systems or third-party devices were targeted.
- No real credentials or personal information were collected.
- The activity was performed for education and defensive-security learning.
- Screenshots were reviewed before being uploaded to GitHub.
- The environment could be restored using VirtualBox snapshots.

---

# Exercise Walkthrough

## 1. Starting the Social-Engineer Toolkit

The Social-Engineer Toolkit was opened on Kali Linux as part of the controlled lab exercise.

This tool provided the interface used to configure the test activity inside the isolated environment.

![Social-Engineer Toolkit used](../screenshots/06%20Setooklit%20Used(1).png)

**Evidence shown:**

- The toolkit was running on Kali Linux.
- The exercise was being configured from the authorized testing machine.
- The activity was limited to the virtual lab.

---

## 2. Configuring the Reverse TCP Exercise

The reverse TCP connection settings were configured using the private IP address assigned to the Kali Linux virtual machine.

A reverse connection causes the monitored endpoint to initiate a connection back to the testing machine. In a real incident, this type of behavior could indicate unauthorized remote access or command-and-control activity.

![Reverse TCP shell setup](../screenshots/06%20Reverse%20TCP%20Shell%20Setup(1).png)

**Security significance:**

A SOC analyst may investigate:

- An unexpected outbound connection
- An unusual destination port
- A process communicating with another system
- A connection to an unauthorized internal or external address
- A process that creates a command shell

---

## 3. Starting the Apache2 Service

Apache2 was started on Kali Linux to provide local web-hosting functionality within the isolated virtual network.

The web service was used only inside the controlled lab and was not intended to expose files publicly.

![Apache2 service setup](../screenshots/06%20Apache%202%20set%20up(2).png)

**Evidence shown:**

- Apache2 was started on Kali Linux.
- The service was available to the virtual lab network.
- The Kali machine was prepared to host the controlled test artifact.

---

## 4. Preparing the Controlled Test Artifact

The controlled test artifact was placed in the Apache2 web directory so it could be accessed by the Windows 11 virtual machine inside the isolated environment.

![Setting up the test artifact with Apache2](../screenshots/06%20Setting%20up%20Payload%20using%20Apache2.png)

**Security significance:**

In a real investigation, a SOC analyst may examine:

- Recently downloaded executable files
- Browser download history
- File-creation timestamps
- Files created in the Downloads directory
- Web-server access logs
- Connections between the endpoint and the hosting system
- Antivirus or endpoint-protection alerts

The actual test artifact is not included in this public repository.

---

## 5. Confirming the Session

After the controlled file was executed inside the Windows 11 lab machine, Kali Linux displayed confirmation that a Meterpreter session had been created.

![Meterpreter session confirmation](../screenshots/06%20Meterpreter%20Session%20Start%20Confirmation.png)

This confirmed that the Windows 11 endpoint established a connection back to the Kali Linux machine.

**Evidence shown:**

- A session was successfully created.
- The connection occurred between the two lab virtual machines.
- The controlled simulation produced observable remote-access behavior.

---

## 6. Viewing Active Sessions

The active-session command was used to verify that the controlled session was available in Metasploit.

![Active sessions in Metasploit](../screenshots/06%20Active%20Sessions%20with%20Msfconsole.png)

This step confirmed that Metasploit recognized the connection and assigned it a session number.

**SOC relevance:**

A defender could search for:

- Unexpected long-running TCP connections
- Connections to unusual ports
- Suspicious parent-child process relationships
- Command shells started by unexpected applications
- Recently created executable files
- Endpoint-protection alerts associated with the process

---

## 7. Opening the Controlled Command Shell

The active lab session was selected, and a Windows command shell was opened.

![Reverse shell created](../screenshots/06%20Reverse%20Shell%20Created.png)

The screenshot shows that the shell was operating from the authorized Windows 11 virtual machine.

The visible directory was:

```text
C:\Users\Victim\Downloads
