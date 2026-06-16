# Day 11

## Overview

Today's session focused on networking fundamentals, including the OSI Model, network devices, routing concepts, and several practical networking commands used for troubleshooting and information gathering.

The training helped me understand how data travels across networks and how various networking tools can be used to inspect and diagnose connectivity issues.

---

## Topics Covered

### OSI Model (Open Systems Interconnection)

The OSI Model divides network communication into seven layers.

| Layer | Name | Function |
|---------|---------|----------|
| 7 | Application | User-facing network services |
| 6 | Presentation | Data formatting and encryption |
| 5 | Session | Session management |
| 4 | Transport | Reliable data delivery |
| 3 | Network | Routing and IP addressing |
| 2 | Data Link | MAC addressing and switching |
| 1 | Physical | Transmission of bits over media |

### Example

When opening a website:

- Application Layer handles browser requests.
- Transport Layer uses TCP.
- Network Layer routes packets using IP addresses.
- Data Link Layer uses MAC addresses.
- Physical Layer transmits signals through cables or wireless media.

---

## Network Devices

### Switch

A switch operates mainly at Layer 2 (Data Link Layer).

Functions:

- Connects devices within a LAN.
- Uses MAC addresses for forwarding.
- Reduces unnecessary traffic.

### Router

A router operates at Layer 3 (Network Layer).

Functions:

- Connects multiple networks.
- Routes packets between networks.
- Uses IP addresses for forwarding decisions.

---

## DNS Lookup

### Command

```bash
nslookup google.com
```

### Purpose

Used to query DNS servers and retrieve information about domain names.

### Example Use

- Convert domain names into IP addresses.
- Troubleshoot DNS issues.
- Verify DNS records.

---

## ARP (Address Resolution Protocol)

### View ARP Table

```bash
arp -a
```

### Purpose

Displays the ARP cache that maps IP addresses to MAC addresses.

### Example

When a device wants to communicate with another device on the same network, it first resolves the MAC address using ARP.

---

## Route Inspection

### Command

```bash
ip route
```

### Purpose

Displays the routing table of the system.

### Information Shown

- Default gateway
- Network routes
- Destination networks
- Interface information

---

## Traceroute

### Linux

```bash
traceroute google.com
```

### Windows

```cmd
tracert google.com
```

### Purpose

Shows the path packets take from the source system to the destination server.

### Benefits

- Identify network delays
- Locate routing issues
- Analyze packet travel paths

---

## Network Connectivity Testing

### Ping

```bash
ping google.com
```

### Purpose

Checks whether a host is reachable and measures network latency.

### Information Provided

- Packet loss
- Response time
- Connectivity status

---

## Windows Performance Assessment

### Command

```powershell
Get-CimInstance Win32_WinSAT
```

### Purpose

Retrieves Windows System Assessment Tool (WinSAT) information.

### Information Obtained

- CPU performance
- Memory performance
- Graphics performance
- Disk performance

---

## Commands Practiced

```bash
nslookup google.com
arp -a
ip route
ping google.com
traceroute google.com
```

### Windows Commands

```cmd
tracert google.com
```

```powershell
Get-CimInstance Win32_WinSAT
```

---

## Key Takeaways

- Learned all seven layers of the OSI Model.
- Understood the role of switches and routers in networking.
- Explored DNS resolution using `nslookup`.
- Learned how ARP maps IP addresses to MAC addresses.
- Viewed routing tables using `ip route`.
- Traced packet paths using `traceroute` and `tracert`.
- Practiced network connectivity testing with `ping`.
- Explored basic Windows system performance information using WinSAT.

---

## Conclusion

Day 11 strengthened my networking fundamentals by connecting theoretical concepts such as the OSI Model with practical networking tools. Understanding how devices communicate, resolve addresses, and route packets is essential for both networking and cybersecurity professionals.
