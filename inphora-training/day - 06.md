# Day 6

## Overview

On Day 6 of the cybersecurity training, I was introduced to basic Linux commands used for navigating the file system and managing files and directories. These commands form the foundation of working efficiently in a Linux environment and are frequently used by system administrators, developers, and cybersecurity professionals.

---

## Commands Learned

### 1. `pwd` - Print Working Directory

Displays the current directory location.

```bash
pwd
```

Example Output:

```bash
/home/kali/Documents
```

---

### 2. `ls` - List Files and Directories

Shows the contents of the current directory.

```bash
ls
```

---

### 3. `ls -la` - Detailed Directory Listing

Displays all files, including hidden files, along with permissions, ownership, and file sizes.

```bash
ls -la
```

---

### 4. `cd` - Change Directory

Used to move into another directory.

```bash
cd Documents
```

---

### 5. `cd ..` - Move Back One Directory

Navigates to the parent directory.

```bash
cd ..
```

---

### 6. `mkdir` - Create Directory

Creates a new folder.

```bash
mkdir notes
```

---

### 7. `touch` - Create File

Creates an empty file.

```bash
touch file.txt
```

---

### 8. `cp` - Copy File

Copies a file from one location to another.

```bash
cp file.txt backup.txt
```

---

### 9. `cp -r` - Copy Directory

Copies an entire directory and its contents.

```bash
cp -r notes backup_notes
```

---

### 10. `rm` - Remove File

Deletes a file permanently.

```bash
rm file.txt
```

---

### 11. `rmdir` - Remove Empty Directory

Deletes an empty directory.

```bash
rmdir notes
```

---

### 12. `cat` - Display File Content

Displays the contents of a text file.

```bash
cat file.txt
```

---

## Practical Exercise

```bash
mkdir practice

cd practice

touch notes.txt

cat notes.txt

cp notes.txt backup.txt

ls -la

cd ..

rmdir practice
```

---

## Key Takeaways

- Learned how to navigate the Linux file system.
- Created and managed files using terminal commands.
- Copied files and directories.
- Viewed file contents directly from the command line.
- Practiced basic file and folder management operations.
- Developed foundational Linux skills essential for cybersecurity and system administration.

---

## Conclusion

This session provided hands-on experience with fundamental Linux commands that are used daily in system administration and cybersecurity tasks. Understanding these commands is an important first step toward becoming comfortable with the Linux command-line environment.
