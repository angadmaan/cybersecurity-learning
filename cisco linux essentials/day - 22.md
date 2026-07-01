# Day 22

## 📌 Overview

Today, I explored **special Linux permissions** and learned how **hard links** and **symbolic (soft) links** work. These concepts are fundamental for Linux system administration and cybersecurity because they control how users access files and how files can be referenced across the filesystem.

---

# 🔐 Special Permissions in Linux

Besides the standard **Read (r), Write (w), and Execute (x)** permissions, Linux supports three special permissions:

- Sticky Bit
- SetUID (Set User ID)
- SetGID (Set Group ID)

These permissions provide additional control over file and directory access.

---

# 📂 Sticky Bit

View the permissions of the temporary directories:

```bash
ls -ld /tmp
ls -ld /var/tmp
```

Example Output:

```text
drwxrwxrwt
```

Notice the **t** at the end of the permission string.

### What is Sticky Bit?

The Sticky Bit is mainly used on shared directories such as `/tmp`.

Without it:
- Any user with write permission could delete another user's files.

With Sticky Bit enabled:
- Every user can create files.
- Only the file owner (or root) can delete their own files.

This prevents users from accidentally or maliciously deleting each other's files.

---

# 🔒 Protecting Password Information

View permissions of the shadow file:

```bash
ls -l /etc/shadow
```

Output:

```text
-rw-r----- root shadow
```

The `/etc/shadow` file stores:

- Encrypted user passwords
- Password aging information
- Password expiration policies

Access is restricted to:

- Root user
- Members of the `shadow` group

---

# 👤 SetUID (Set User ID)

View the permissions of the passwd command:

```bash
ls -l /usr/bin/passwd
```

Output:

```text
-rwsr-xr-x
```

Notice the **s** in the owner's execute position.

### What is SetUID?

Normally, a program runs with the permissions of the user executing it.

With **SetUID**, the program runs using the permissions of its owner.

Since `/usr/bin/passwd` is owned by **root**, every user can securely update their password even though they cannot directly edit `/etc/shadow`.

---

# 👥 SetGID (Set Group ID)

View the permissions of the wall command:

```bash
ls -l /usr/bin/wall
```

Output:

```text
-rwxr-sr-x
```

Notice the **s** in the group's execute position.

### What is SetGID?

SetGID allows a program to execute using the permissions of the group that owns it instead of the user's group.

This enables commands like `wall` to write messages to all logged-in terminals.

---

# 📁 SetGID on Directories

SetGID can also be applied to directories.

When enabled:

- Every new file created inside the directory automatically inherits the directory's group ownership.
- Useful for collaborative projects where multiple users share files.

---

# 🔗 Hard Links

Moved to the home directory:

```bash
cd
```

Created a source file:

```bash
echo "data" > source
```

View inode information:

```bash
ls -li source
```

---

## Creating a Hard Link

```bash
ln source hardlink
```

Verify:

```bash
ls -li source hardlink
```

Both files shared:

- Same inode number
- Same file contents

The link count increased from **1 → 2**.

---

## Creating Multiple Hard Links

```bash
ln source hardlinktwo
```

Verify:

```bash
ls -li source hardlink hardlinktwo
```

All files:

- Shared one inode
- Link count increased to **3**

---

## Removing Hard Links

Delete one hard link:

```bash
rm hardlinktwo
```

Verify:

```bash
ls -li source hardlink
```

The inode remained the same while the link count decreased.

Deleting all hard links except the original still keeps the original file intact.

---

# 🔗 Symbolic (Soft) Links

Unlike hard links, symbolic links point to the **filename**, not the inode.

Create a symbolic link:

```bash
ln -s source softlink
```

Verify:

```bash
ls -li source softlink
```

Output shows:

- Different inode numbers
- File type begins with **l**

Example:

```text
softlink -> source
```

---

# 📂 Symbolic Links to Directories

Create a symbolic link pointing to `/proc`:

```bash
ln -s /proc crossdir
```

Verify:

```bash
ls -l crossdir
```

Output:

```text
crossdir -> /proc
```

Unlike hard links, symbolic links:

- Can link directories
- Can cross different filesystems and partitions

---

# 🔄 Hard Link vs Symbolic Link

| Feature | Hard Link | Symbolic (Soft) Link |
|----------|-----------|----------------------|
| Shares inode | ✅ Yes | ❌ No |
| Different inode | ❌ No | ✅ Yes |
| Can link directories | ❌ No | ✅ Yes |
| Can cross filesystems | ❌ No | ✅ Yes |
| Original file deleted | ✅ Link still works | ❌ Link becomes broken |

---

# 💻 Commands Learned Today

```bash
ls -ld /tmp
ls -ld /var/tmp

ls -l /etc/shadow
ls -l /usr/bin/passwd
ls -l /usr/bin/wall

cd

echo "data" > source

ls -li source

ln source hardlink
ln source hardlinktwo

rm hardlink
rm hardlinktwo

ln -s source softlink

ln -s /proc crossdir

ls -li source hardlink
ls -li source softlink
ls -l crossdir
```

---
