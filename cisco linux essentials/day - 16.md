# Day 16

## 📌 Overview

Today I completed **Lab 12: Understanding Computer Hardware** from the Cisco Linux Essentials course. This lab focused on exploring Linux commands used to inspect hardware components such as the CPU, memory, storage devices, PCI devices, USB devices, kernel modules, and disk partitions. Understanding these commands is essential for system administration, troubleshooting, and hardware diagnostics.

---

# Commands Learned

## 1. Display CPU Information

### Command

```bash
lscpu
```

### Purpose

Displays detailed information about the processor including:

* CPU architecture
* Number of CPUs and cores
* CPU model
* Virtualization support
* Cache sizes
* CPU flags and capabilities

### Why it's useful

* Verify processor architecture (32-bit/64-bit)
* Check virtualization support
* Identify processor specifications
* Troubleshoot CPU-related issues

---

## 2. View Detailed CPU Information

### Command

```bash
head -n 20 /proc/cpuinfo
```

### Purpose

Displays the first 20 lines of the CPU information file maintained by the Linux kernel.

### Information Available

* Processor number
* Vendor ID
* CPU model
* Cache size
* CPU frequency
* Supported processor flags

### Why it's useful

Provides more detailed hardware information than `lscpu` and is useful when checking CPU capabilities and supported instruction sets.

---

## 3. Display Memory Usage

### Commands

```bash
free -m
```

```bash
free -g
```

### Purpose

Shows RAM and Swap memory usage.

### Options

* `-m` → Display values in Megabytes
* `-g` → Display values in Gigabytes

### Information Displayed

* Total memory
* Used memory
* Free memory
* Buffers/Cache
* Available memory
* Swap usage

### Why it's useful

Helps monitor system memory usage and determine whether the system has sufficient RAM or is relying on swap space.

---

## 4. Display PCI Devices

### Command

```bash
lspci
```

### Purpose

Lists all devices connected to the PCI bus.

### Common Devices Displayed

* Graphics cards
* Network adapters
* Storage controllers
* PCI bridges
* Audio devices

### Why it's useful

Useful for identifying installed hardware and checking whether Linux detects all PCI devices correctly.

---

## 5. Display PCI Devices with Drivers

### Command

```bash
lspci -k
```

### Purpose

Displays PCI devices along with the Linux kernel driver currently handling each device.

### Information Displayed

* Device name
* Subsystem
* Kernel driver in use
* Available kernel modules

### Why it's useful

Very helpful while troubleshooting hardware driver issues or confirming whether the correct driver is loaded.

---

## 6. Display USB Devices

### Command

```bash
lsusb
```

### Purpose

Lists all USB devices connected to the system.

### Examples

* USB Mouse
* Keyboard
* USB Storage
* USB Hub

### Why it's useful

Quickly verifies whether Linux has detected connected USB hardware.

---

## 7. View Loaded Kernel Modules

### Command

```bash
lsmod
```

### Purpose

Displays all kernel modules currently loaded into memory.

### Output Includes

* Module name
* Module size
* Number of times the module is used

### Why it's useful

Kernel modules provide hardware drivers and additional kernel functionality. This command helps verify whether required modules are loaded.

---

## 8. Display Disk Partitions

### Command

```bash
fdisk -l
```

### Purpose

Lists all disks and their partition tables.

### Information Displayed

* Disk size
* Sector size
* Partition layout
* Filesystem type
* Boot partition
* Swap partition

### Why it's useful

Essential when managing storage devices, checking partition layouts, or preparing disks for installation.

---

# Key Concepts Learned

* Linux provides powerful built-in commands to inspect hardware without third-party software.
* `/proc` contains kernel-generated information about system hardware.
* RAM usage can be monitored using the `free` command.
* PCI and USB devices can be identified using `lspci` and `lsusb`.
* Linux hardware drivers are managed through kernel modules.
* `fdisk` is a powerful utility for viewing and managing disk partitions.

---

# Commands Summary

```bash
# CPU Information
lscpu

# Detailed CPU Information
head -n 20 /proc/cpuinfo

# Memory Usage
free -m
free -g

# PCI Devices
lspci

# PCI Devices with Drivers
lspci -k

# USB Devices
lsusb

# Loaded Kernel Modules
lsmod

# Disk Partitions
fdisk -l
```

---

## What I Learned

This lab helped me understand how Linux interacts with computer hardware. Instead of relying on graphical tools, Linux provides powerful command-line utilities to inspect processors, memory, storage devices, PCI hardware, USB devices, and kernel drivers. These commands form an important foundation for Linux system administration, troubleshooting, and cybersecurity tasks where understanding the underlying hardware is essential.
