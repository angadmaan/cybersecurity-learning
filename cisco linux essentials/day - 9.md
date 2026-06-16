# Day 9

## Overview

Today I learned how Linux organizes files and directories through its filesystem hierarchy. I explored navigation techniques, path types, and various ways to list and inspect files using command-line tools.

---

## Topics Covered

### Linux Filesystem Structure

Unlike Windows, Linux uses a single directory tree that starts from the root directory:

```bash
/
```

Common directories:

| Directory | Purpose |
|------------|----------|
| `/home` | User home directories |
| `/etc` | Configuration files |
| `/bin` | Essential commands |
| `/usr` | User programs and utilities |
| `/var` | Logs and variable data |
| `/tmp` | Temporary files |
| `/boot` | Boot-related files |

---

## Home Directory

Each user has a personal home directory:

```bash
/home/username
```

Examples:

```bash
/home/sysadmin
```

Shortcut:

```bash
~
```

---

## Checking Current Location

Display the current working directory:

```bash
pwd
```

Example:

```bash
pwd
```

Output:

```bash
/home/sysadmin
```

---

## Navigating Directories

Change directory:

```bash
cd directory_name
```

Examples:

```bash
cd Documents
cd Downloads
cd
```

Return to home directory:

```bash
cd
```

---

## Understanding Paths

### Absolute Path

Starts from root (`/`).

```bash
cd /home/sysadmin/Documents
```

### Relative Path

Starts from the current directory.

```bash
cd Documents
cd School/Art
```

---

## Useful Path Shortcuts

Move one directory up:

```bash
cd ..
```

Current directory:

```bash
.
```

Example:

```bash
cd ../../Downloads
```

---

## Listing Files and Directories

Basic listing:

```bash
ls
```

List another directory:

```bash
ls /var
```

---

## Display Hidden Files

Files beginning with `.` are hidden.

```bash
ls -a
```

Example hidden files:

```bash
.bashrc
.profile
.cache
```

---

## Long Listing Format

View detailed file information:

```bash
ls -l
```

Information displayed:

- File type
- Permissions
- Owner
- Group
- File size
- Modification date
- File name

---

## Human Readable Sizes

Display file sizes in KB, MB, or GB:

```bash
ls -lh
```

Example:

```bash
286K
1.7M
2.3G
```

---

## Recursive Listing

View all files and subdirectories:

```bash
ls -R
```

Example:

```bash
ls -R /etc/ppp
```

---

## Directory Information Only

Display details about the directory itself:

```bash
ls -ld
```

---

## Sorting Files

### Sort by Size

```bash
ls -lS
```

### Sort by Modification Time

```bash
ls -lt
```

### Reverse Order

```bash
ls -lr
```

### Human Readable + Sorted by Size

```bash
ls -lSh
```

---

## Key Commands Practiced

```bash
pwd
cd
cd ..
ls
ls -a
ls -l
ls -lh
ls -ld
ls -R
ls -lS
ls -lt
ls -lr
```

---

## Key Takeaways

- Learned the Linux filesystem hierarchy.
- Understood the difference between absolute and relative paths.
- Practiced navigating directories using `cd`.
- Used `pwd` to identify the current working directory.
- Learned how to view hidden files.
- Explored advanced `ls` options for detailed file information.
- Learned to sort files by size and modification time.
- Improved confidence in filesystem navigation through the Linux CLI.

---

## Conclusion

Day 9 focused on understanding how Linux organizes files and directories. By learning filesystem navigation, path structures, and file listing techniques, I strengthened my ability to work efficiently within the Linux command-line environment.
