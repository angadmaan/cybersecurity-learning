# Day 7 — Bash Security Automation & Linux Security Audit

## 🎯 Objective

Apply the Bash and Linux concepts learned during the previous six days to **security-focused system auditing and automation**.

Today focused on:

- Linux users and groups
- File permissions
- Process inspection
- Network information
- Log analysis
- Security checks
- Automating multiple checks with Bash
- Generating a security report
- Building the final Linux Security Audit project

This day connects Bash scripting with **cybersecurity, Linux administration, and DevSecOps**.

---

# 1. Bash for Security Automation

Cybersecurity involves collecting and analyzing large amounts of system information.

Manually performing every check is inefficient.

Bash allows multiple Linux commands to be combined into an automated security tool.

The general workflow is:

```text
Linux System
     ↓
Collect Information
     ↓
Analyze Data
     ↓
Check Security Conditions
     ↓
Generate Report
```

A Bash security script can automate repetitive checks while producing consistent output.

---

# 2. Users and Groups

Linux is a multi-user operating system.

User information can be examined with:

```bash
whoami
```

This displays the current user.

More detailed information:

```bash
id
```

Example:

```text
uid=1000(user) gid=1000(user) groups=1000(user)
```

---

# 3. `/etc/passwd`

Linux user account information is commonly stored in:

```text
/etc/passwd
```

View it with:

```bash
cat /etc/passwd
```

A safer way to extract usernames is:

```bash
cut -d: -f1 /etc/passwd
```

This demonstrates the text-processing skills learned on Day 4.

The file contains account information such as:

```text
username
password placeholder
UID
GID
home directory
login shell
```

Modern Linux systems generally store password hashes separately in `/etc/shadow`.

---

# 4. Login Shells

A user's login shell is one of the fields in `/etc/passwd`.

For example:

```bash
awk -F: '{print $1, $7}' /etc/passwd
```

This displays:

```text
username shell
```

This can help identify which accounts have interactive login shells.

Security analysis should consider whether an account actually requires interactive access rather than treating every account as suspicious.

---

# 5. Linux File Permissions

File permissions determine who can:

- Read a file
- Write to a file
- Execute a file

The three basic permission types are:

```text
r = read
w = write
x = execute
```

Permissions can be viewed with:

```bash
ls -l
```

Example:

```text
-rwxr-xr-x
```

The permission string is divided into:

```text
Owner
Group
Others
```

Conceptually:

```text
-rwx | r-x | r-x
     |     |
   Owner  Group  Others
```

---

# 6. Numeric Permissions

Permissions can also be represented numerically.

```text
r = 4
w = 2
x = 1
```

Therefore:

```text
7 = rwx
6 = rw-
5 = r-x
4 = r--
0 = ---
```

Examples:

```text
755 = rwxr-xr-x
644 = rw-r--r--
700 = rwx------
600 = rw-------
```

These permissions are frequently encountered when securing Linux files and scripts.

---

# 7. Checking Executable Files

A Bash script can determine whether a file is executable:

```bash
if [ -x "$file" ]; then
    echo "Executable"
fi
```

Similarly:

```bash
if [ -r "$file" ]; then
    echo "Readable"
fi
```

and:

```bash
if [ -w "$file" ]; then
    echo "Writable"
fi
```

This allows scripts to automate permission checks.

---

# 8. Finding Files with Specific Permissions

The `find` command can search for files based on permission patterns.

For example:

```bash
find . -type f -perm -111
```

This searches for regular files with execute permissions for the relevant permission bits.

Permission auditing should always be performed in the intended scope. Running broad filesystem searches as root can generate large amounts of output and may expose sensitive information.

---

# 9. Process Inspection

Running processes can be examined using:

```bash
ps aux
```

Search for a specific process:

```bash
ps aux | grep ssh
```

A more direct approach is:

```bash
pgrep ssh
```

Process information can help during:

- Troubleshooting
- System administration
- Incident investigation
- Security auditing

The objective is to identify what is running and determine whether it is expected.

---

# 10. Network Information

Basic network configuration can be examined using:

```bash
ip addr
```

Routing information:

```bash
ip route
```

Listening TCP/UDP sockets:

```bash
ss -tuln
```

These commands can help answer questions such as:

```text
What interfaces exist?
What IP addresses are configured?
What routes are present?
What ports are listening?
```

Network output should be interpreted in the context of the system's intended configuration.

---

# 11. Log Analysis

Logs are an important source of information during security investigations.

Relevant events can include:

```text
failed authentication
permission denied
service errors
unexpected activity
```

The text-processing skills learned on Day 4 can be used to search logs.

Example:

```bash
grep -Ei "failed|denied|error" logfile.txt
```

Count matching lines:

```bash
grep -Ei "failed|denied|error" logfile.txt | wc -l
```

This provides a basic automated log-analysis workflow.

---

# 12. Security Checks

A security auditing script can divide its work into separate checks.

For example:

```text
Security Audit
│
├── System Information
├── User Information
├── Permission Checks
├── Process Checks
├── Network Checks
├── Disk Checks
└── Log Analysis
```

Each check can be implemented as a separate Bash function.

This makes the script modular and easier to maintain.

---

# 13. Security Audit Functions

Example:

```bash
check_system() {
    echo "[ SYSTEM ]"
    echo "Hostname: $(hostname)"
    echo "Kernel: $(uname -r)"
    echo "Uptime: $(uptime -p)"
}
```

User check:

```bash
check_users() {
    echo "[ USERS ]"
    echo "Current User: $(whoami)"
    echo "User Count: $(cut -d: -f1 /etc/passwd | wc -l)"
}
```

Disk check:

```bash
check_disk() {
    echo "[ DISK ]"
    df -h /
}
```

Network check:

```bash
check_network() {
    echo "[ NETWORK ]"
    ip addr
}
```

The functions can then be called from the main script.

---

# 14. Final Project — Linux Security Audit

The final project of this 7-day Bash journey is a **Linux Security Audit** tool.

The purpose of the project is to demonstrate the ability to combine:

```text
Bash
+
Linux Commands
+
Control Flow
+
Functions
+
Text Processing
+
Error Handling
=
Security Automation
```

---

# 15. Project Requirements

The audit script should collect information from several categories.

### System

```text
Hostname
Operating System
Kernel
Uptime
Current User
```

### Users

```text
User accounts
Login shells
Current user
```

### Permissions

```text
Selected file permissions
Executable files
Permission-related checks
```

### Processes

```text
Running processes
Selected process information
```

### Network

```text
IP addresses
Routes
Listening sockets
```

### Disk

```text
Filesystem usage
Disk utilization
```

### Logs

```text
Failed events
Permission errors
General errors
```

---

# 16. Project Structure

The Bash folder contains the practical scripts developed during the learning journey.

The final project can be organized as:

```text
Bash/
├── README.md
├── bash-learning.md
└── scripts/
    ├── system_info.sh
    ├── disk_check.sh
    ├── backup.sh
    ├── permission_audit.sh
    ├── failed_login_check.sh
    └── security_audit.sh
```

The primary final script is:

```text
security_audit.sh
```

---

# 17. Final Security Audit Script

A simplified structure for the final script is:

```bash
#!/bin/bash

set -euo pipefail

check_system() {
    echo "[ SYSTEM ]"
    echo "Hostname : $(hostname)"
    echo "Kernel   : $(uname -r)"
    echo "Uptime   : $(uptime -p)"
}

check_users() {
    echo
    echo "[ USERS ]"
    echo "Current User : $(whoami)"
    echo "User Count   : $(cut -d: -f1 /etc/passwd | wc -l)"
}

check_disk() {
    echo
    echo "[ DISK ]"
    df -h /
}

check_network() {
    echo
    echo "[ NETWORK ]"
    ip addr
}

check_processes() {
    echo
    echo "[ PROCESSES ]"
    ps aux
}

echo "========================================"
echo "        LINUX SECURITY AUDIT"
echo "========================================"

check_system
check_users
check_disk
check_network
check_processes

echo
echo "========================================"
echo "             AUDIT COMPLETE"
echo "========================================"
```

This is a starting point rather than a complete enterprise security scanner.

The important objective is understanding how the individual components work and how they can be safely combined.

---

# 18. Generating a Report

The audit output can be redirected into a file:

```bash
./security_audit.sh > security_report.txt
```

A timestamp can be added to the filename:

```bash
timestamp=$(date +"%Y-%m-%d_%H-%M-%S")

./security_audit.sh > "security_report_$timestamp.txt"
```

This turns the script into a basic reporting tool.

---

# 19. Improving the Audit

The basic audit can be extended with additional checks.

For example:

```text
System
   ↓
Users
   ↓
Permissions
   ↓
Processes
   ↓
Network
   ↓
Disk
   ↓
Logs
   ↓
Report
```

Future improvements could include:

- Configurable thresholds
- Command-line arguments
- Better input validation
- More structured output
- Separate log files
- Exit-status reporting
- Optional checks
- Human-readable summaries

These improvements can be added after the initial version works correctly.

---

# 20. Practical Exercises

## Exercise 1 — User Audit

Create a script that displays:

```text
Current User:
Number of Accounts:
Users with Login Shells:
```

Use:

```bash
whoami
cut
awk
wc
```

---

## Exercise 2 — Permission Audit

Create a script that checks selected files and reports their permissions.

Example:

```text
File: script.sh
Permissions: -rwxr-xr-x
Executable: Yes
```

---

## Exercise 3 — Process Check

Create a script that checks whether a particular process exists.

Example:

```text
Process: ssh
Status: Running
```

or:

```text
Process: ssh
Status: Not Running
```

---

## Exercise 4 — Network Audit

Create a script that displays:

```text
IP Addresses
Routes
Listening Ports
```

using:

```bash
ip
ss
```

---

## Exercise 5 — Log Audit

Create a script that accepts a log file as an argument and reports:

```text
Errors:
Failed Events:
Permission Denied:
```

Use:

```bash
grep
wc
```

---

## Exercise 6 — Combine Everything

Combine the previous exercises into:

```text
security_audit.sh
```

The script should produce one consolidated report.

---

# 21. What I Learned During the 7-Day Journey

The Bash journey progressed from basic Linux commands to security automation.

```text
Day 1
Linux Shell
    ↓
Day 2
Bash Basics
    ↓
Day 3
Control Flow
    ↓
Day 4
Text Processing
    ↓
Day 5
Functions & Error Handling
    ↓
Day 6
Linux Automation
    ↓
Day 7
Security Automation
```

The progression demonstrates how basic command-line knowledge can develop into practical scripting skills.

---

# 🔐 Cybersecurity Relevance

Bash is an important tool in a Linux-based cybersecurity environment.

It can help security professionals automate:

- System enumeration
- Configuration checks
- Permission auditing
- Log analysis
- Process inspection
- Network inspection
- Backup operations
- Security reporting

However, Bash should be considered an **automation and orchestration tool**, not a replacement for dedicated security tools.

A professional security workflow often combines Bash with tools such as:

```text
Linux
+
Bash
+
Git
+
Networking Tools
+
Security Tools
+
Cloud Tools
```

---

# 🧠 Final Key Takeaways

- Linux provides the environment in which many security scripts operate.
- Bash can combine Linux utilities into automated workflows.
- Functions make security scripts modular.
- Arguments make scripts configurable.
- Exit codes allow scripts to communicate success or failure.
- Permissions are fundamental to Linux security.
- Users, processes, networks, and logs provide valuable security information.
- Pipes and text-processing tools make large amounts of command output easier to analyze.
- Automation improves consistency and reduces repetitive manual work.
- Security scripts should be tested carefully and executed only on systems where you have authorization.

---

# 🏁 7-Day Bash Journey Completed

```text
Day 1  ✓ Linux Shell Fundamentals
Day 2  ✓ Bash Scripting Fundamentals
Day 3  ✓ Control Flow
Day 4  ✓ Files & Text Processing
Day 5  ✓ Functions, Arguments & Error Handling
Day 6  ✓ Linux Automation
Day 7  ✓ Security Automation
```

## Final Project

**Linux Security Audit**

The project demonstrates the practical application of Bash scripting to Linux security auditing and automation.

---

## 📌 Status

**Completed — 7-Day Bash Learning Journey**

**Skills:** Bash · Linux · Shell Scripting · Automation · System Administration · Security Automation · DevSecOps