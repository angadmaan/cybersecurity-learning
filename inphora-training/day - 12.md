# Day 12

## Overview

On Day 12 of the cybersecurity training, I explored multiple cybersecurity tools, practiced Linux terminal commands, learned basic WHOIS reconnaissance, and gained hands-on exposure to network packet analysis using Wireshark.

The session focused on understanding how cybersecurity professionals gather information, analyze network traffic, and work with Linux-based security tools.

---

## PentMenu Installation & Setup

We installed **PentMenu** from its GitHub repository and learned how Linux permissions are used to execute programs.

### Commands Used

```bash
cp -r pentmenu Desktop
```
```
cd pentmenu
```
```
chmod +x ./pentmenu
```
```
./pentmenu
```

### What I Learned

* Copying directories using Linux commands.
* Navigating between directories.
* Making files executable using `chmod`.
* Running terminal-based security utilities.
* Exploring menu-driven security tools.

---

## WHOIS Reconnaissance

We were introduced to **WHOIS**, a protocol used to gather publicly available information about domains and websites.

### Example Command

```bash
whois google.com
```

### Information Obtained Through WHOIS

* Domain registration details
* Registrar information
* Registration and expiry dates
* Name server information
* Administrative contact information (when publicly available)

### Importance in Cybersecurity

WHOIS is commonly used for:

* Open Source Intelligence (OSINT)
* Domain investigation
* Security research
* Threat analysis
* Website ownership verification

---

## Network Traffic Analysis with Wireshark

The session included a basic introduction to **Wireshark**, a network protocol analyzer used to inspect network traffic.

### Activities Performed

* Captured traffic on the `eth0` interface.
* Observed packets moving through the network.
* Examined source and destination addresses.
* Explored the Wireshark interface and packet details.

### Applications of Wireshark

* Network troubleshooting
* Protocol analysis
* Security investigations
* Packet inspection
* Understanding network communication

---

## Introduction to UFONet

We also explored **UFONet** and learned its installation process in Linux.

### Commands Used

```bash
cd Downloads
```
```
cd ufonet
```
```
./ufonet --download-nodes
```
```
./ufonet --help
```
```
./ufonet --gui
```

### What I Learned

* Extracting and working with compressed Linux packages.
* Downloading required resources and dependencies.
* Viewing available command-line options.
* Launching graphical interfaces from the terminal.
* Understanding the structure of security-focused tools.

---

## Skills Practiced

* Linux Command Line
* File Permissions Management
* WHOIS Reconnaissance
* Basic OSINT Techniques
* Wireshark Packet Analysis
* Network Monitoring
* Security Tool Installation
* GUI & CLI Tool Usage

---

## Key Takeaways

* Learned how to install and execute Linux-based security tools.
* Explored WHOIS as a reconnaissance and information-gathering technique.
* Captured and analyzed network packets using Wireshark.
* Improved confidence with Linux commands and permissions.
* Gained practical exposure to cybersecurity tools in a controlled environment.
* Continued building foundational cybersecurity and networking skills.

---

## Conclusion

Day 12 focused on information gathering, network traffic analysis, and practical exposure to security tools. Through hands-on exercises with WHOIS, Wireshark, PentMenu, and UFONet, I gained a better understanding of how cybersecurity professionals collect information, analyze network activity, and work within Linux environments.
