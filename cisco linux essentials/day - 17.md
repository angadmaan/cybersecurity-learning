# Day 17

## 📌 Overview

Today I completed **Lab 13: Where Data is Stored** from the Cisco Linux Essentials course. This lab introduced the Linux **/proc pseudo-filesystem**, process management, system monitoring, and log files. I learned how Linux stores runtime information, manages processes, monitors system activity, and records important events through system logs.

---

# Topics Covered

* Understanding the **/proc pseudo-filesystem**
* Viewing kernel and process information
* Managing foreground and background processes
* Monitoring processes using **top**
* Terminating processes using **kill**, **killall**, and **pkill**
* Viewing running processes using **ps**
* Exploring Linux system logs

---

# 1. Understanding the /proc Filesystem

## What is /proc?

`/proc` is a **virtual (pseudo) filesystem** stored in memory rather than on disk. It provides real-time information about:

* Running processes
* CPU
* Memory
* Devices
* Kernel settings

Unlike normal directories such as `/etc` or `/usr`, files inside `/proc` are generated dynamically by the Linux kernel.

---

## List the /proc Directory

### Command

```bash
ls /proc
```

### Purpose

Displays all files and directories maintained by the Linux kernel.

### Important Entries

* `/proc/cpuinfo` → CPU information
* `/proc/meminfo` → Memory details
* `/proc/devices` → Registered devices
* `/proc/sys` → Kernel configuration
* Numeric directories (e.g., `/proc/1`) → Running processes

---

## View Process Command

### Command

```bash
cat /proc/1/cmdline
```

### Purpose

Displays the command used to start Process ID (PID) 1.

Example Output

```
/sbin/init
```

---

## Display Process Information

### Command

```bash
ps -p 1
```

### Purpose

Shows information about Process ID 1.

Useful for checking running system processes.

---

## View Kernel Boot Parameters

### Command

```bash
cat /proc/cmdline
```

### Purpose

Displays all parameters passed to the Linux kernel during boot.

Useful for:

* Boot troubleshooting
* Kernel configuration
* Debugging startup issues

---

# 2. Process Management

Linux allows processes to run in either the **foreground** or **background**.

---

## Run a Process in Foreground

### Command

```bash
ping localhost > /dev/null
```

### Purpose

Runs the ping command continuously.

Since it runs in the foreground, the terminal remains occupied until the process is stopped.

---

## Stop a Foreground Process

### Shortcut

```
Ctrl + C
```

### Purpose

Terminates the currently running foreground process.

---

## Run a Process in Background

### Command

```bash
ping localhost > /dev/null &
```

### Purpose

Runs the process in the background while keeping the terminal available.

The `&` symbol sends the command to the background.

---

## View Background Jobs

### Command

```bash
jobs
```

### Purpose

Displays all jobs running in the current terminal.

---

## Bring a Background Job to Foreground

### Command

```bash
fg %1
```

### Purpose

Moves Job 1 back to the foreground.

---

## Suspend a Foreground Process

### Shortcut

```
Ctrl + Z
```

### Purpose

Pauses the running process without terminating it.

---

## Resume a Suspended Process

### Command

```bash
bg %1
```

### Purpose

Continues the suspended process in the background.

---

## Kill a Specific Background Job

### Command

```bash
kill %3
```

### Purpose

Terminates Job 3.

---

## Kill All Processes with the Same Name

### Command

```bash
killall ping
```

### Purpose

Stops every running `ping` process.

---

# 3. Monitoring Processes Using top

The `top` command provides a real-time view of system activity.

---

## Start top

### Command

```bash
top
```

### Purpose

Displays:

* Running processes
* CPU usage
* Memory usage
* Load average
* Process IDs
* Process priority

The display refreshes automatically every few seconds.

---

## Kill a Process Inside top

### Steps

1. Press **k**
2. Enter the Process ID (PID)
3. Press **Enter**
4. Press **Enter** again to send **SIGTERM (15)**

---

## Force Kill a Process

When prompted:

```
Kill PID with signal [15]:
```

Enter:

```
9
```

### Purpose

Sends **SIGKILL**, which forcefully terminates the process.

---

## Exit top

Press

```
q
```

---

# 4. Process Management Commands

## View Running Processes

```bash
ps
```

Displays processes running in the current shell.

---

## Kill a Process by PID

```bash
kill PID
```

Terminates a specific process.

---

## Kill by Process Name

```bash
pkill process_name
```

Terminates processes by matching their name.

Example

```bash
pkill firefox
```

---

## Kill All Processes

```bash
killall process_name
```

Example

```bash
killall ping
```

Stops every running ping process.

---

# 5. Linux System Logs

Linux stores important system events inside the **/var/log** directory.

These logs help administrators troubleshoot errors, monitor security, and analyze system activity.

---

## List Log Files

### Command

```bash
ls /var/log
```

### Common Log Files

| File     | Purpose                           |
| -------- | --------------------------------- |
| auth.log | Authentication and login attempts |
| syslog   | General system messages           |
| dmesg    | Kernel boot messages              |
| cron.log | Scheduled tasks                   |
| dpkg.log | Package installation logs         |
| wtmp     | Login history                     |
| btmp     | Failed login attempts             |

---

## View Authentication Logs

### Command

```bash
tail -5 /var/log/auth.log
```

### Purpose

Displays the last five authentication events.

Useful for monitoring:

* Successful logins
* Failed logins
* SSH access attempts
* Security incidents

---

# Important Commands Summary

```bash
# View /proc contents
ls /proc

# View command of Process 1
cat /proc/1/cmdline

# Display Process 1
ps -p 1

# View kernel boot parameters
cat /proc/cmdline

# Run process in foreground
ping localhost > /dev/null

# Stop foreground process
Ctrl + C

# Run process in background
ping localhost > /dev/null &

# List jobs
jobs

# Bring job to foreground
fg %1

# Suspend process
Ctrl + Z

# Resume process
bg %1

# Kill a job
kill %1

# Kill all ping processes
killall ping

# Process monitor
top

# View processes
ps

# Kill process by PID
kill PID

# Kill process by name
pkill process_name

# List log files
ls /var/log

# View authentication logs
tail -5 /var/log/auth.log
```

---

# Key Concepts Learned

* `/proc` is a virtual filesystem maintained by the Linux kernel.
* Every running process has its own directory inside `/proc`.
* Foreground processes occupy the terminal, while background processes allow multitasking.
* Job control commands (`jobs`, `fg`, `bg`) help manage running processes.
* `top` provides real-time monitoring of CPU, memory, and processes.
* `kill`, `killall`, and `pkill` are essential process management tools.
* Linux stores important system and security logs inside `/var/log`.
* Authentication logs are valuable for detecting failed login attempts and investigating security events.

---

# What I Learned

This lab helped me understand how Linux manages running processes and stores runtime information through the `/proc` filesystem. I also learned how to start, pause, resume, monitor, and terminate processes using various command-line utilities. Finally, I explored Linux system logs, which are essential for troubleshooting, auditing, and maintaining the security and stability of a Linux system.
