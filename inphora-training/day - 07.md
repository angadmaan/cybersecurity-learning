# Day 7

## Overview

On Day 7, I explored Linux commands used for gathering system information, monitoring processes, checking network configuration, and troubleshooting connectivity. These commands are widely used by Linux administrators, network engineers, and cybersecurity professionals during system analysis and troubleshooting.

---

## Commands Learned

### 1. `history`

Displays previously executed commands in the terminal.

```bash
history
```

Useful for reviewing command usage and repeating previous commands.

---

### 2. `whoami`

Shows the currently logged-in user.

```bash
whoami
```

Example Output:

```bash
kali
```

---

### 3. `hostname`

Displays the system hostname.

```bash
hostname
```

Example Output:

```bash
kali
```

---

### 4. `uname -a`

Displays detailed information about the operating system and kernel.

```bash
uname -a
```

Provides:
- Kernel version
- Architecture
- Host information
- Operating system details

---

## Network Information Commands

### 5. `ifconfig`

Displays network interface configuration.

```bash
ifconfig
```

Shows:
- IP address
- MAC address
- Network statistics

---

### 6. `ip link`

Displays network interfaces and their status.

```bash
ip link
```

Useful for viewing available network adapters.

---

### 7. `ping`

Tests network connectivity to a host.

```bash
ping flipkart.com
```

Used to verify:
- Internet connectivity
- DNS resolution
- Network reachability

---

## Network Monitoring Commands

### 8. `netstat -tulp`

Displays active network connections and listening ports.

```bash
netstat -tulp
```

Shows:
- TCP connections
- UDP connections
- Listening services
- Associated processes

---

### 9. `ss -tulp`

Modern replacement for netstat.

```bash
ss -tulp
```

Provides faster and more detailed socket statistics.

---

## Process Monitoring Commands

### 10. `ps aux`

Displays all running processes.

```bash
ps aux
```

Useful for:
- Viewing active programs
- Identifying suspicious processes
- System monitoring

---

### 11. `top`

Displays real-time system resource usage.

```bash
top
```

Shows:
- CPU utilization
- Memory usage
- Running processes
- System load

---

## Practical Exercise

```bash
whoami

hostname

uname -a

ifconfig

ip link

ping flipkart.com

netstat -tulp

ss -tulp

ps aux

top
```

---

## Key Takeaways

- Learned commands for identifying system and user information.
- Explored network configuration and connectivity testing.
- Viewed active network services and listening ports.
- Monitored running processes and system performance.
- Gained practical experience with Linux troubleshooting and administration tools.

---

## Conclusion

This session focused on system monitoring, process management, and network diagnostics. These commands are essential for Linux administration, cybersecurity investigations, and troubleshooting network-related issues.
