# Day 18

## 📌 Overview

Today I completed **Lab 14: Network Configuration** from the Cisco Linux Essentials course. This lab focused on understanding how Linux systems communicate over a network. I learned how to view IP addresses, inspect routing tables, resolve hostnames using DNS, test connectivity, and monitor active network connections using essential networking tools.

---

# Topics Covered

* Viewing network interface configuration
* Understanding IPv4 and IPv6 addresses
* Examining routing tables
* Working with the `/etc/hosts` file
* Testing connectivity using `ping`
* DNS configuration and name resolution
* Forward and reverse DNS lookups with `dig`
* Monitoring network connections using `netstat`
* Viewing socket statistics using `ss`

---

# 1. Viewing Network Configuration

## Display Network Interfaces

### Command

```bash
ifconfig
```

### Purpose

Displays information about all network interfaces on the system.

Important information shown includes:

* IPv4 Address
* IPv6 Address
* MAC Address
* Netmask
* Broadcast Address
* Interface Status (UP/DOWN)
* Packets Sent and Received

---

## Common Network Interfaces

### eth0

Represents the primary Ethernet network interface.

### lo

Represents the **Loopback Interface**.

Loopback IP:

```text
127.0.0.1
```

Used by the computer to communicate with itself.

---

## IPv4 vs IPv6

### IPv4

* 32-bit address
* Written as four decimal numbers
* Example:

```text
192.168.1.2
```

### IPv6

* 128-bit address
* Written in hexadecimal
* Example:

```text
fe80::42:c0ff:fea8:102
```

IPv6 provides a significantly larger address space than IPv4.

---

# 2. Viewing the Routing Table

### Command

```bash
route
```

### Purpose

Displays the kernel's IP routing table.

Important fields include:

* Destination Network
* Gateway
* Netmask
* Interface

Example:

```text
default → 192.168.1.1
```

The **default gateway** forwards packets destined for external networks.

---

# 3. Local Hostname Resolution

Linux can resolve hostnames locally using the `/etc/hosts` file.

### Verify localhost Entry

```bash
grep 127.0.0.1 /etc/hosts
```

Example Output

```text
127.0.0.1 localhost
```

This maps the hostname **localhost** to the loopback IP address.

---

# 4. Testing Network Connectivity

### Command

```bash
ping -c4 localhost
```

### Purpose

Sends four ICMP Echo Requests to verify network connectivity.

Important Output

* Packets Sent
* Packets Received
* Packet Loss
* Round Trip Time (RTT)

Example

```text
4 packets transmitted
4 received
0% packet loss
```

A successful ping confirms that the destination is reachable.

---

# 5. DNS Configuration

Linux stores DNS server information inside:

```text
/etc/resolv.conf
```

### View DNS Configuration

```bash
cat /etc/resolv.conf
```

Typical Output

```text
nameserver 127.0.0.11
```

The **nameserver** entry specifies which DNS server the system uses to resolve domain names into IP addresses.

---

# 6. DNS Lookup Using dig

The `dig` command performs DNS queries.

---

## Resolve a Hostname

### Command

```bash
dig localhost.localdomain
```

### Purpose

Converts a hostname into its IP address.

Example Result

```text
localhost.localdomain → 127.0.0.1
```

---

## Resolve a Fully Qualified Domain Name (FQDN)

### Command

```bash
dig cserver.example.com
```

### Purpose

Performs a DNS lookup for an FQDN.

Example

```text
cserver.example.com → 192.168.1.2
```

---

## Reverse DNS Lookup

### Command

```bash
dig -x 192.168.1.2
```

### Purpose

Converts an IP address back into its hostname.

This is known as a **PTR (Pointer) Record Lookup**.

---

# 7. Fully Qualified Domain Name (FQDN)

An FQDN contains:

```text
Hostname + Domain Name
```

Example

```text
cserver.example.com
```

Where

* Hostname → cserver
* Domain → example.com

---

# 8. Network Monitoring Using netstat

The `netstat` command displays network statistics and active connections.

---

## Display Help

```bash
netstat --help
```

Lists all available options.

---

## View Listening TCP Ports

### Command

```bash
netstat -tl
```

### Purpose

Displays TCP services currently waiting for incoming connections.

Example

```text
ssh
domain
```

---

## Display Numeric Addresses

### Command

```bash
netstat -tln
```

### Purpose

Shows listening TCP ports without resolving hostnames.

Example

```text
0.0.0.0:22
```

Port **22** indicates the SSH service.

---

## Common Options

| Option | Meaning             |
| ------ | ------------------- |
| -t     | TCP connections     |
| -l     | Listening services  |
| -n     | Numeric addresses   |
| -p     | Show process IDs    |
| -a     | Display all sockets |

---

# 9. Common Network Ports

| Port | Service |
| ---- | ------- |
| 22   | SSH     |
| 53   | DNS     |
| 80   | HTTP    |
| 443  | HTTPS   |

These are known as **well-known ports**.

---

# 10. Socket Statistics Using ss

The `ss` command is the modern replacement for `netstat`.

---

## Generate Traffic

```bash
start_webserver
```

Creates local network activity for monitoring.

---

## View Socket Statistics

```bash
ss
```

### Purpose

Displays active TCP and UDP socket connections.

Information includes:

* Connection State
* Local Address
* Remote Address
* Port Numbers
* Send Queue
* Receive Queue

Example States

* LISTEN
* ESTABLISHED
* CLOSE-WAIT
* FIN-WAIT-2

The `ss` command is faster and provides more detailed socket information than `netstat`.

---

# Important Commands Summary

```bash
# View network interfaces
ifconfig

# Display routing table
route

# Verify localhost entry
grep 127.0.0.1 /etc/hosts

# Test connectivity
ping -c4 localhost

# View DNS configuration
cat /etc/resolv.conf

# Resolve hostname
dig localhost.localdomain

# Resolve FQDN
dig cserver.example.com

# Reverse DNS lookup
dig -x 192.168.1.2

# Display netstat help
netstat --help

# Show listening TCP ports
netstat -tl

# Show numeric listening ports
netstat -tln

# Modern socket statistics
ss
```

---

# Key Concepts Learned

* `ifconfig` displays detailed network interface information.
* Every Linux system includes a loopback interface (`127.0.0.1`) for internal communication.
* The routing table determines how packets reach other networks.
* `/etc/hosts` provides local hostname-to-IP mappings.
* `ping` is used to test network connectivity using ICMP.
* `/etc/resolv.conf` defines the DNS servers used by the system.
* `dig` performs DNS queries, including forward and reverse lookups.
* An FQDN combines a hostname with its domain name.
* `netstat` displays active network connections and listening ports.
* `ss` is the modern, faster replacement for `netstat` for monitoring sockets and network statistics.

---

# What I Learned

This lab helped me understand the core networking tools available in Linux for configuring and troubleshooting network connectivity. I learned how to inspect IP addresses, routing tables, and DNS settings, verify communication using `ping`, resolve hostnames with `dig`, and analyze active network services using `netstat` and `ss`. These commands form the foundation for diagnosing network issues and managing Linux systems in both administrative and cybersecurity environments.
