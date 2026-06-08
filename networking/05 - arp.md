# Address Resolution Protocol (ARP)

## Introduction

ARP (Address Resolution Protocol) is used to find the MAC address of a device when its IP address is known.

ARP operates within a local network and helps devices communicate at the Data Link Layer.

---

## Why ARP is Needed

Computers communicate using IP addresses, but actual data delivery inside a LAN uses MAC addresses.

ARP acts as a bridge between IP addresses and MAC addresses.

---

## How ARP Works

1. Device knows destination IP address.
2. ARP Request is broadcast.
3. Target device responds with its MAC address.
4. ARP table is updated.
5. Communication begins.

---

## ARP Request

Broadcast message asking:

"Who has this IP address?"

---

## ARP Reply

Response containing the MAC address of the target device.

---

## ARP Table

Stores IP-to-MAC mappings.

Useful for:
- Faster communication
- Reduced network traffic

---

## ARP Spoofing

An attacker sends fake ARP messages to impersonate another device.

Risks:

- Traffic interception
- Man-in-the-Middle attacks
- Data theft

---

## Importance in Cybersecurity

Security professionals monitor ARP activity to detect spoofing attacks and unauthorized devices.

---

## Key Learning

ARP translates IP addresses into MAC addresses, enabling communication within local networks.
