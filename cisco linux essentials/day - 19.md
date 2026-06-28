# Day 19

## 📌 Overview
Today I learned how Linux manages **user accounts, administrative privileges, passwords, user groups, and login history**. I explored the difference between normal users and the root user, understood how to execute administrative commands securely, and examined the files that store user account information and authentication details.

---

# 🔑 Running Commands as an Administrator

Linux provides two primary methods to perform administrative tasks.

## 1. `su` (Switch User)

The `su` command switches to another user account (typically **root**) and starts a new shell session.

### Switch to Root User

```bash
su -
```

### Verify Current User

```bash
id
```

Example Output:

```text
uid=0(root) gid=0(root) groups=0(root)
```

### Return to Previous User

```bash
exit
```

### Key Points

- Opens a new shell as another user.
- Commonly used when executing multiple administrative commands.
- Requires the root password.

---

## 2. `sudo`

The `sudo` command executes a **single command** with administrative privileges.

Example:

```bash
sudo head /etc/shadow
```

### Advantages of `sudo`

- Safer than logging in as root.
- Executes only one command with elevated privileges.
- Uses the current user's password.
- Administrative access automatically expires after a timeout.

---

# 👤 User Account Information

Linux stores user account information inside:

```text
/etc/passwd
```

### View First 10 User Accounts

```bash
head /etc/passwd
```

### View a Specific User

```bash
grep sysadmin /etc/passwd
```

or

```bash
getent passwd sysadmin
```

---

# 📄 Structure of `/etc/passwd`

Each user account is stored as a colon-separated entry.

```text
username:password_placeholder:UID:GID:Comment:Home_Directory:Shell
```

Example:

```text
sysadmin:x:1001:1001:System Administrator:/home/sysadmin:/bin/bash
```

| Field | Description |
|--------|-------------|
| Username | Login name |
| Password Placeholder | Usually `x` (actual password stored in `/etc/shadow`) |
| UID | Unique User ID |
| GID | Primary Group ID |
| Comment | User description |
| Home Directory | User's default directory |
| Shell | Default login shell |

---

# 🔒 Password Storage

Linux stores encrypted passwords inside:

```text
/etc/shadow
```

Regular users cannot read this file.

Attempting to access it:

```bash
head /etc/shadow
```

Output:

```text
Permission denied
```

Access using administrator privileges:

```bash
sudo head -3 /etc/shadow
```

---

## Check Shadow File Permissions

```bash
ls -l /etc/shadow
```

Example Output:

```text
-rw-r----- 1 root shadow
```

Meaning:

- Owner: **root**
- Group: **shadow**
- Only authorized users can read the file.

---

# 🆔 User Identity

Display information about the current user.

```bash
id
```

Example Output:

```text
uid=1001(sysadmin)
gid=1001(sysadmin)
groups=1001(sysadmin),4(adm),27(sudo)
```

Display information for another user:

```bash
id root
```

---

# 👥 User Groups

Linux uses groups to simplify permission management.

Group information is stored inside:

```text
/etc/group
```

Each entry follows this format:

```text
group_name:password:GID:user_list
```

Groups allow multiple users to share common permissions.

---

# 👀 Viewing Logged-in Users

## `who`

Displays users currently logged into the system.

```bash
who
```

Example:

```text
sysadmin pts/0
```

Shows:

- Username
- Terminal
- Login time
- Remote host (if applicable)

---

## `w`

Provides more detailed information about active users.

```bash
w
```

Displays:

- Logged-in users
- System uptime
- Load average
- Login time
- Idle time
- CPU usage
- Current running command

---

# 📜 Viewing Login History

Linux stores login history inside:

```text
/var/log/wtmp
```

Display login history:

```bash
last
```

Example:

```text
sysadmin pts/0 still logged in
```

Useful for:

- Auditing user activity
- Security investigations
- Troubleshooting login issues

---

# 💻 Commands Learned Today

```bash
su -
id
exit
sudo head /etc/shadow
head /etc/passwd
grep sysadmin /etc/passwd
getent passwd sysadmin
head /etc/shadow
ls -l /etc/shadow
id root
who
w
last
man 5 passwd
```

---
