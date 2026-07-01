# Day 21

## 📌 Overview

Today, I learned one of the most important Linux administration concepts: **file ownership and permissions**. I explored how Linux controls access to files and directories, modified permissions using both **symbolic** and **octal** notation, and changed ownership using the **chown** and **chgrp** commands.

Understanding permissions is essential for system administration and cybersecurity because it helps protect sensitive files from unauthorized access.

---

# 🔐 Understanding File Permissions

Created two directories and two files:

```bash
cd /tmp

mkdir priv-dir pub-dir

touch priv-dir/priv-file
touch pub-dir/pub-file
```

Verified ownership:

```bash
ls -l priv-dir
ls -l pub-dir
```

Example Output:

```text
-rw-rw-r-- 1 sysadmin sysadmin priv-file
-rw-rw-r-- 1 sysadmin sysadmin pub-file
```

---

# 📂 Linux File Types

The first character of `ls -l` output indicates the file type.

| Symbol | Meaning |
|---------|---------|
| `-` | Regular File |
| `d` | Directory |
| `l` | Symbolic Link |
| `b` | Block Device |
| `c` | Character Device |
| `p` | Pipe |
| `s` | Socket |

---

# 👤 Permission Structure

Linux permissions are divided into three categories:

```text
-rwxrwxr-x
```

| Section | Represents |
|----------|------------|
| User (Owner) | First 3 permissions |
| Group | Middle 3 permissions |
| Others | Last 3 permissions |

Permission values:

| Permission | Symbol |
|------------|--------|
| Read | r |
| Write | w |
| Execute | x |
| No Permission | - |

---

# 👀 Viewing Hidden Files

Display all files including hidden ones:

```bash
ls -la
```

Hidden files begin with a `.` (dot).

---

# 🔒 Making a Directory Private

View permissions:

```bash
ls -ld priv-dir
```

Remove access for others:

```bash
chmod o-rx priv-dir
```

Verify:

```bash
ls -ld priv-dir
```

Permissions changed from:

```text
drwxrwxr-x
```

to

```text
drwxrwx---
```

Now only the owner and group can access the directory.

---

# 🌍 Making a Directory Public

View permissions:

```bash
ls -ld pub-dir
```

Grant write permission to others:

```bash
chmod o+w pub-dir
```

Verify:

```bash
ls -ld pub-dir
```

Permissions became:

```text
drwxrwxrwx
```

---

# 🔐 Securing Files

View file permissions:

```bash
ls -l priv-dir/priv-file
```

Remove group and others permissions:

```bash
chmod g-rw,o-r priv-dir/priv-file
```

Verify:

```bash
ls -l priv-dir/priv-file
```

Result:

```text
-rw-------
```

Only the owner can read and write.

---

# 📄 Giving Everyone Read & Write Access

```bash
chmod a=rw pub-dir/pub-file
```

Result:

```text
-rw-rw-rw-
```

Everyone now has read and write permissions.

---

# ⚙️ Making a Script Executable

Create a script:

```bash
echo "date" > test.sh
```

Attempt to execute:

```bash
./test.sh
```

Result:

```text
Permission denied
```

Reason:

```bash
ls -l test.sh
```

The file lacked execute permission.

Grant execute permission:

```bash
chmod u+x test.sh
```

Run again:

```bash
./test.sh
```

The script successfully executed and displayed the current date.

---

# 🔢 Octal Permission Values

Each permission has a numeric value.

| Permission | Value |
|------------|-------|
| Read | 4 |
| Write | 2 |
| Execute | 1 |

Examples:

| Octal | Permission |
|--------|------------|
| 7 | rwx |
| 6 | rw- |
| 5 | r-x |
| 4 | r-- |
| 0 | --- |

---

# 📊 Viewing Detailed File Information

Use the `stat` command:

```bash
stat test.sh
```

Example:

```text
Access: (0764/-rwxrw-r--)
```

This confirms both symbolic and octal permission formats.

---

# 🔄 Changing Permissions Using Octal

Allow everyone to execute the script:

```bash
chmod 775 test.sh
```

Verify:

```bash
ls -l test.sh
```

Output:

```text
-rwxrwxr-x
```

Meaning:

- Owner → Read, Write, Execute
- Group → Read, Write, Execute
- Others → Read, Execute

---

# 👑 File Ownership

Switch to root:

```bash
su -
```

---

# 🔄 Changing Owner and Group

View current ownership:

```bash
ls -ld pub-dir
```

Change owner and group:

```bash
chown root:root pub-dir
```

Verify:

```bash
ls -ld pub-dir
```

Ownership changed from:

```text
sysadmin sysadmin
```

to

```text
root root
```

---

# 👤 Changing File Owner

```bash
chown bin pub-dir/pub-file
```

Verify:

```bash
ls -l pub-dir/pub-file
```

Result:

```text
bin sysadmin
```

Only the file owner changed.

---

# 👥 Changing Group Ownership

View current ownership:

```bash
ls -ld priv-dir
ls -l priv-dir/priv-file
```

Recursively change group:

```bash
chgrp -R users priv-dir
```

Verify:

```bash
ls -ld priv-dir
ls -l priv-dir/priv-file
```

The group owner changed from:

```text
sysadmin
```

to

```text
users
```

The `-R` option applies the change recursively to all files and subdirectories.

---

# 💻 Commands Learned Today

```bash
cd /tmp

mkdir priv-dir pub-dir

touch priv-dir/priv-file
touch pub-dir/pub-file

ls -l
ls -la
ls -ld

chmod o-rx priv-dir
chmod o+w pub-dir
chmod g-rw,o-r priv-dir/priv-file
chmod a=rw pub-dir/pub-file
chmod u+x test.sh
chmod 775 test.sh

echo "date" > test.sh
./test.sh

stat test.sh

su -

chown root:root pub-dir
chown bin pub-dir/pub-file

chgrp -R users priv-dir
```

---
