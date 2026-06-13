# Day 7

## Overview

Today's session focused on Linux documentation systems and command-line help tools. Learning how to find information quickly is an essential Linux skill for troubleshooting and mastering new commands.

---

## Topics Covered

### Man Pages

Manual pages provide detailed documentation for Linux commands.

```bash
man ls
man cp
man mkdir
```

Useful actions:

```text
q        Exit
/word    Search
n        Next result
Shift+n  Previous result
```

---

### Whatis & Apropos

Find command descriptions and related documentation.

```bash
whatis ls
man -f ls

apropos copy
man -k copy
```

---

### Which & Whereis

Locate command binaries and documentation.

```bash
which ls
whereis ls
```

Example:

```text
/bin/ls
```

---

### Locate Command

Search files and directories using the system database.

```bash
locate passwd
locate -c passwd
locate -b "\passwd"
```

Update database (root):

```bash
updatedb
```

---

### Info Documentation

Provides structured and detailed documentation.

```bash
info ls
```

Useful navigation:

```text
q  Quit
h  Help
n  Next
p  Previous
u  Up
```

---

### Quick Help

Most commands support the `--help` option.

```bash
ls --help
cp --help
cat --help
```

Useful for quickly checking syntax and options.

---

### Documentation Directories

Linux stores additional documentation in:

```text
/usr/share/doc
/usr/doc
```

Common files:

```text
README
INSTALL
CHANGELOG
```

---

## Commands Practiced

```bash
man
man -f
man -k
whatis
apropos
which
whereis
locate
info
updatedb
--help
```

---

## Key Takeaways

- Learned how to access Linux documentation.
- Used man pages and info pages for command references.
- Located commands using `which` and `whereis`.
- Searched files using `locate`.
- Used `--help` for quick command guidance.
- Explored Linux documentation directories.

---

## Conclusion

Linux provides powerful built-in documentation tools. Understanding how to use man pages, info pages, and search utilities makes learning Linux faster and improves troubleshooting skills.
