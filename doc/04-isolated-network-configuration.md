# Isolated Network Configuration

## Purpose

This document explains how the Kali Linux and Windows 11 virtual machines were configured to communicate through an isolated VirtualBox network.

Kali Linux is used as the authorized security-testing machine, while Windows 11 is used as the monitored endpoint.

The isolated network allows the two virtual machines to communicate without directly exposing the testing environment to the physical home network or other external systems.

---

## Network Objective

The network configuration must allow:

* Kali Linux to communicate with Windows 11
* Windows 11 to communicate with Kali Linux
* Authorized network scanning between the virtual machines
* Controlled security simulations
* Network traffic observation
* Separation from public and third-party systems
* Safe restoration of the environment after testing

Both virtual machines must use:

* The same VirtualBox network mode
* The same virtual network
* IP addresses within the same subnet

---

## Selected Network Mode

The primary network mode selected for this project is:

```text
Internal Network
```

A Internal Network creates a private virtual network between:

* The Kali Linux virtual machine
* The Windows 11 virtual machine
* The physical host computer

The virtual machines can communicate with each other without being directly accessible from the internet.

### Why Host-Only Networking Was Selected

Internal networking was selected because it:

* Keeps the lab separated from the physical home network
* Allows the virtual machines to communicate
* Allows the physical host to communicate with the virtual machines
* Reduces the risk of unintentionally testing external systems
* Supports packet captures and troubleshooting
* Is appropriate for a controlled cybersecurity lab

---

## Network Architecture

```text
┌──────────────────────────┐
│ Physical Host Computer   │
│ Windows + VirtualBox     │
└────────────┬─────────────┘
             │
             │ VirtualBox Internal Network
             │
    ┌────────┴────────┐
    │                 │
┌───▼────────────┐ ┌──▼────────────────┐
│ Kali Linux VM  │ │ Windows 11 VM     │
│ Security Test  │ │ Monitored Endpoint│
└────────────────┘ └───────────────────┘
```

The Kali Linux and Windows 11 systems communicate only through the private virtual network during controlled exercises.

---

## VirtualBox Network Name

Both virtual machines must be attached to the same Internal network.

The network used for this project is:

```text
Network mode: Internal Network
Network name: testNetwork
```

Possible network names may appear as:

```text
VirtualBox testNetwork Ethernet Adapter
```

or:

```text
VirtualBox Internal Network
```

The exact name displayed in VirtualBox should be entered in this document.

---

# Kali Linux Network Configuration

## VirtualBox Adapter Settings

The Kali Linux virtual network adapter was configured using the following settings:

| Setting                | Configuration        |
| ---------------------- | -------------------- |
| Enable Network Adapter | Enabled              |
| Attached To            | Internal Network     |
| Network Name           | testNetwork          |
| Adapter Type           | VirtualBox default   |
| Cable Connected        | Enabled              |
| Promiscuous Mode       | Deny or Allow VMs    |
| MAC Address            | Not published        |

The MAC address is not required for the public project documentation.

---

## Kali Linux IP Address

The Kali Linux network configuration can be viewed with:

```bash
ip address
```

A shorter version of the command is:

```bash
ip addr
```

The interface used for the Host-Only network may appear as:

```text
eth0
```

or:

```text
eth1
```

The exact interface depends on the VirtualBox adapter configuration.

### Kali Linux Address Information

| Network Detail | Value                                   |
| -------------- | --------------------------------------- |
| Interface      | etho                                    |
| IPv4 Address   | 192.168.100.3                           |
| Prefix Length  | Prefix length = /24                     |
| Subnet Mask    | Deafult = 255.255.255.255               |
| Network Type   | Private Internal Network                |



# Windows 11 Network Configuration

## VirtualBox Adapter Settings

The Windows 11 virtual network adapter was configured using the following settings:

| Setting                | Configuration                              |
| ---------------------- | ------------------------------------------ |
| Enable Network Adapter | Enabled                                    |
| Attached To            | Internal Network Adapter                   |
| Network Name           | testNetwork                                |
| Adapter Type           | VirtualBox default                         |
| Cable Connected        | Enabled                                    |
| Promiscuous Mode       | Deny or Allow VMs                          |
| MAC Address            | Not published                              |

The Windows 11 virtual machine must use the exact same Internal network as Kali Linux.

---

## Windows 11 IP Address

The Windows 11 network configuration can be viewed by opening Command Prompt and running:

```cmd
ipconfig
```

For more detailed information, the following command may be used:

```cmd
ipconfig /all
```

### Windows 11 Address Information

| Network Detail  | Value                               |
| --------------- | ----------------------------------- |
| Adapter Name    | testNetwork                         |
| IPv4 Address    | 192.168.100.2                       |
| Subnet Mask     |255.255.255.0                        |
| Default Gateway | May be blank on a Internal  network |
| Network Type    | Private Internal  Network           |


## Same-Subnet Verification

For direct communication, both virtual machines must normally be on the same subnet.

Example of a correct configuration:

```text
Kali Linux:  192.168.56.101/24
Windows 11:  192.168.56.102/24
```

Both addresses begin with:

```text
192.168.56
```

With a `/24` prefix, this indicates that both machines are on the same local network.

Example of an incorrect configuration:

```text
Kali Linux:  192.168.56.101/24
Windows 11:  192.168.100.2/24
```

These addresses are on different `/24` networks and will not normally communicate directly without routing or additional configuration.

---

# IP Address Assignment

The virtual machines may receive IP addresses through:

* VirtualBox Host-Only DHCP
* Manual static configuration

For this project, the addresses should remain consistent so that commands and documentation continue to match.

### Selected Addressing Method

```text
Addressing method: STATIC
```

### Final Address Plan

| System     | IPv4 Address       | Subnet Mask/Prefix     |
| ---------- | ------------------ | ---------------------- |
| Kali Linux | 192.168.100.3      | /24                    |
| Windows 11 | 192.168.100.2      | /24                    |

If static addresses are used, they must not duplicate another device address on the Host-Only network.

---

# Connectivity Testing

After both virtual machines were configured, connectivity was tested in both directions.

## Kali Linux to Windows 11

From the Kali Linux terminal:

```bash
ping -c 4 [WINDOWS-IP-ADDRESS]
```

The `-c 4` option sends four ping requests and then stops automatically.

### Expected Result

A successful test displays replies similar to:

```text
64 bytes from 192.168.100.2
```

### Actual Result

```text
Result: SUCCESSFUL
Packets transmitted: 4
Packets received: 4
Packet loss: 0%
```

---

## Windows 11 to Kali Linux

From Windows Command Prompt:

```cmd
ping [KALI-IP-ADDRESS]
```

### Expected Result

A successful test displays replies similar to:

```text
Reply from 192.168.100.3
```

### Actual Result

```text
Result: SUCCESSFUL 
Packets sent: 4
Packets received: 4
Packet loss: 0%
```

---

## Windows Firewall Consideration

Windows Firewall may block incoming ping requests even when the network configuration is correct.

A failed ping does not always mean that the virtual machines are incorrectly configured.

Before disabling security controls, the following should be checked:

* Both machines use the same network mode
* Both machines use the same network name
* Both IP addresses are on the same subnet
* Both virtual adapters show **Cable Connected**
* The correct IP addresses are being tested
* Both virtual machines are powered on
* The appropriate Windows firewall rule permits ICMP echo requests

The entire Windows Firewall should not be permanently disabled simply to make ping work.

Any temporary firewall change must be:

* Limited to the isolated lab
* Documented
* Reversed after testing when appropriate

---

# Internet Access

The Internal Network Adapter does not normally provide direct internet access.

Temporary internet access may be needed for:

* Operating-system updates
* Security definition updates
* Approved software installation
* Tool downloads

A second NAT adapter may temporarily be added for these purposes.

Example temporary configuration:

| Adapter              | Purpose                                       |
| -------------------- | --------------------------------------------- |
| Adapter 1: Host-Only | Private communication between the lab systems |
| Adapter 2: NAT       | Temporary internet access                     |

Before controlled security exercises, the NAT adapter should be:

* Disabled, or
* Disconnected when it is not required

The attack simulation should not be conducted through a bridged adapter.

---

## Bridged Networking

Bridged networking was not selected for this lab.

A bridged adapter connects the virtual machine more directly to the physical network.

Using bridged networking during an attack simulation could:

* Expose the virtual machines to the home network
* Allow the lab to interact with unrelated devices
* Increase the chance of testing the wrong system
* Create unnecessary security risks

For these reasons, bridged networking should remain disabled during the controlled exercises.

---

# Network Verification Commands

## Kali Linux Commands

Display network interfaces:

```bash
ip address
```

Display the routing table:

```bash
ip route
```

Test communication with Windows:

```bash
ping -c 4 [WINDOWS-IP]
```

Display nearby systems learned by the machine:

```bash
ip neigh
```

---

## Windows 11 Commands

Display the network configuration:

```cmd
ipconfig
```

Display detailed network information:

```cmd
ipconfig /all
```

Test communication with Kali Linux:

```cmd
ping [KALI-IP]
```

Display the Windows routing table:

```cmd
route print
```

Display nearby systems learned by Windows:

```cmd
arp -a
```

These commands are used only for network configuration and connectivity verification.

---


## Screenshot Requirements

### Kali Network Adapter Settings

Show:

* Kali Linux selected in VirtualBox
* Network settings open
* Host-Only Adapter selected
* Network name visible
* Cable Connected enabled

### Windows 11 Network Adapter Settings

Show:

* Windows 11 selected in VirtualBox
* Network settings open
* Host-Only Adapter selected
* The same network name used by Kali
* Cable Connected enabled

### Kali IP Address

Show the result of:

```bash
ip address
```

The relevant interface and private IPv4 address should be visible.

### Windows 11 IP Address

Show the result of:

```cmd
ipconfig
```

The relevant adapter, IPv4 address, and subnet mask should be visible.

### Kali-to-Windows Connectivity

Show the successful result of:

```bash
ping -c 4 [WINDOWS-IP]
```

### Windows-to-Kali Connectivity

Show the successful result of:

```cmd
ping [KALI-IP]
```

Screenshots must not reveal:

* Passwords
* Personal email addresses
* Public IP addresses
* Authentication tokens
* Personal files
* Sensitive host information

---

---

# Network Configuration Evidence

## Kali Linux VirtualBox Adapter

```markdown
![Kali Linux network adapter settings](../screenshots/04-kali-network-adapter-settings.png)

*Figure 1: Kali Linux Host-Only Adapter configuration.*
```

## Windows 11 VirtualBox Adapter

```markdown
![Windows 11 network adapter settings](../screenshots/04-windows11-network-adapter-settings.png)

*Figure 2: Windows 11 connected to the same Host-Only network.*
```

## Kali Linux IP Configuration

```markdown
![Kali Linux IP address](../screenshots/04-kali-ip-address.png)

*Figure 3: Private IPv4 address assigned to Kali Linux.*
```

## Windows 11 IP Configuration

```markdown
![Windows 11 IP address](../screenshots/04-windows11-ip-address.png)

*Figure 4: Private IPv4 address assigned to Windows 11.*
```

## Kali Linux to Windows 11 Test

```markdown
![Kali Linux pinging Windows 11](../screenshots/04-kali-to-windows-ping.png)

*Figure 5: Successful communication from Kali Linux to Windows 11.*
```

## Windows 11 to Kali Linux Test

```markdown
![Windows 11 pinging Kali Linux](../screenshots/04-windows-to-kali-ping.png)

*Figure 6: Successful communication from Windows 11 to Kali Linux.*
```

Remove the surrounding Markdown code fences when adding these image links to the final document so GitHub displays the actual images.

---

# Problems Encountered

Document actual networking problems using the following format:

```text
Problem:
Describe what did not work.

Cause:
Explain why the issue occurred.

Solution:
Explain how the problem was corrected.

Result:
Explain whether communication worked afterward.

Lesson:
Explain what was learned.
```

Example:

```text
Problem:
Kali Linux could not communicate with Windows 11.

Cause:
The virtual machines were connected to different Host-Only networks.

Solution:
Both VirtualBox adapters were changed to the same Host-Only network.

Result:
The two virtual machines successfully communicated.

Lesson:
Both virtual machines must use the same virtual network and compatible IP addresses.
```

Only include this example as an actual finding if this problem occurred during the project.

---


---

# Completion Criteria

This stage is complete when:

* Both virtual machines use the Host-Only Adapter.
* Both virtual machines use the same Host-Only network.
* Kali Linux has a valid private IPv4 address.
* Windows 11 has a valid private IPv4 address.
* Both addresses are on the same subnet.
* Kali Linux can communicate with Windows 11.
* Windows 11 can communicate with Kali Linux.
* Bridged networking is not being used.
* Any temporary NAT adapter is documented.
* Relevant screenshots have been collected.
* Actual IP addresses and results have been entered into this document.
* No sensitive information has been published.

---



Snapshots should be created only after both virtual machines are functioning correctly and can communicate through the isolated network.

