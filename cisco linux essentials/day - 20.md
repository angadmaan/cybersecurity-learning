# Day 20

## 📌 Overview

Today I learned how Linux manages **users and groups**. I explored creating, modifying, and deleting groups, creating user accounts, assigning group memberships, setting passwords, and managing user access. These are fundamental Linux administration skills used in system administration and cybersecurity.

---

# 👥 Creating Groups

Groups make it easier to assign permissions to multiple users.

## Create System Groups

```bash
groupadd -r research
groupadd -r sales
```

The `-r` option creates **system groups**, assigning them GIDs from the reserved system range (typically below 1000).

---

## View Group Information

Using `getent`:

```bash
getent group research
```

Using `grep`:

```bash
grep sales /etc/group
```

Example Output:

```text
research:x:999:
sales:x:998:
```

---

# ✏️ Modifying Groups

## Rename a Group

```bash
groupmod -n clerks sales
```

---

## Change Group ID (GID)

```bash
groupmod -g 10003 clerks
```

Verify changes:

```bash
grep clerks /etc/group
```

Example:

```text
clerks:x:10003:
```

> **Note:** Changing a group's name or GID may leave previously owned files with orphaned group ownership.

---

# ❌ Deleting Groups

Delete a group:

```bash
groupdel clerks
```

Verify removal:

```bash
grep clerks /etc/group
```

---

# 👤 User Configuration

View default settings used when creating new users:

```bash
useradd -D
```

Example Output:

```text
GROUP=100
HOME=/home
INACTIVE=-1
SHELL=/bin/bash
SKEL=/etc/skel
CREATE_MAIL_SPOOL=no
```

---

## Change Default User Settings

Allow users with expired passwords to log in for **30 additional days**:

```bash
useradd -D -f 30
```

Verify:

```bash
useradd -D
```

---

## Modify Default Configuration File

Edit:

```bash
nano /etc/default/useradd
```

Change:

```text
CREATE_MAIL_SPOOL=no
```

to

```text
CREATE_MAIL_SPOOL=yes
```

Verify:

```bash
useradd -D
```

---

# ➕ Creating Users

Create a new user named **student**.

```bash
useradd -G research -c "Linux Student" -m student
```

### Options Used

| Option | Purpose |
|---------|----------|
| `-G` | Add to secondary group |
| `-c` | User description/comment |
| `-m` | Create home directory |

---

## Verify User Creation

```bash
grep student /etc/passwd
```

```bash
grep student /etc/group
```

Example Output:

```text
student:x:1002:1002:Linux Student:/home/student:/bin/sh
```

---

# 👥 Managing Group Membership

Add an existing user to a secondary group:

```bash
usermod -aG research sysadmin
```

Verify:

```bash
getent group research
```

Example:

```text
research:x:999:student,sysadmin
```

---

# 🔍 Viewing User Information

View user details:

```bash
getent passwd student
```

View password database:

```bash
getent shadow student
```

Example:

```text
student:!:16902:0:99999:7:30::
```

The `!` indicates the account exists but **no password has been set yet**.

---

# 🔑 Setting User Password

Assign a password:

```bash
passwd student
```

After setting the password, verify:

```bash
getent shadow student
```

The second field now contains an encrypted password hash instead of `!`.

---

# 📜 Viewing Login History

Display login history for all users:

```bash
last
```

Display login history for a specific user:

```bash
last student
```

Since the user had never logged in, no login records were displayed.

---

# 🔒 Locking and Unlocking Accounts

Lock a user account:

```bash
usermod -L student
```

Unlock a user account:

```bash
usermod -U student
```

Useful when temporarily disabling user access without deleting the account.

---

# 🗑️ Deleting Users

Delete a user account only:

```bash
userdel student
```

Delete the account along with its home directory and mail spool:

```bash
userdel -r student
```

Verify removal:

```bash
grep student /etc/group
```

---

# 💻 Commands Learned Today

```bash
su -

groupadd -r research
groupadd -r sales

getent group research
grep sales /etc/group

groupmod -n clerks sales
groupmod -g 10003 clerks

groupdel clerks

useradd -D
useradd -D -f 30

nano /etc/default/useradd

useradd -G research -c "Linux Student" -m student

grep student /etc/passwd
grep student /etc/group

usermod -aG research sysadmin

getent passwd student
getent shadow student

passwd student

last
last student

usermod -L student
usermod -U student

userdel student
userdel -r student
```

---
