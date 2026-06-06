# Day 5

## Topics Covered

- Kali Linux
- VirtualBox
- Installing Kali Linux using ISO File
- Virtual Machine Configuration
- Troubleshooting Installation Errors

---

# Kali Linux

Kali Linux is a Debian-based Linux distribution designed for cybersecurity and penetration testing.

It contains numerous security tools used for:
- Information Gathering
- Vulnerability Assessment
- Wireless Testing
- Digital Forensics
- Penetration Testing

---

# VirtualBox

VirtualBox is a virtualization software that allows users to run multiple operating systems on a single computer.

Benefits:
- Safe testing environment
- Isolation from host system
- Easy snapshot and recovery options

---

# Installing Kali Linux

## Requirements

- Kali Linux ISO file
- VirtualBox
- Sufficient RAM and Storage

---

## Installation Steps

1. Download Kali Linux ISO.
2. Install VirtualBox.
3. Create a new virtual machine.
4. Allocate RAM and storage.
5. Attach the Kali Linux ISO file.
6. Start the virtual machine.
7. Follow the installation wizard.
8. Create username and password.
9. Complete installation and reboot.

---

# Virtual Machine Configuration

Important settings:

- RAM Allocation
- CPU Cores
- Storage Size
- Network Adapter

Proper configuration improves performance and stability.

---

# Troubleshooting Common Errors

## Virtualization Disabled

Cause:
Virtualization Technology (VT-x/AMD-V) disabled in BIOS.

Solution:
Enable virtualization in BIOS settings.

---

## Insufficient RAM

Cause:
Low memory allocation.

Solution:
Increase RAM assigned to the virtual machine.

---

## Boot Errors

Cause:
Incorrect ISO selection or corrupted ISO file.

Solution:
Verify ISO integrity and reconnect the ISO file.

---

## Guest Additions Issues

Cause:
Missing VirtualBox Guest Additions.

Solution:
Install Guest Additions for improved performance and display support.

## Secure Boot Enabled

Cause:
Secure Boot enabled in BIOS may prevent VirtualBox from working properly on some systems.

Solution:
Disable Secure Boot from the Boot settings in BIOS and then restart the system.

---

# Key Learning

Virtualization allows safe cybersecurity practice without affecting the host operating system. Kali Linux is one of the most widely used operating systems for cybersecurity professionals and penetration testers.
