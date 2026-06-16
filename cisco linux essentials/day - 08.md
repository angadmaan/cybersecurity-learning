# Day 8

## Overview

This lab focused on using Linux help systems and file-searching utilities. The objective was to learn how to find command documentation, navigate manual pages, and locate files and commands within the system.

---

## Topics Covered

### Viewing Command Documentation

Access command manuals using:

```bash
man date
```

Useful navigation inside man pages:

```text
q      Quit
h      Help
Space  Next page
b      Previous page
/file  Search forward
n      Next match
N      Previous match
```

---

### Searching Documentation

Find commands related to a keyword:

```bash
man -k password
apropos password
```

View available manual sections:

```bash
man -f passwd
whatis passwd
```

Open a specific section:

```bash
man 5 passwd
```

---

### Using Info Pages

View detailed documentation:

```bash
info date
```

Useful keys:

```text
q  Quit
h  Help
l  Back
Enter  Open link
```

---

### Quick Command Help

Display command usage:

```bash
date --help
```

Common for most Linux commands:

```bash
ls --help
cp --help
cat --help
```

---

### System Documentation

Additional documentation can be found in:

```bash
ls /usr/share/doc
```

Common files include:

```text
README
INSTALL
CHANGELOG
```

---

### Finding Files

Search files using locate:

```bash
locate crontab
```

Search exact filename:

```bash
locate -b "\crontab"
```

Update locate database (root):

```bash
updatedb
```

---

### Finding Commands

Locate commands and related man pages:

```bash
whereis passwd
```

Example output:

```text
/usr/bin/passwd
/etc/passwd
/usr/share/man/man1/passwd.1.gz
```

---

## Commands Practiced

```bash
man
man -k
man -f
whatis
apropos
info
locate
updatedb
whereis
date --help
```

---

## Key Takeaways

* Learned how to use Linux help systems.
* Navigated man pages and info documentation.
* Searched documentation using apropos and whatis.
* Used locate to find files.
* Used whereis to locate commands and man pages.
* Explored additional documentation stored in `/usr/share/doc`.

---

## Conclusion

This lab strengthened the ability to find information directly from the Linux system using built-in documentation and search tools, an essential skill for troubleshooting and learning new commands.
