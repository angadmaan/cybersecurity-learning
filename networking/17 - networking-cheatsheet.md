# Networking Cheat Sheet

## OSI Model

1. Physical
2. Data Link
3. Network
4. Transport
5. Session
6. Presentation
7. Application

---

## TCP/IP Model

1. Network Access
2. Internet
3. Transport
4. Application

---

## IP Addressing

IPv4 -> 32-bit

Example:
192.168.1.1

IPv6 -> 128-bit

Example:
2001:db8::1

Types:
- Public IP
- Private IP
- Static IP
- Dynamic IP

---

## MAC Address

Physical address of a device.

Example:

00:1A:2B:3C:4D:5E

Used at:
Data Link Layer

---

## ARP

Purpose:

IP Address → MAC Address

Used for communication within a LAN.

---

## DNS

Purpose:

Domain Name → IP Address

Example:

google.com → IP Address

Port:
53

---

## DHCP

Purpose:

Automatically assigns network settings.

DORA Process:

D - Discover

O - Offer

R - Request

A - Acknowledge

---

## NAT

Purpose:

Private IP → Public IP

Benefits:

- Conserves IPv4 addresses
- Hides internal network

Common Type:

PAT (Port Address Translation)

---

## ICMP

Purpose:

Network diagnostics and error reporting.

Commands:

ping

traceroute

---

## Common Ports

HTTP   -> 80

HTTPS  -> 443

SSH    -> 22

FTP    -> 20, 21

SMTP   -> 25

DNS    -> 53

POP3   -> 110

IMAP   -> 143

DHCP   -> 67, 68

---

## Common Protocols

HTTP   -> Web Communication

HTTPS  -> Secure Web Communication

FTP    -> File Transfer

SMTP   -> Email Sending

POP3   -> Email Receiving

IMAP   -> Email Synchronization

DNS    -> Domain Resolution

SSH    -> Secure Remote Access

ICMP   -> Diagnostics

DHCP   -> Automatic IP Assignment

---

## Network Devices

Hub
→ Broadcasts data to all devices

Switch
→ Uses MAC addresses

Router
→ Uses IP addresses

Modem
→ Connects network to ISP

Access Point
→ Provides Wi-Fi

Firewall
→ Filters traffic

Gateway
→ Connects different networks

---

## Routing vs Switching

Switch:
- Uses MAC Address
- Works inside LAN

Router:
- Uses IP Address
- Connects Networks

---

## Topologies

Bus
→ Single cable backbone

Star
→ Central switch/hub

Ring
→ Circular connection

Mesh
→ Multiple connections

Tree
→ Hierarchical structure

Most Common:
Star Topology

---

## Wireless Networking

Common Standards:

802.11n

802.11ac

802.11ax (Wi-Fi 6)

Security:

WPA2

WPA3

Threats:

- Rogue Access Point
- Evil Twin Attack
- Packet Sniffing

---

## VPN

Purpose:

Creates an encrypted communication tunnel.

Benefits:

- Privacy
- Secure Browsing
- Remote Access

---

## Subnetting Basics

Purpose:

Divide large networks into smaller subnets.

Common CIDR:

/8   = 255.0.0.0

/16  = 255.255.0.0

/24  = 255.255.255.0

Benefits:

- Better Performance
- Better Security
- Easier Management

---

## Security Concepts

Firewall

VPN

IDS

IPS

Encryption

Authentication

---

## Quick Revision

OSI → 7 Layers

TCP/IP → 4 Layers

ARP → IP to MAC

DNS → Domain to IP

DHCP → Auto IP Assignment

NAT → Private to Public IP

ICMP → Ping & Troubleshooting

Switch → MAC Address

Router → IP Address

HTTPS → Secure Web Traffic

VPN → Encrypted Tunnel

WPA3 → Wireless Security

Subnetting → Divide Networks
