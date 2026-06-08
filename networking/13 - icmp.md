# Internet Control Message Protocol (ICMP)

## Introduction

ICMP is a network protocol used for diagnostics, error reporting, and troubleshooting.

Unlike TCP and UDP, ICMP does not transfer application data.

---

## Purpose of ICMP

ICMP helps:

- Check connectivity
- Report network errors
- Diagnose communication issues

---

## Common ICMP Messages

### Echo Request

Sent by the Ping command.

### Echo Reply

Returned by the destination device.

### Destination Unreachable

Indicates the destination cannot be reached.

### Time Exceeded

Occurs when packet TTL expires.

---

## Ping

Ping uses ICMP to test connectivity.

Example:

ping google.com

Benefits:

- Verify network connection
- Measure response time
- Troubleshoot problems

---

## Traceroute

Traceroute uses ICMP to identify the path packets take across networks.

Benefits:

- Identify network bottlenecks
- Troubleshoot routing issues

---

## Importance in Cybersecurity

ICMP helps:

- Network monitoring
- Troubleshooting
- Security assessments

Attackers may also misuse ICMP for reconnaissance.

---

## Key Learning

ICMP is essential for network diagnostics and is commonly used by tools such as Ping and Traceroute.
