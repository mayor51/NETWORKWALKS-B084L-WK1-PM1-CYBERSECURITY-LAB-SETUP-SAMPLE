# NETWORKWALKS-B084L-WK1-PM1-CYBERSECURITY-LAB-SETUP-SAMPLE

# 🔐 Cybersecurity Lab Environment Setup

Building an isolated virtual lab for penetration testing and ethical hacking practice.


## 📌 Project Overview

This project focuses on setting up a virtual cybersecurity and penetration-testing laboratory using Oracle VirtualBox and Kali Linux.

The purpose of the lab is to create a controlled environment where cybersecurity tools, network scanning, reconnaissance, vulnerability assessment, and other security-testing activities can be performed safely and repeatedly.


## 🎯 Objectives

The main objectives of this project are to:

- Install and configure VirtualBox.
- Download and import Kali Linux as a virtual machine.
- Create a private NAT Network for the cybersecurity laboratory.
- Configure network connectivity for Kali Linux.
- Configure and verify the IPv4 address, gateway, and DNS settings.
- Test network connectivity and DNS resolution.
- Create a clean virtual machine snapshot for recovery.
- Document the complete setup procedure.
- Prepare the environment for future cybersecurity exercises.

## 🛡️ Purpose of the Lab

The laboratory provides an isolated environment for cybersecurity learning and authorized penetration-testing practice.

It can be used for:

- Network reconnaissance.
- Port scanning.
- Vulnerability assessment.
- Packet analysis.
- Web application security testing.
- Exploitation practice on authorized targets.
- Security-tool experimentation.

**Security notice:** This laboratory should only be used to test systems you own or have explicit permission to assess.

---

## 🏗️ Lab Architecture

The laboratory consists of a host computer running VirtualBox, with Kali Linux operating as a virtual machine.

The virtual machine connects to a dedicated NAT Network. Additional virtual machines can be connected to the same network for future security exercises.

**Lab components:**

1. Host computer — the physical system running the virtualization software.
2. Oracle VirtualBox — the hypervisor used to manage virtual machines.
3. Kali Linux — the operating system used for security testing.
4. NAT Network — the virtual network providing connectivity to the lab machines.
5. Additional target virtual machines — optional systems for authorized testing.

*Insert a screenshot showing your lab architecture or VirtualBox configuration here.*

---

## ⚙️ Lab Configuration

The following table provides a configuration template. Replace example values with the actual specifications and settings of your system.

```
| Component | Configuration |
|---|---|
| Host OS | Windows (actual version to be recorded) |
| Host RAM | Actual installed memory |
| Processor | Actual processor model |
| Hypervisor | Oracle VirtualBox |
| Security OS | Kali Linux |
| Kali RAM | 2048 MB (example) |
| Virtual Network | NAT Network |
| Network Address | 10.0.2.0/24  |
| Kali IP Address | 10.0.2.4/24  |
| Default Gateway | 8.8.8.8 |
| DNS Server | 8.8.8.8  |

```

# 🪜 Lab Setup Procedure

## Step 1: Install 7-Zip

7-Zip is a file compression and extraction utility used to extract archived files.

It can be used to extract a Kali Linux virtual-machine package when it is provided in a `.7z` archive.

**Tool:** 7-Zip

**Procedure:**

1. Visit the official 7-Zip website.
2. Download the appropriate version for the host operating system.
3. Run the installer and complete the installation.
4. Verify that the application is available for extracting archived files.

**Official website:** https://www.7-zip.org/

## Step 2: Install VirtualBox

Oracle VirtualBox is a virtualization platform that allows multiple operating systems to run as virtual machines on a physical computer.

**Procedure:**

1. Visit the official VirtualBox website.
2. Download the appropriate installer for the host operating system.
3. Run the installer and follow the installation instructions.
4. Open VirtualBox after installation.
5. Confirm that the VirtualBox Manager interface loads correctly.

**Tool:** Oracle VirtualBox

**Official website:** https://www.virtualbox.org/wiki/Downloads


## Step 3: Create the NAT Network

A dedicated NAT Network was prepared for the cybersecurity laboratory.

A NAT Network allows multiple virtual machines connected to the same virtual network to communicate with one another while providing network address translation for external connectivity.

**Procedure:**

1. Open VirtualBox Manager.
2. Navigate to the network management section.
3. Create a new NAT Network.
4. Assign a network name, such as `NatNetwork`.
5. Configure the IPv4 network prefix according to the lab subnet.
6. Enable DHCP if automatic address assignment is required.
7. Disable IPv6 only if it is not required for the exercise.
8. Save the network configuration.

**Example configuration:**

```text
Network Name: NatNetwork
IPv4 Prefix: 10.0.2.4/24
DHCP: Enabled
IPv6: Disabled
```

These values are examples and must be checked against the actual lab configuration.

![VirtualBox NAT Network settings](screenshots/VirtualBox%20NAT%20Network%20settings.png)

## Step 4: Download and Import Kali Linux

Kali Linux is a Linux distribution designed for penetration testing, digital forensics, and security assessment.

A prebuilt Kali virtual machine can be imported into VirtualBox to reduce the need for manual operating-system installation.

**Procedure:**

1. Visit the official Kali Linux website.
2. Download a VirtualBox-compatible virtual-machine image.
3. Extract the archive if necessary.
4. Open VirtualBox Manager.
5. Import the virtual appliance or open the supplied virtual-machine configuration, depending on the downloaded format.
6. Review the virtual-machine settings.
7. Allocate suitable memory and other resources based on the host computer's capacity.

**Example virtual-machine settings:**

```text
Operating System: Kali Linux
Allocated RAM: 4032 MB
Network Adapter: NAT Network
Network Name: NatNetwork 1
```

![kali linux virtual](screenshots/kali%20linux%20virtual%20.png.png)

## Step 5: Configure the Kali Linux Network

After importing Kali Linux, the virtual network adapter should be checked to ensure that it is connected to the intended NAT Network.

The network configuration should include an appropriate IPv4 address, subnet mask, gateway, and DNS server.

**Example network configuration:**

```text
IP Address:     10.0.0.2
Subnet Mask:    255.255.255.0
Gateway:        10.0.0.1
DNS Server:     8.8.8.8
```

**Procedure:**

1. Start the Kali Linux virtual machine.
2. Log in to the operating system.
3. Open a terminal.
4. Run `ip a` to identify the network interfaces and assigned IP addresses.
5. Check the active network connection and its IPv4 settings.
6. Configure a static IP address only if required by the lab design.
7. Verify that the configured address belongs to the intended subnet.
8. Confirm that the gateway and DNS settings are appropriate for the virtual network.

![configure network](screenshots/configure%20network.png)

## Step 6: Create a Clean Virtual Machine Snapshot

A virtual-machine snapshot records the state of a virtual machine at a particular point in time.

A clean snapshot is useful because it provides a recovery point before subsequent cybersecurity exercises modify the operating system or its configuration.

**Procedure:**

1. Complete the initial Kali Linux setup.
2. Confirm that the virtual machine starts correctly.
3. Verify the network configuration.
4. Shut down or prepare the virtual machine according to VirtualBox's snapshot requirements.
5. Open the snapshot management interface.
6. Create a snapshot with a descriptive name.

**Example snapshot name:**

```text
Clean Kali - Network Setup
```

The snapshot should represent a known-good baseline of the laboratory.

If a future exercise causes configuration problems, the virtual machine can be restored to the saved state.


---

# 🔎 Lab Verification

After completing the setup, the virtual machine's network configuration and basic connectivity should be tested.

The following commands can be used to perform the checks.

| Test | Command | Expected Result |
|---|---|---|
| Check IP address | `ip a` | The intended IP address is displayed |
| Check routing table | `ip route` | The expected route and gateway are displayed |
| Test gateway | `ping -c 4 10.0.0.1` | Replies are received if the gateway responds to ICMP |
| Test external connectivity | `ping -c 4 8.8.8.8` | Replies are received if ICMP traffic is permitted |
| Test DNS resolution | `nslookup networkwalks.com` | The domain resolves to an IP address |
| Verify Nmap | `nmap --version` | The installed Nmap version is displayed |

The example IP addresses must be replaced if the actual network uses a different subnet.

**Important:** Expected results are not actual results. Run the commands and document the output observed on your own system. A failed ping does not always mean the network is unavailable because ICMP traffic may be filtered.

### Example Results Format

Record your actual results using a format similar to the following:

```text
Kali IP Address:
10.0.2.4

Default Gateway:
8.8.8.8

DNS Resolution:
8.8.8.8

```


# 🐞 Problems Encountered and Solutions

This section should document problems encountered during the setup, their causes, and the solutions applied.

## Problem 1: Internet Connectivity After Static IP Configuration

Manually configuring an IPv4 address can result in connectivity problems if the IP address, gateway, DNS settings, or network connection profile is incorrect.

**Troubleshooting procedure:**

1. Run `ip a` to check the assigned IP address.
2. Run `ip route` to inspect the routing table.
3. Check the active network connection profile.
4. Verify the configured gateway and DNS server.
5. Restart the affected connection if necessary.
6. Test connectivity and DNS resolution again.

The exact solution depends on the cause of the problem. Record the actual error message and the command used to resolve it.

## Problem 2: VirtualBox Virtualization Error

A virtual machine may fail to start if hardware virtualization is unavailable or disabled in the computer's firmware settings.

**Troubleshooting procedure:**

1. Read the error message displayed by VirtualBox.
2. Restart the computer if a firmware setting needs to be changed.
3. Enter the BIOS/UEFI configuration interface.
4. Check whether hardware virtualization is enabled.
5. Enable the appropriate virtualization setting if necessary and permitted.
6. Save the changes and restart the computer.
7. Start the virtual machine again.

The exact menu name varies by computer manufacturer and processor platform.



---

# 💡 What I Learned

Through this project, I developed an understanding of how to prepare a virtual environment for cybersecurity practice.

### 1. Virtualization

I learned that virtualization makes it possible to run separate operating systems on one physical computer. This is useful for building cybersecurity labs without requiring a separate physical computer for every system.

### 2. NAT and NAT Network

I learned that standard NAT and NAT Network configurations serve different purposes. A NAT Network can allow multiple connected virtual machines to communicate with one another while providing outbound network connectivity.

### 3. Virtual Machine Networking

I learned how virtual network adapters connect virtual machines to different network configurations and how those settings influence communication between systems.

### 4. IPv4 Configuration

I learned about IPv4 addresses, subnet masks, gateways, and DNS servers, and how to inspect these settings using Linux networking commands.

### 5. Virtual Machine Snapshots

I learned the importance of saving a known-good virtual-machine state before performing experimental activities. A snapshot can make recovery easier when a lab configuration needs to be restored.

### 6. Network Verification

I learned how to use commands such as `ip a`, `ip route`, `ping`, and `nslookup` to inspect network settings and troubleshoot connectivity.

### 7. Technical Documentation

I learned that a professional cybersecurity project should document the tools used, configuration settings, commands executed, verification results, problems encountered, and solutions applied.

---

# 🔐 Security and Ethical Use

This laboratory is intended for educational purposes and authorized security testing.

All scanning, vulnerability assessment, and exploitation exercises should be restricted to systems owned by the tester or explicitly authorized for testing.

Vulnerable virtual machines should be configured carefully to reduce the risk of exposing them to unintended networks.

---

# 🔗 Tools and Resources

- **7-Zip:** https://www.7-zip.org/
- **Oracle VirtualBox:** https://www.virtualbox.org/wiki/Downloads
- **Kali Linux:** https://www.kali.org/get-kali/
- **Kali Linux Documentation:** https://www.kali.org/docs/
- **Nmap:** https://nmap.org/
- **PortSwigger Web Security Academy:** https://portswigger.net/web-security

---

## 📌 Project Information

Program Name: Cybersecurity at Networkwalks

Week: 01

Project: Cybersecurity and Penetration-Testing Lab Setup

Repository Name: `NETWORKWALKS-B084L-WK1-PM1-CYBERSECURITY-LAB-SETUP-SAMPLE`
