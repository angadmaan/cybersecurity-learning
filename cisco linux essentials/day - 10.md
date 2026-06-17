# Day 10

## Overview

On Day 10 of the Cisco Linux Essentials course, I learned how Linux organizes files and directories and how to navigate the filesystem using command-line tools. The session focused on working with absolute and relative paths, understanding the Linux directory structure, and using various `ls` options to view files and directories efficiently.

---

## Topics Covered

### Linux Filesystem Basics

Key concepts learned:

* Everything in Linux is treated as a file.
* Directories are special files used to organize other files.
* Linux filenames are case-sensitive.
* The root directory (`/`) is the top level of the filesystem.
* Each user has a personal home directory.

---

## Working with Directories

### Display Current Directory

```bash
pwd
```

### View Home Directory Path

```bash
echo $HOME
```

### Change Directories

```bash
cd /
cd
cd /home
cd ~
```

### Navigate Using Relative Paths

```bash
cd bash
cd ..
cd ../dict
```

### Important Path Symbols

| Symbol | Meaning                       |
| ------ | ----------------------------- |
| `/`    | Root directory                |
| `~`    | Current user's home directory |
| `.`    | Current directory             |
| `..`   | Parent directory              |

---

## Absolute vs Relative Paths

### Absolute Path

Starts from the root directory.

Example:

```bash
cd /usr/share/doc
```

### Relative Path

Starts from the current directory.

Example:

```bash
cd bash
cd ../dict
```

---

## Listing Files and Directories

### List Directory Contents

```bash
ls
```

### Show Hidden Files

```bash
ls -a
```

Hidden files begin with a dot (`.`), such as:

```text
.bashrc
.profile
.cache
```

### Detailed File Information

```bash
ls -l /etc/hosts
```

Information displayed includes:

* File type
* Permissions
* Owner
* Group
* Size
* Modification date

---

## Recursive Directory Listing

Display files inside subdirectories as well:

```bash
ls -R /etc/udev
```

---

## File Globbing (Wildcards)

### Match Multiple Characters

```bash
ls -d /etc/s*
```

Displays files beginning with `s`.

### Match Exactly One Character

```bash
ls -d /etc/????
```

Displays names containing exactly four characters.

### Match Character Ranges

```bash
ls -d /etc/[abcd]*
```

Displays files beginning with `a`, `b`, `c`, or `d`.

---

## Key Commands Practiced

```bash
pwd
echo $HOME

cd /
cd ~
cd ..
cd bash
cd ../dict

ls
ls -a
ls -l
ls -R

ls -d /etc/s*
ls -d /etc/????
ls -d /etc/[abcd]*
```

---

## Key Takeaways

* Learned Linux filesystem hierarchy and directory structure.
* Practiced navigating using absolute and relative paths.
* Understood the purpose of home directories.
* Learned how hidden files work.
* Explored multiple `ls` options for viewing files.
* Used wildcard patterns to search and filter directory contents.
* Improved confidence in Linux command-line navigation.

---

## Conclusion

Day 10 focused on mastering filesystem navigation in Linux. Through hands-on practice with directory navigation, path management, file listing, and wildcard usage, I gained a stronger understanding of how Linux organizes and manages files, an essential skill for system administration, networking, and cybersecurity.
