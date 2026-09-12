# Day 6 — Linux Automation

## 🎯 Objective

Learn how to use Bash to automate common Linux administration tasks instead of performing them manually.

Today focused on:

- System information gathering
- Disk usage monitoring
- Memory and CPU information
- Network information
- Creating automated backups
- Working with `tar`
- Timestamps and filenames
- Combining commands, variables, functions, and conditions
- Building practical Bash utilities

This day connected the Bash fundamentals learned earlier with real-world **Linux administration and DevSecOps automation**.

---

# 1. Why Linux Automation?

Linux systems often require repetitive tasks such as:

- Checking system health
- Monitoring disk usage
- Collecting system information
- Creating backups
- Checking network configuration
- Examining running processes
- Generating reports

Performing these tasks manually is inefficient.

Bash allows multiple Linux commands to be combined into a single script.

The basic idea is:

```text
Manual Tasks
     ↓
Bash Script
     ↓
Automated Process
     ↓
Consistent Result
```

---

# 2. System Information

Linux provides many commands for collecting system information.

Important commands include:

```bash
hostname
uname
uptime
whoami
id
date
```

---

## Hostname

```bash
hostname
```

Displays the system's hostname.

The hostname can be stored in a variable:

```bash
hostname_name=$(hostname)

echo "Hostname: $hostname_name"
```

---

# 3. Operating System Information

A common command for kernel information is:

```bash
uname -a
```

On Linux systems, additional operating-system information can often be found in:

```bash
/etc/os-release
```

For example:

```bash
cat /etc/os-release
```

A script can retrieve this information automatically.

---

# 4. System Uptime

The `uptime` command displays how long the system has been running.

```bash
uptime
```

This can be useful when troubleshooting system availability or performance.

---

# 5. CPU Information

CPU information can be inspected using:

```bash
lscpu
```

For example:

```bash
lscpu | grep "CPU(s)"
```

This combines system information with the text-processing skills learned on Day 4.

---

# 6. Memory Usage

The `free` command displays memory usage.

```bash
free
```

Human-readable output:

```bash
free -h
```

Example:

```text
               total        used        free
Mem:            15Gi        6Gi         4Gi
```

A script can collect this information automatically.

---

# 7. Disk Usage

The `df` command displays filesystem disk usage.

```bash
df
```

Human-readable output:

```bash
df -h
```

To check the root filesystem:

```bash
df -h /
```

Example:

```text
Filesystem      Size  Used Avail Use%
/dev/sda1       100G   72G   28G  72%
```

---

# 8. Disk Usage Monitoring

A script can use disk information to determine whether storage usage has become too high.

For example, a threshold can be defined:

```bash
threshold=80
```

The script can then compare the current usage against the threshold.

Conceptually:

```text
Disk Usage
    ↓
Extract Percentage
    ↓
Compare with Threshold
    ↓
 ┌───────────────┐
 │ Above 80%?    │
 └───────────────┘
      ↓     ↓
     Yes    No
      ↓     ↓
   Warning  OK
```

Example output:

```text
Disk Usage: 72%
STATUS: OK
```

or:

```text
Disk Usage: 91%
WARNING: Disk usage is high!
```

This is a basic example of automated system monitoring.

---

# 9. Network Information

Network configuration can be inspected using:

```bash
ip addr
```

or:

```bash
ip a
```

To inspect routing information:

```bash
ip route
```

To display listening network sockets on systems where `ss` is available:

```bash
ss -tuln
```

These commands are useful for basic Linux network administration and security investigations.

---

# 10. Process Information

Running processes can be viewed using:

```bash
ps aux
```

Search for a particular process:

```bash
ps aux | grep ssh
```

A more direct process search can use:

```bash
pgrep ssh
```

This can be incorporated into automation scripts to check whether a required service or process is running.

---

# 11. Creating Backups

Backups are another common automation task.

Linux provides `tar` for creating archives.

Basic example:

```bash
tar -cf backup.tar documents/
```

Create a gzip-compressed archive:

```bash
tar -czf backup.tar.gz documents/
```

The options mean:

```text
-c → create archive
-z → gzip compression
-f → specify archive filename
```

---

# 12. Using Timestamps

A timestamp can be generated with:

```bash
date
```

For filenames, a formatted timestamp is more useful:

```bash
date +"%Y-%m-%d_%H-%M-%S"
```

Example:

```text
2026-09-11_00-30-45
```

This can be used to create unique backup filenames.

Example:

```bash
timestamp=$(date +"%Y-%m-%d_%H-%M-%S")

echo "$timestamp"
```

---

# 13. Automated Backup Script

A basic backup script can accept a directory as an argument.

Example:

```bash
#!/bin/bash

set -euo pipefail

if [ "$#" -ne 1 ]; then
    echo "Usage: $0 <directory>"
    exit 1
fi

source_dir="$1"
timestamp=$(date +"%Y-%m-%d_%H-%M-%S")
backup_name="backup_$timestamp.tar.gz"

tar -czf "$backup_name" "$source_dir"

echo "Backup created: $backup_name"
```

This script demonstrates several concepts learned during the previous five days:

- Script arguments
- Argument validation
- Variables
- Command substitution
- Error handling
- `set -euo pipefail`
- `tar`
- Timestamps

---

# 14. Functions for Automation

Larger scripts become easier to maintain when tasks are separated into functions.

Example:

```bash
#!/bin/bash

set -euo pipefail

show_system_info() {
    echo "Hostname: $(hostname)"
    echo "User: $(whoami)"
    echo "Kernel: $(uname -r)"
    echo "Uptime: $(uptime -p)"
}

show_memory() {
    free -h
}

show_disk() {
    df -h /
}

show_system_info
show_memory
show_disk
```

The script now has separate functions for different tasks.

This approach will be important for the final security auditing project.

---

# 15. Building a System Information Script

A practical script was designed to collect important system information.

Example:

```bash
#!/bin/bash

set -euo pipefail

echo "========================================"
echo "        SYSTEM INFORMATION"
echo "========================================"

echo
echo "[ SYSTEM ]"
echo "Hostname : $(hostname)"
echo "User     : $(whoami)"
echo "Kernel   : $(uname -r)"
echo "Uptime   : $(uptime -p)"

echo
echo "[ MEMORY ]"
free -h

echo
echo "[ DISK ]"
df -h /

echo
echo "[ NETWORK ]"
ip addr
```

The purpose is not to reproduce every possible system detail, but to demonstrate how Bash can combine multiple Linux utilities into one automated report.

---

# 16. Script Design

A useful automation script should generally follow this structure:

```text
Start
  ↓
Validate Input
  ↓
Collect Information
  ↓
Process Information
  ↓
Check Conditions
  ↓
Generate Output
  ↓
Exit
```

For larger scripts:

```text
Main Script
     │
     ├── validate_input()
     │
     ├── collect_system_info()
     │
     ├── check_disk()
     │
     ├── check_memory()
     │
     ├── check_network()
     │
     └── generate_report()
```

This is the same modular approach used in larger software projects.

---

# 17. Practical Exercises

## Exercise 1 — System Information

Create a script that displays:

```text
Hostname:
Current User:
Kernel:
Uptime:
```

Use:

```bash
hostname
whoami
uname
uptime
```

---

## Exercise 2 — Disk Monitor

Create a script that:

1. Checks root filesystem usage.
2. Extracts the usage percentage.
3. Compares it against a threshold.
4. Prints `OK` or `WARNING`.

Example:

```text
Disk Usage: 72%
STATUS: OK
```

---

## Exercise 3 — Memory Check

Use:

```bash
free -h
```

to display memory information.

Extend the script to identify when memory usage crosses a chosen threshold.

---

## Exercise 4 — Backup

Create a backup script that accepts a directory:

```bash
./backup.sh ~/Documents
```

and creates:

```text
backup_YYYY-MM-DD_HH-MM-SS.tar.gz
```

---

## Exercise 5 — System Report

Combine the previous concepts into one script that produces a system report containing:

```text
========================================
          SYSTEM REPORT
========================================

Hostname:
User:
Kernel:
Uptime:

Memory:

Disk:

Network:

========================================
```

---

# 18. Practical Workflow

The main concept learned today was combining previously learned Bash features.

```text
Linux Commands
      ↓
Variables
      ↓
Functions
      ↓
Conditions
      ↓
Text Processing
      ↓
Automation
      ↓
Useful Tool
```

For example:

```bash
disk_usage=$(df -h / | awk 'NR==2 {print $5}')
```

Here:

```text
df       → collects disk information
|        → passes output to another command
awk      → extracts the required field
$()      → stores command output
variable → saves the result
```

This demonstrates how individual Linux tools can be combined into automation.

---

# 🔐 Cybersecurity & DevSecOps Relevance

Linux automation is a major part of cybersecurity and DevSecOps.

Bash scripts can be used to:

- Collect system information
- Monitor system resources
- Check security configurations
- Analyze logs
- Verify permissions
- Monitor processes
- Inspect network configuration
- Automate backups
- Generate security reports
- Support incident investigation

For example, a security automation script might collect:

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
Logs
   ↓
Security Report
```

Day 6 therefore connects basic Bash programming with practical system administration.

---

# 🧠 Key Takeaways

- Bash can automate repetitive Linux administration tasks.
- `hostname`, `uname`, `uptime`, `free`, and `df` provide useful system information.
- `ip` and `ss` can provide basic network information.
- `ps` and `pgrep` can be used to inspect processes.
- `tar` can create compressed backups.
- Timestamps can be used to create unique filenames.
- Functions help organize larger automation scripts.
- Bash commands can be combined using pipes and command substitution.
- Thresholds and conditions allow scripts to monitor system state automatically.
- Reliable automation requires input validation and error handling.
- These techniques provide a foundation for security automation.

---

# 🧪 Commands & Syntax Learned

```text
hostname
uname -a
uname -r
uptime
uptime -p
lscpu
free -h
df -h
df -h /
ip addr
ip route
ss -tuln
ps aux
pgrep
tar -cf
tar -czf
date +"%Y-%m-%d_%H-%M-%S"
```

---

## 📌 Day 6 Status

**Completed — Linux Automation**

Next:

**Day 7 — Bash Security Automation & Linux Security Audit**