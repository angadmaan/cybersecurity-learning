# Network Address Translation (NAT)

## Introduction

NAT (Network Address Translation) allows multiple devices on a private network to share a single public IP address.

It is commonly used in home and office networks.

---

## Why NAT is Needed

IPv4 addresses are limited.

NAT helps conserve public IP addresses by allowing many devices to use one public address.

---

## How NAT Works

1. Device sends traffic to the internet.
2. Router replaces private IP with public IP.
3. Response returns to the router.
4. Router forwards data to the correct device.

---

## Example

Private IP:

192.168.1.10

Public IP:

103.25.50.100

The internet sees only the public IP.

---

## Types of NAT

### Static NAT

One private IP maps to one public IP.

### Dynamic NAT

Public IP selected from a pool.

### PAT (Port Address Translation)

Multiple devices share one public IP using different ports.

Most home routers use PAT.

---

## Advantages

- Conserves IPv4 addresses
- Improves privacy
- Simplifies network management

---

## Importance in Cybersecurity

NAT hides internal devices from direct internet exposure and provides a basic layer of protection.

---

## Key Learning

NAT allows multiple private devices to access the internet using a single public IP address.
